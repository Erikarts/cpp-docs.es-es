---
title: Procedimientos recomendados generales con el Runtime de simultaneidad
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
ms.openlocfilehash: 15bae5ba25da4987b076cf3de67cd8484fe47df8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141767"
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>Procedimientos recomendados generales con el Runtime de simultaneidad

En este documento se describen los procedimientos recomendados que se aplican a varias áreas del runtime de simultaneidad.

## <a name="top"></a> Secciones

Este documento contiene las siguientes secciones:

- [Usar construcciones de sincronización cooperativa cuando sea posible](#synchronization)

- [Evitar tareas largas que no producen](#yield)

- [Usar la suscripción excesiva para desplazar las operaciones que bloquean o tienen una latencia alta](#oversubscription)

- [Usar funciones de administración de memoria simultáneas siempre que sea posible](#memory)

- [Usar RAII para administrar la duración de los objetos de simultaneidad](#raii)

- [No crear objetos de simultaneidad en el ámbito global](#global-scope)

- [No usar objetos de simultaneidad en segmentos de datos compartidos](#shared-data)

## <a name="synchronization"></a>Usar construcciones de sincronización cooperativa cuando sea posible

El runtime de simultaneidad proporciona muchas construcciones seguras para simultaneidad que no requieren un objeto de sincronización externo. Por ejemplo, la clase [Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) proporciona operaciones de anexado y acceso a elementos con seguridad de simultaneidad. Aquí, la seguridad de simultaneidad significa que los punteros o iteradores siempre son válidos. No es una garantía de la inicialización de elementos o de un orden de cruce determinado. Sin embargo, para los casos en los que se requiere acceso exclusivo a un recurso, el tiempo de ejecución proporciona las clases Concurrency [:: critical_section](../../parallel/concrt/reference/critical-section-class.md), [Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)y [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) . Estos tipos se comportan de forma cooperativa; por consiguiente, el programador de tareas puede reasignar los recursos de procesamiento a otro contexto mientras la primera tarea espera los datos. Cuando sea posible, use estos tipos de sincronización en lugar de otros mecanismos de sincronización, como los proporcionados por la API de Windows, que no se comportan de manera cooperativa. Para obtener más información sobre estos tipos de sincronización y un ejemplo de código, vea [sincronización de estructuras de datos](../../parallel/concrt/synchronization-data-structures.md) y comparación de estructuras de datos de [sincronización con la API de Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).

[[Arriba](#top)]

## <a name="yield"></a>Evitar tareas largas que no producen

Dado que el programador de tareas se comporta de forma cooperativa, no es ecuánime entre las tareas. Por consiguiente, una tarea puede evitar que se inicien otras tareas. Aunque esto es aceptable en algunos casos, en otros puede producir un interbloqueo o un colapso.

En el siguiente ejemplo se realizan más tareas que el número de recursos de procesamiento asignados. La primera tarea no produce resultados en el programador de tareas y, por consiguiente, la segunda tarea no se inicia hasta que finaliza la primera tarea.

[!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]

En este ejemplo se produce la siguiente salida:

1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000

Hay varias maneras de habilitar la cooperación entre las dos tareas. Una consiste en producir ocasionalmente resultados de una tarea de ejecución prolongada en el programador de tareas. En el ejemplo siguiente se modifica la función `task` para llamar al método [Concurrency:: context:: yield](reference/context-class.md#yield) para producir la ejecución en el programador de tareas para que se pueda ejecutar otra tarea.

[!code-cpp[concrt-cooperative-tasks#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_2.cpp)]

En este ejemplo se produce la siguiente salida:

```Output
1: 250000000
2: 250000000
1: 500000000
2: 500000000
1: 750000000
2: 750000000
1: 1000000000
2: 1000000000
```

El método `Context::Yield` produce solo otro subproceso activo en el programador al que pertenece el subproceso actual, una tarea ligera u otro subproceso del sistema operativo. Este método no da lugar a que el trabajo esté programado para ejecutarse en un objeto [Concurrency:: task_group](reference/task-group-class.md) o [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) pero todavía no se ha iniciado.

Hay otras maneras de habilitar la cooperación entre las tareas de ejecución prolongada. Puede dividir una tarea larga en otras más pequeñas. También puede habilitar la sobresuscripción durante una tarea larga. La sobresuscripción le permite crear más subprocesos que el número de subprocesos de hardware disponibles. La sobresuscripción es especialmente útil cuando una tarea larga contiene mucha latencia, por ejemplo, al leer datos del disco o de una conexión de red. Para obtener más información sobre las tareas ligeras y la suscripción excesiva, consulte [programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Arriba](#top)]

## <a name="oversubscription"></a>Usar la suscripción excesiva para desplazar las operaciones que bloquean o tienen una latencia alta

El Runtime de simultaneidad proporciona primitivas de sincronización, como [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md), que permiten que las tareas se bloqueen y se produzcan entre sí de forma cooperativa. Cuando una tarea se bloquea de forma cooperativa o produce resultados, el programador de tareas puede reasignar los recursos de procesamiento a otro contexto mientras la primera tarea espera los datos.

Hay casos en los que no se puede usar el mecanismo de bloqueo cooperativo que el runtime de simultaneidad proporciona. Por ejemplo, una biblioteca externa que usa podría emplear un mecanismos de sincronización diferente. Otro ejemplo es el caso en el que realiza una operación que podría tener mucha latencia, por ejemplo, cuando se usa la función de la API de Windows `ReadFile` para leer datos de una conexión de red. En estos casos, la sobresuscripción puede permitir que otras tareas se ejecuten cuando otra tarea está inactiva. La sobresuscripción le permite crear más subprocesos que el número de subprocesos de hardware disponibles.

Considere la función siguiente, `download`, que descarga el archivo en la dirección URL dada. En este ejemplo se usa el método [Concurrency:: context:: subsubscribe](reference/context-class.md#oversubscribe) para aumentar temporalmente el número de subprocesos activos.

[!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]

Dado que la función `GetHttpFile` realiza una operación potencialmente latente, la sobresuscripción puede permitir que otras tareas se ejecuten mientras la tarea actual espera los datos. Para obtener la versión completa de este ejemplo, consulte [Cómo: usar la sobresuscripción a la latencia de desplazamiento](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

[[Arriba](#top)]

## <a name="memory"></a>Usar funciones de administración de memoria simultáneas siempre que sea posible

Use las funciones de administración de memoria, [Concurrency:: Alloc](reference/concurrency-namespace-functions.md#alloc) y [Concurrency:: Free](reference/concurrency-namespace-functions.md#free), cuando tenga tareas específicas que asignan con frecuencia objetos pequeños que tienen una duración relativamente corta. El runtime de simultaneidad contiene una memoria caché independiente para cada subproceso en ejecución. Las funciones `Alloc` y `Free` asignan y liberan memoria de estas memorias caché sin el uso de bloqueos ni barreras de memoria.

Para obtener más información acerca de estas funciones de administración de memoria, consulte [programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Para obtener un ejemplo en el que se usan estas funciones, consulte [Cómo: usar Alloc y Free para mejorar el rendimiento de la memoria](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).

[[Arriba](#top)]

## <a name="raii"></a>Usar RAII para administrar la duración de los objetos de simultaneidad

El runtime de simultaneidad usa el control de excepciones para implementar características como la cancelación. Por consiguiente, escriba el código seguro para excepciones cuando se llama al runtime o a otra biblioteca que llama al runtime.

El patrón *Resource Acquisition Is Initialization* (RAII) es una manera de administrar de forma segura la duración de un objeto de simultaneidad en un ámbito determinado. Bajo el modelo RAII, se asigna una estructura de datos en la pila. Esa estructura de datos se inicializa o adquiere un recurso cuando se crea, y destruye o libera ese recurso cuando se destruye la estructura de datos. El modelo RAII garantiza que se llama al destructor antes de que el ámbito de inclusión salga. Este modelo resulta útil cuando una función contiene varias instrucciones `return`. Este modelo también le ayuda a escribir código seguro para excepciones. Cuando una instrucción `throw` hace que la pila se desenrede, se llama al destructor del objeto RAII; por consiguiente, el recurso siempre se elimina o se libera correctamente.

El tiempo de ejecución define varias clases que usan el patrón RAII, por ejemplo, [Concurrency:: critical_section:: scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class) y [Concurrency:: reader_writer_lock:: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class). Estas clases auxiliares se conocen como *bloqueos de ámbito*. Estas clases proporcionan varias ventajas cuando se trabaja con objetos [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) o [Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) . El constructor de estas clases adquiere el acceso al objeto `critical_section` o `reader_writer_lock` proporcionado; el destructor libera el acceso a ese objeto. Dado que un bloqueo con ámbito libera automáticamente el acceso a su objeto de exclusión mutua cuando se destruye; por consiguiente, no se desbloquea manualmente el objeto subyacente.

Considere la siguiente clase, `account`, que se define mediante una biblioteca externa y, por consiguiente, no se puede modificar.

[!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]

En el siguiente ejemplo se realizan varias transacciones en un objeto `account` en paralelo. En el ejemplo se usa un objeto `critical_section` para sincronizar el acceso al objeto `account` porque la clase `account` no es segura para simultaneidad. Cada operación paralela usa un objeto `critical_section::scoped_lock` para garantizar que el objeto `critical_section` se desbloquea cuando la operación se realiza correctamente o tiene errores. Cuando el saldo de cuenta es negativo, la operación `withdraw` produce un error e inicia una excepción.

[!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_5.cpp)]

Este ejemplo genera la siguiente salida de ejemplo:

```Output
Balance before deposit: 1924
Balance after deposit: 2924
Balance before withdrawal: 2924
Balance after withdrawal: -76
Balance before withdrawal: -76
Error details:
    negative balance: -76
```

Para obtener ejemplos adicionales que usan el patrón RAII para administrar la duración de los objetos de simultaneidad, vea [Tutorial: quitar trabajo de un subproceso](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)de la interfaz de usuario, [Cómo: usar la clase context para implementar un semáforo cooperativo](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)y [Cómo: usar la sobresuscripción a la latencia de desplazamiento](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

[[Arriba](#top)]

## <a name="global-scope"></a>No crear objetos de simultaneidad en el ámbito global

Cuando se crea un objeto de simultaneidad en el ámbito global, pueden surgir problemas en la aplicación, como infracciones de acceso a la memoria o interbloqueo.

Por ejemplo, cuando se crea un objeto de runtime de simultaneidad, el runtime crea un programador predeterminado para el usuario si aún no se había creado. Un objeto en tiempo de ejecución creado durante la construcción de objetos globales provocará que el runtime cree este programador predeterminado. Sin embargo, este proceso utiliza un bloqueo interno, lo que puede interferir con la inicialización de otros objetos que admiten la infraestructura del runtime de simultaneidad. Otro objeto de la infraestructura que aún no se haya inicializado podría requerir este bloqueo interno y provocar, por tanto, un interbloqueo en la aplicación.

En el ejemplo siguiente se muestra la creación de un objeto [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) global. Este patrón no se aplica solo a la clase `Scheduler`, sino también al resto de tipos que proporciona el runtime de simultaneidad. Es recomendable que no siga este patrón, ya que puede provocar un comportamiento inesperado en la aplicación.

[!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]

Para obtener ejemplos de la forma correcta de crear objetos `Scheduler`, vea [programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Arriba](#top)]

## <a name="shared-data"></a>No usar objetos de simultaneidad en segmentos de datos compartidos

El Runtime de simultaneidad no admite el uso de objetos de simultaneidad en una sección de datos compartidos, por ejemplo, una sección de datos creada por la Directiva de`#pragma` de [data_seg](../../preprocessor/data-seg.md) . Un objeto de simultaneidad que se comparte entre los límites del proceso puede colocar el runtime en un estado incoherente o no válido.

[[Arriba](#top)]

## <a name="see-also"></a>Consulte también

[Procedimientos recomendados del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[Biblioteca de patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Estructuras de datos de sincronización](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Comparación de estructuras de datos de sincronización con la API de Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
[Procedimiento para usar Alloc y Free para mejorar el rendimiento de la memoria](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)<br/>
[Procedimiento para usar la suscripción excesiva para compensar la latencia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)<br/>
[Procedimiento para usar la clase Context para implementar un semáforo cooperativo](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[Tutorial: Quitar trabajo de un subproceso de la interfaz de usuario](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
[Procedimientos recomendados en la biblioteca de modelos paralelos](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[Procedimientos recomendados en la biblioteca de agentes asincrónicos](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)
