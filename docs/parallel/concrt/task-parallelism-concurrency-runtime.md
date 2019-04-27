---
title: Paralelismo de tareas (Runtime de simultaneidad)
ms.date: 11/04/2016
helpviewer_keywords:
- structured task groups [Concurrency Runtime]
- structured tasks [Concurrency Runtime]
- task groups [Concurrency Runtime]
- task parallelism
- tasks [Concurrency Runtime]
ms.assetid: 42f05ac3-2098-494a-ba84-737fcdcad077
ms.openlocfilehash: c9f18dfd1498538ce3700fd73a27ce6f6088ee42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180048"
---
# <a name="task-parallelism-concurrency-runtime"></a>Paralelismo de tareas (Runtime de simultaneidad)

En el Runtime de simultaneidad, un *tarea* es una unidad de trabajo que realiza un trabajo específico y normalmente se ejecuta en paralelo con otras tareas. Una tarea se puede descomponer en tareas adicionales más específicas que se organizan en una *grupo de tareas*.

Las tareas se usan al escribir código asincrónico y cuando se quiere que alguna operación se produzca después de que finalice la operación asincrónica. Por ejemplo, podría utilizar una tarea para leer de forma asincrónica desde un archivo y, a continuación, utilizar otra tarea — una *tarea de continuación*, que se explica más adelante en este documento — para procesar los datos cuando estén disponible. A la inversa, se pueden usar grupos de tareas para descomponer el trabajo paralelo en partes más pequeñas. Supongamos, por ejemplo, que tiene un algoritmo recursivo que divide el trabajo restante en dos partes. Puede usar grupos de tareas para ejecutar estas partes simultáneamente y esperar a que el trabajo dividido se complete.

> [!TIP]
> Cuando desea aplicar la misma rutina en cada elemento de una colección en paralelo, use un algoritmo paralelo, como [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for), en lugar de una tarea o un grupo de tareas. Para obtener más información acerca de los algoritmos paralelos, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).

## <a name="key-points"></a>Puntos clave

- Cuando se pasan variables por referencia a una expresión lambda, es necesario garantizar que esas variables van a persistir hasta que la tarea finalice.

- Uso de tareas (la [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) clases) al escribir código asincrónico. La clase task usa como programador el grupo de subprocesos de Windows, no el Runtime de simultaneidad.

- Usar grupos de tareas (la [Concurrency:: task_group](reference/task-group-class.md) clase o el [Concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmo) cuando desee descomponer el trabajo paralelo en partes más pequeñas y, a continuación, espere a que los más pequeños piezas en completarse.

- Use la [concurrency::task::then](reference/task-class.md#then) método para crear continuaciones. Un *continuación* es una tarea que se ejecuta de forma asincrónica después de otra tarea. Puede conectar un número indeterminado de continuaciones para formar una cadena de trabajo asincrónico.

- Una continuación basada en tareas está programada siempre para ejecutarse cuando finaliza la tarea antecedente, aun cuando esta se cancele o genere una excepción.

- Use [Concurrency:: when_all](reference/concurrency-namespace-functions.md#when_all) para crear una tarea que completa una vez completada cada miembro de un conjunto de tareas. Use [Concurrency:: when_any](reference/concurrency-namespace-functions.md#when_any) para crear una tarea que finaliza después de un miembro de un conjunto de tareas.

- Las tareas y los grupos de tareas pueden participar en el mecanismo de cancelación de la Biblioteca de patrones de procesamiento paralelo (PPL). Para obtener más información, consulte [cancelación en PPL](cancellation-in-the-ppl.md).

- Para obtener información sobre cómo el runtime controla las excepciones producidas por tareas y grupos de tareas, consulte [Exception Handling](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="in-this-document"></a>En este documento

- [Usar expresiones Lambda](#lambdas)

- [La clase de tarea](#task-class)

- [Tareas de continuación](#continuations)

- [Basada en valores frente a continuaciones basadas en tareas](#value-versus-task)

- [Componer tareas](#composing-tasks)

    - [La función when_all](#when-all)

    - [La función when_any](#when-any)

- [Ejecución retrasada de una tarea](#delayed-tasks)

- [Grupos de tareas](#task-groups)

- [Comparación de task_group y structured_task_group](#comparing-groups)

- [Ejemplo](#example)

- [Programación sólida](#robust)

##  <a name="lambdas"></a> Usar expresiones Lambda

Dada su sintaxis concisa, las expresiones lambda son una forma habitual de definir el trabajo que las tareas y los grupos de tareas llevan a cabo. Estas son algunas sugerencias de uso:

- Como las tareas normalmente se ejecutan en subprocesos en segundo plano, tenga en cuenta la duración del objeto cuando capture variables en expresiones lambda. Cuando se captura una variable por valor, se hace una copia de esa variable en el cuerpo de la lambda. Esta copia no se realiza cuando se captura por referencia. Por lo tanto, asegúrese de que la duración de la variable que capture por referencia es mayor que la tarea que la usa.

- Al pasar una expresión lambda a una tarea, no capture variables que estén asignadas en la pila por referencia.

- Sea explícito con respecto a las variables que capture en las expresiones lambda; así, podrá identificar lo que está capturando por valor en contraposición a por referencia. Por este motivo, recomendamos no usar las opciones `[=]` o `[&]` en expresiones lambda.

Un patrón común tiene lugar cuando una tarea en una cadena de continuación se asigna a una variable y otra tarea lee esa variable. En este caso no se podría capturar por valor, porque cada tarea de continuación contendría una copia diferente de la variable. En el caso de las variables asignadas a una pila, tampoco se podrá capturar por referencia, dado que es posible que la variable ya no sea válida.

Para solucionar este problema, utilice un puntero inteligente, tales como [std:: shared_ptr](../../standard-library/shared-ptr-class.md)para ajustar la variable y pasar el puntero inteligente por valor. De este modo, el objeto subyacente se puede asignar y leer, y su duración será mayor que la de las tareas que lo usan. Use esta técnica incluso cuando la variable sea un puntero o un identificador de recuento de referencia (`^`) a un objeto de Windows en tiempo de ejecución. Este es un ejemplo básico:

[!code-cpp[concrt-lambda-task-lifetime#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_1.cpp)]

Para obtener más información sobre las expresiones lambda, vea [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md).

##  <a name="task-class"></a> La clase de tarea

Puede usar el [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) clase para crear tareas dentro de un conjunto de operaciones dependientes. Este modelo de composición es compatible con la noción de *continuaciones*. Un continuación permita el código que se ejecuta al anterior, o *antecedente*, se completa la tarea. El resultado de la tarea antecedente se pasa como entrada para una o varias tareas de continuación. Cuando una tarea antecedente se completa, las tareas de continuación en espera están programadas para ejecutarse. Cada tarea de continuación recibe una copia del resultado de la tarea anterior. Las tareas de continuación también pueden ser, a su vez, tareas antecedentes de otras continuaciones, lo que hace que se vaya creando una cadena de tareas. Las continuaciones sirven para crear cadenas de tareas de longitud arbitraria que tienen dependencias específicas entre ellas. Asimismo, una tarea puede participar en la cancelación antes de que una tarea se inicie o bien de manera cooperativa, mientras se está ejecutando. Para obtener más información sobre este modelo de cancelación, vea [cancelación en PPL](cancellation-in-the-ppl.md).

`task` es una clase de plantilla. El parámetro de tipo `T` es el tipo del resultado generado por la tarea. Este tipo puede ser `void` si la tarea no devuelve un valor. `T` no puede usar el modificador `const`.

Cuando se crea una tarea, proporciona un *función de trabajo* que realiza el cuerpo de la tarea. Esta función de trabajo tiene la forma de una función lambda, un puntero de función o un objeto de función. Para esperar a que una tarea finalice sin obtener el resultado, llame a la [concurrency::task::wait](reference/task-class.md#wait) método. El `task::wait` método devuelve un [Concurrency:: task_status](reference/concurrency-namespace-enums.md#task_group_status) valor que describe si la tarea se ha completado o cancelado. Para obtener el resultado de la tarea, llame a la [concurrency::task::get](reference/task-class.md#get) método. Este método llama a `task::wait` para esperar a que la tarea finalice y, por lo tanto, bloquea la ejecución del subproceso actual hasta que el resultado esté disponible.

En el siguiente ejemplo se muestra cómo crear una tarea, esperar su resultado y mostrar el valor correspondiente. En los ejemplos de esta documentación se usan funciones lambda porque proporcionan una sintaxis más concisa. Sin embargo, también se pueden usar objetos de función y punteros de función al trabajar con tareas.

[!code-cpp[concrt-basic-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_2.cpp)]

Cuando se usa el [Concurrency:: create_task](reference/concurrency-namespace-functions.md#create_task) función, puede usar el `auto` palabra clave en lugar de declarar el tipo. Veamos, por ejemplo, este código con el que se crea e imprime la matriz de identidad:

[!code-cpp[concrt-create-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_3.cpp)]

Puede usar la función `create_task` para crear la operación equivalente.

[!code-cpp[concrt-create-task#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_4.cpp)]

Si se produce una excepción mientras una tarea se ejecuta, el Runtime calcula las referencias a esa excepción en la siguiente llamada a `task::get` o `task::wait`, o bien a una continuación basada en tareas. Para obtener más información sobre el mecanismo de control de excepciones de tareas, consulte [Exception Handling](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Para obtener un ejemplo que usa `task`, [Concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), cancelación, vea [Tutorial: Conectar usando tareas y solicitudes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md). (La clase `task_completion_event` se describe más adelante en este documento).

> [!TIP]
>  Para obtener detalles que son específicos de las tareas en aplicaciones para UWP, consulte [programación asincrónica en C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) y [crear operaciones asincrónicas en C++ para aplicaciones UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).

##  <a name="continuations"></a> Tareas de continuación

En la programación asincrónica, es muy común que una operación asincrónica, al finalizar, invoque una segunda operación y le pase los datos. Tradicionalmente, esto se realiza mediante métodos de devolución de llamada. En el Runtime de simultaneidad, se proporciona la misma funcionalidad mediante *tareas de continuación*. Una tarea de continuación (también conocida simplemente como una continuación) es una tarea asincrónica invocada por otra tarea, que se conoce como el *antecedente*, cuando el antecedente se completa. El uso de continuaciones permite hacer lo siguiente:

- Pasar datos del antecedente a la continuación.

- Especificar las condiciones exactas en las que se invoca o no se invoca la continuación.

- Cancelar una continuación antes de que se inicie o de forma cooperativa mientras se ejecuta.

- Proporcionar sugerencias sobre cómo debería programarse la continuación. (Esto se aplica a solo las aplicaciones de la plataforma Universal de Windows (UWP). Para obtener más información, consulte [crear operaciones asincrónicas en C++ para aplicaciones UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).)

- Invocar varias continuaciones desde el mismo antecedente.

- Invocar una continuación cuando todas o una de las tareas antecedentes finalicen.

- Encadenar continuaciones una tras otra de cualquier longitud.

- Usar una continuación para controlar las excepciones producidas por el antecedente.

Estas características permiten ejecutar una o más tareas cuando la primera tarea se completa. Por ejemplo, puede crear una continuación que comprenda un archivo después de que la primera tarea lo lea desde el disco.

El ejemplo siguiente modifica el ejemplo anterior para usar el [concurrency::task::then](reference/task-class.md#then) método para programar una continuación que imprime el valor de la tarea antecedente cuando esté disponible.

[!code-cpp[concrt-basic-continuation#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_5.cpp)]

Puede encadenar y anidar tareas de cualquier longitud. Una tarea también puede tener varias continuaciones. En el siguiente ejemplo se muestra una cadena de continuación básica que triplica el valor de la tarea anterior.

[!code-cpp[concrt-continuation-chain#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_6.cpp)]

Una continuación también puede devolver otra tarea. Si no hay ninguna cancelación, esta tarea se ejecuta antes de la continuación siguiente. Esta técnica se conoce como *desencapsulación asincrónica*. La desencapsulación asincrónica resulta útil cuando se quiere realizar un trabajo adicional en segundo plano sin que la tarea actual bloquee el subproceso actual. (Esto es habitual en aplicaciones UWP, donde pueden ejecutar continuaciones en el subproceso de interfaz de usuario). En el siguiente ejemplo se muestran tres tareas. La primera tarea devuelve otra tarea que se ejecuta antes de una tarea de continuación.

[!code-cpp[concrt-async-unwrapping#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_7.cpp)]

> [!IMPORTANT]
>  Cuando una continuación de una tarea devuelve una tarea anidada de tipo `N`, la tarea resultante tiene el tipo `N` (no `task<N>`) y se completa cuando lo haga la tarea anidada. En otras palabras, la continuación realiza la desencapsulación de la tarea anidada.

##  <a name="value-versus-task"></a> Basada en valores frente a continuaciones basadas en tareas

Si tenemos un objeto `task` cuyo tipo de valor devuelto es `T`, se puede proporcionar un valor de tipo `T` o `task<T>` a las tareas de continuación. Una continuación que toma el tipo `T` se conoce como un *continuación basada en el valor*. Una continuación basada en valores está programada para ejecutarse cuando la tarea antecedente se completa sin errores y no se ha cancelado. Una continuación que toma el tipo `task<T>` como su parámetro se conoce como un *basado en tareas de continuación*. Una continuación basada en tareas está programada siempre para ejecutarse cuando finaliza la tarea antecedente, aun cuando esta se cancele o genere una excepción. Tras ello, puede llamar a `task::get` para obtener el resultado de la tarea antecedente. Si se canceló la tarea antecedente, `task::get` produce [Concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md). Si la tarea antecedente produjo una excepción, `task::get` vuelve a producir esta excepción. Una continuación basada en tareas no se marca como cancelada cuando su tarea antecedente se cancela.

##  <a name="composing-tasks"></a> Componer tareas

Esta sección se describe la [Concurrency:: when_all](reference/concurrency-namespace-functions.md#when_all) y [Concurrency:: when_any](reference/concurrency-namespace-functions.md#when_all) funciones, que pueden ayudarle a crear varias tareas para implementar patrones comunes.

###  <a name="when-all"></a> La función when_all

La función `when_all` genera una tarea que finaliza después de que se complete un conjunto de tareas. Esta función devuelve un std::[vector](../../standard-library/vector-class.md) objeto que contiene el resultado de cada tarea del conjunto. En el siguiente ejemplo básico se usa `when_all` para crear una tarea que representa la finalización de otras tres tareas.

[!code-cpp[concrt-join-tasks#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_8.cpp)]

> [!NOTE]
>  Las tareas que se pasan a `when_all` tienen que ser uniformes. En otras palabras, todas tienen que devolver el mismo tipo.

También puede usar la sintaxis `&&` para crear una tarea que finalice cuando lo haga un conjunto de tareas, como se aprecia en el siguiente ejemplo.

`auto t = t1 && t2; // same as when_all`

Es habitual usar una continuación junto con `when_all` para realizar una acción después de que un conjunto de tareas finalice. En el siguiente ejemplo se modifica el ejemplo anterior con el propósito de imprimir la suma de tres tareas que generan un resultado `int` cada una.

[!code-cpp[concrt-join-tasks#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_9.cpp)]

En este ejemplo, también puede especificar `task<vector<int>>` para generar una continuación basada en tareas.

Si una tarea de un conjunto de tareas se cancela o genera una excepción, `when_all` se completa inmediatamente y no se espera a que las tareas restantes terminen. Si se produce una excepción, el Runtime volverá a producirla cuando se llame a `task::get` o a `task::wait` en el objeto de tarea que `when_all` devuelve. Si se produce una excepción en más de una tarea, el Runtime elige una de ellas. Por lo tanto, procure observar todas las excepciones después de que todas las tareas se hayan completado; una excepción de tarea no controlada hará que la aplicación finalice.

A continuación mostramos una función de utilidad que le servirá para asegurarse de que su programa tenga presentes todas las excepciones. Por cada tarea en el intervalo proporcionado, `observe_all_exceptions` desencadena cualquier excepción que se haya vuelto a producir y, luego, la pasa.

[!code-cpp[concrt-eh-when_all#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_10.cpp)]

Considere la posibilidad de una aplicación para UWP que usa C++ y XAML y escribe un conjunto de archivos en disco. En el siguiente ejemplo se muestra cómo usar `when_all` y `observe_all_exceptions` para asegurarse de que el programa tiene presentes todas las excepciones.

[!code-cpp[concrt-eh-when_all#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_11.cpp)]

##### <a name="to-run-this-example"></a>Para ejecutar este ejemplo

1. En MainPage.xaml, agregue un control `Button`.

[!code-xml[concrt-eh-when_all#3](../../parallel/concrt/codesnippet/xaml/task-parallelism-concurrency-runtime_12.xaml)]

1. En MainPage.xaml.h, agregue estas declaraciones adelantadas a la sección `private` de la declaración de clase `MainPage`.

[!code-cpp[concrt-eh-when_all#4](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_13.h)]

1. En MainPage.xaml.cpp, implemente el controlador de eventos `Button_Click`.

[!code-cpp[concrt-eh-when_all#5](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_14.cpp)]

1. En MainPage.xaml.cpp, implemente `WriteFilesAsync` tal y como se muestra en el ejemplo.

> [!TIP]
> `when_all` es una función sin bloqueo que genera `task` como resultado. A diferencia de [Task:: wait](reference/task-class.md#wait), resulta seguro llamar a esta función en una aplicación para UWP en el subproceso ASTA (Application STA).

###  <a name="when-any"></a> La función when_any

La función `when_any` genera una tarea que finaliza después de que lo haga la primera tarea de un conjunto de tareas. Esta función devuelve un [std:: Pair](../../standard-library/pair-structure.md) objeto que contiene el resultado de la tarea completada y el índice de la tarea en el conjunto.

La función `when_any` es especialmente útil en los siguientes escenarios:

- Operaciones redundantes. Considere un algoritmo o una operación que pueda realizarse de muchas maneras. Puede usar la función `when_any` para seleccionar la operación que finaliza primero y, luego, cancelar las operaciones restantes.

- Operaciones intercaladas. Puede iniciar varias operaciones que tienen que finalizar en su totalidad y usar la función `when_any` para procesar los resultados cuando cada operación finalice. Finalizada una operación, puede iniciar una o más tareas adicionales.

- Operaciones limitadas. Puede usar la función `when_any` para ampliar el escenario anterior limitando el número de operaciones simultáneas.

- Operaciones que han expirado. Puede usar la función `when_any` para seleccionar entre una o más tareas y una tarea que finaliza después de una hora específica.

Al igual que `when_all`, es habitual usar una continuación que tiene `when_any` para realizar una acción al finalizar la primera tarea de un conjunto de tareas. En el siguiente ejemplo básico se usa `when_any` para crear una tarea que se completa cuando lo hace la primera de otras tres tareas.

[!code-cpp[concrt-select-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_15.cpp)]

En este ejemplo, también puede especificar `task<pair<int, size_t>>` para generar una continuación basada en tareas.

> [!NOTE]
> Al igual que `when_all`, todas las tareas que se pasan a `when_any` tienen que devolver el mismo tipo.

También puede usar la sintaxis `||` para crear una tarea que finalice cuando lo haga la primera tarea de un conjunto de tareas, como se aprecia en el siguiente ejemplo.

`auto t = t1 || t2; // same as when_any`

> [!TIP]
> Igual que con `when_all`, `when_any` no es de bloqueo y es seguro llamar a en una aplicación para UWP en el subproceso ASTA.

##  <a name="delayed-tasks"></a> Ejecución retrasada de una tarea

Hay veces que es necesario retrasar la ejecución de una tarea hasta que se satisfaga una condición, o iniciar una tarea en respuesta a un evento externo. Por ejemplo, en una programación asincrónica, puede que tenga que iniciar una tarea en respuesta a un evento de finalización de E/S.

Dos formas de lograrlo son usar una continuación o bien iniciar una tarea y esperar un evento dentro de la función de trabajo de la tarea. Sin embargo, hay casos en los que no es posible recurrir a una de estas técnicas. Por ejemplo, para crear una continuación, hay que tener la tarea antecedente. Sin embargo, si no tiene la tarea antecedente, puede crear un *evento de finalización de tarea* y más adelante, encadenar ese evento de finalización a la tarea antecedente cuando esté disponible. Además, como una tarea en espera también bloquea un subproceso, puede usar eventos de finalización de tarea para realizar el trabajo cuando una operación asincrónica se complete y, de este modo, liberar un subproceso.

El [Concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) clase ayuda a simplificar las tareas. Al igual que la clase `task`, el parámetro de tipo `T` es el tipo del resultado que la tarea genera. Este tipo puede ser `void` si la tarea no devuelve un valor. `T` no puede usar el modificador `const`. Normalmente, se proporciona un objeto `task_completion_event` a un subproceso o una tarea que indicará el momento en el que el valor esté disponible. Al mismo tiempo, se establecen una o varias tareas como agentes de escucha de ese evento. Cuando se establece el evento, las tareas de agente de escucha finalizan y sus continuaciones se programan para ejecutarse.

Para obtener un ejemplo que usa `task_completion_event` para implementar una tarea que finaliza después de un retraso, vea [Cómo: Crear una tarea que finaliza después de un retraso](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md).

##  <a name="task-groups"></a> Grupos de tareas

Un *grupo de tareas* organiza una colección de tareas. Los grupos de tareas envían tareas a una cola de robo de trabajo. El programador quita las tareas de esta cola y las ejecuta en los recursos informáticos disponibles. Después de agregar tareas a un grupo de tareas, puede esperar a que todas las tareas finalicen o cancelar las tareas que aún no se han iniciado.

La biblioteca PPL usa la [Concurrency:: task_group](reference/task-group-class.md) y [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) clases para representar grupos de tareas y el [Concurrency:: task_handle](../../parallel/concrt/reference/task-handle-class.md) clase para representar las tareas que se ejecutan en estos grupos. La clase `task_handle` encapsula el código que realiza el trabajo. Al igual que la clase `task`, la función de trabajo tiene la forma de una función lambda, un puntero de función o un objeto de función. Normalmente no es necesario trabajar con objetos `task_handle` directamente. En su lugar, se pasan funciones de trabajo a un grupo de tareas y el grupo de tareas crea y administra los objetos `task_handle`.

La biblioteca PPL divide los grupos de tareas en estas dos categorías: *grupos de tareas estructurados* y *estructurada de los grupos de tareas*. La biblioteca PPL usa la clase `task_group` para representar grupos de tareas sin estructura y la clase `structured_task_group` para representar grupos de tareas con estructura.

> [!IMPORTANT]
> La biblioteca PPL también define la [Concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmo, que usa el `structured_task_group` clase para ejecutar un conjunto de tareas en paralelo. Como el algoritmo `parallel_invoke` tiene una sintaxis más concisa, recomendamos usarlo en lugar de la clase `structured_task_group` siempre que sea posible. El tema [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md) describe `parallel_invoke` con mayor detalle.

Use `parallel_invoke` cuando tenga varias tareas independientes que quiere ejecutar al mismo tiempo y tenga que esperar a que todas las tareas finalicen antes de continuar. Esta técnica se conoce a menudo como *bifurcación y combinación* paralelismo. Use `task_group` cuando tenga varias tareas independientes que quiere ejecutar al mismo tiempo, pero quiera esperar a que las tareas finalicen más adelante. Por ejemplo, puede agregar tareas a un objeto `task_group` y esperar a que las tareas finalicen en otra función o desde otro subproceso.

Los grupos de tareas admiten el concepto de cancelación. Con la cancelación puede indicar a todas las tareas activas que quiere cancelar la operación global. De igual modo, las cancelaciones evitan que se inicien las tareas que aún no han empezado. Para obtener más información sobre la cancelación, vea [cancelación en PPL](cancellation-in-the-ppl.md).

El Runtime también proporciona un modelo de control de excepciones que permite generar una excepción desde una tarea y controlar esa excepción mientras espera a que el grupo de tareas asociado finalice. Para obtener más información sobre este modelo de control de excepciones, vea [Exception Handling](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

##  <a name="comparing-groups"></a> Comparación de task_group y structured_task_group

Aunque recomendamos usar `task_group` o `parallel_invoke` en lugar de la clase `structured_task_group`, hay casos donde probablemente prefiera usar `structured_task_group`, por ejemplo, al escribir un algoritmo paralelo que realiza un número variable de tareas o que requiere compatibilidad con la cancelación. En esta sección se explican las diferencias entre las clases `task_group` y `structured_task_group`.

La clase `task_group` es segura para la ejecución de subprocesos. Por lo tanto, puede agregar tareas a un objeto `task_group` desde varios subprocesos y esperar o cancelar un objeto `task_group` desde varios subprocesos. Es necesario que la construcción y destrucción de un objeto `structured_task_group` ocurran en el mismo ámbito léxico. Además, todas las operaciones en un objeto `structured_task_group` tienen que producirse en el mismo subproceso. La excepción a esta regla es la [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) y [concurrency::structured_task_group::is_canceling](reference/structured-task-group-class.md#is_canceling) métodos. Una tarea secundaria puede llamar a estos métodos para cancelar el grupo de tareas primario y buscar la cancelación en cualquier momento.

Puede ejecutar tareas adicionales en un `task_group` objeto después de llamar a la [task_group](reference/task-group-class.md#wait) o [run_and_wait](reference/task-group-class.md#run_and_wait) método. Por el contrario, si ejecuta tareas adicionales en un `structured_task_group` objeto después de llamar a la [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait) o [concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait) métodos , a continuación, el comportamiento es indefinido.

La clase `structured_task_group` no se sincroniza entre subprocesos, de modo que tiene menos sobrecarga de ejecución que la clase `task_group`. Por lo tanto, si su problema no requiere programar el trabajo desde varios subprocesos y no puede usar el algoritmo `parallel_invoke`, la clase `structured_task_group` le ayudará a escribir código con mejor rendimiento.

Si usa un objeto `structured_task_group` dentro de otro objeto `structured_task_group`, el objeto interno debe finalizar y destruirse antes de que el objeto externo finalice. La clase `task_group` no requiere que los grupos de tareas anidadas finalicen antes de que finalice el grupo externo.

Los grupos de tareas con y sin estructura funcionan con identificadores de tareas de distinta forma. Se pueden pasar funciones de trabajo directamente a un objeto `task_group`; el objeto `task_group` creará y administrará el identificador de tarea automáticamente. La clase `structured_task_group` requiere que se administre un objeto `task_handle` por cada tarea. Cada objeto `task_handle` tiene que ser válido a lo largo de toda la duración del objeto `structured_task_group` asociado. Use la [Concurrency:: make_task](reference/concurrency-namespace-functions.md#make_task) función para crear un `task_handle` de objeto, como se muestra en el siguiente ejemplo básico:

[!code-cpp[concrt-make-task-structure#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_16.cpp)]

Para administrar los identificadores de tarea para los casos donde haya un número variable de tareas, use una rutina de asignación de pila como [_malloca](../../c-runtime-library/reference/malloca.md) o una clase de contenedor, como std::[vector](../../standard-library/vector-class.md).

Tanto `task_group` como `structured_task_group` admiten la cancelación. Para obtener más información sobre la cancelación, vea [cancelación en PPL](cancellation-in-the-ppl.md).

##  <a name="example"></a> Ejemplo

En el siguiente ejemplo básico se indica cómo trabajar con grupos de tareas. En él se usa el algoritmo `parallel_invoke` para realizar dos tareas simultáneamente. Cada tarea agrega subtareas a un objeto `task_group`. Tenga en cuenta que la clase `task_group` permite que varias tareas agreguen tareas al objeto al mismo tiempo.

[!code-cpp[concrt-using-task-groups#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_17.cpp)]

Aquí mostramos la salida de muestra de este ejemplo:

```Output
Message from task: Hello
Message from task: 3.14
Message from task: 42
```

El algoritmo `parallel_invoke` ejecuta tareas de forma simultánea, por lo que el orden de los mensajes de salida podría variar.

Para obtener ejemplos completos que muestran cómo usar el `parallel_invoke` algoritmo, vea [Cómo: Usar Parallel.Invoke para escribir una rutina de ordenación en paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) y [Cómo: Usar Parallel.Invoke para ejecutar operaciones paralelas](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md). Para obtener un ejemplo completo que usa el `task_group` clase para implementar futuros asincrónicos, vea [Tutorial: Implementar futuros](../../parallel/concrt/walkthrough-implementing-futures.md).

##  <a name="robust"></a> Programación sólida

Asegúrese de que comprende el rol de cancelación y control de excepciones cuando use tareas, grupos de tareas y algoritmos paralelos. Por ejemplo, en un árbol de trabajo paralelo, una tarea que se cancela impide que se ejecuten las tareas secundarias. Esto puede causar problemas si una de las tareas secundarias realiza una operación que tiene importancia para la aplicación, como liberar un recurso. Además, si una tarea secundaria genera una excepción, esta podría propagarse a través de un destructor de objetos y provocar un comportamiento no definido en la aplicación. Para obtener un ejemplo que ilustre estos aspectos, vea el [entender cómo la cancelación y la excepción control afectan a la destrucción de objetos](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) sección de procedimientos recomendados en el documento de Parallel Patterns Library. Para obtener más información sobre los modelos de control de excepciones en la biblioteca PPL y la cancelación, vea [cancelación](../../parallel/concrt/cancellation-in-the-ppl.md) y [Exception Handling](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="related-topics"></a>Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[Cómo: Usar parallel.invoke para escribir una rutina de ordenación en paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Muestra cómo usar el algoritmo `parallel_invoke` para mejorar el rendimiento del algoritmo de ordenación bitónica.|
|[Cómo: Usar parallel_invoke para ejecutar operaciones en paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Muestra cómo usar el algoritmo `parallel_invoke` para mejorar el rendimiento de un programa que realiza varias operaciones en un origen de datos compartido.|
|[Cómo: Crear una tarea que se complete después de un retardo](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Se muestra cómo usar el `task`, `cancellation_token_source`, `cancellation_token`, y `task_completion_event` las clases para crear una tarea que finaliza después de un retraso.|
|[Tutorial: Implementación de futuros](../../parallel/concrt/walkthrough-implementing-futures.md)|Muestra cómo combinar la funcionalidad existente en el Runtime de simultaneidad para ampliar capacidades.|
|[Biblioteca de patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Describe la biblioteca PPL, que proporciona un modelo de programación imperativo para desarrollar aplicaciones simultáneas.|

## <a name="reference"></a>Referencia

[task (clase) (Runtime de simultaneidad)](../../parallel/concrt/reference/task-class.md)

[task_completion_event (clase)](../../parallel/concrt/reference/task-completion-event-class.md)

[when_all (función)](reference/concurrency-namespace-functions.md#when_all)

[when_any (función)](reference/concurrency-namespace-functions.md#when_any)

[task_group (clase)](reference/task-group-class.md)

[parallel_invoke (función)](reference/concurrency-namespace-functions.md#parallel_invoke)

[structured_task_group (clase)](../../parallel/concrt/reference/structured-task-group-class.md)
