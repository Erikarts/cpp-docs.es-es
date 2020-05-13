---
title: 'Tutorial: Crear un bloque de mensajes personalizado'
ms.date: 04/25/2019
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
ms.openlocfilehash: 3386994dce68812cf3ed0852a24d8910cb903acf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368555"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>Tutorial: Crear un bloque de mensajes personalizado

En este documento se describe cómo crear un tipo de bloque de mensajes personalizado que ordena los mensajes entrantes por prioridad.

Aunque los tipos integrados de bloques de mensajes proporciona una amplia gama de funcionalidad, puede crear su propio tipo de bloque de mensajes y personalizarlo para satisfacer los requisitos de la aplicación. Para obtener una descripción de los tipos de bloquedes de mensajes integrados proporcionados por la biblioteca de agentes asincrónicos, vea Bloques de mensajes [asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="prerequisites"></a>Prerrequisitos

Lea los documentos siguientes antes de iniciar este tutorial:

- [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funciones de paso de mensajes](../../parallel/concrt/message-passing-functions.md)

## <a name="sections"></a><a name="top"></a>Secciones

Este tutorial contiene las siguientes secciones:

- [Diseñar un bloque de mensajes personalizado](#design)

- [Definir la clase priority_buffer](#class)

- [Ejemplo completo](#complete)

## <a name="designing-a-custom-message-block"></a><a name="design"></a>Diseño de un bloque de mensajes personalizado

Los bloques de mensajes participan en el acto de enviar y recibir mensajes. Un bloque de mensajes que envía mensajes se conoce como bloque de *origen.* Un bloque de mensajes que recibe mensajes se conoce como bloque de *destino.* Un bloque de mensajes que envía y recibe mensajes se conoce como *bloque de propagador.* La biblioteca de agentes utiliza la clase abstracta [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) para representar bloques de origen y la clase abstracta [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) para representar bloques de destino. Los tipos de bloques de mensajes que actúan como orígenes derivan de `ISource`; los tipos de bloques de mensajes que actúan como destinos derivan de `ITarget`.

Aunque puede derivar el tipo de bloque de mensajes directamente de `ISource` y `ITarget`, la Biblioteca de agentes define tres clases base que realizan gran parte de la funcionalidad común a todos los tipos de bloques de mensajes; por ejemplo, control de errores y conexión de los bloques de mensajes de manera segura para simultaneidad. La clase [concurrency::source_block](../../parallel/concrt/reference/source-block-class.md) `ISource` deriva y envía mensajes a otros bloques. La [clase concurrency::target_block](../../parallel/concrt/reference/target-block-class.md) `ITarget` deriva y recibe mensajes de otros bloques. La clase [concurrency::propagator_block](../../parallel/concrt/reference/propagator-block-class.md) `ISource` deriva `ITarget` y envía mensajes a otros bloques y recibe mensajes de otros bloques. Se recomienda usar estas tres clases base para controlar los detalles de infraestructura de modo que se pueda centrar en el comportamiento del bloque de mensajes.

Las clases `source_block`, `target_block` y `propagator_block` son plantillas que se parametrizan en un tipo que administra las conexiones, o vínculos, entre los bloques de origen y de destino y en un tipo que administra cómo se procesan los mensajes. La biblioteca de agentes define dos tipos que realizan la administración de vínculos, [concurrency::single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md) y [concurrency::multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md). La clase `single_link_registry` permite vincular un bloque de mensajes a un origen o a un destino. La clase `multi_link_registry` permite vincular un bloque de mensajes a varios orígenes o a varios destinos. La biblioteca de agentes define una clase que realiza la administración de mensajes, [concurrency::ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md). La clase `ordered_message_processor` permite que los bloques de mensajes procesen los mensajes en el orden en que se reciben.

Para entender mejor cómo se relacionan los bloques de mensajes con sus orígenes y destinos, considere el ejemplo siguiente. En este ejemplo se muestra la declaración de la clase [concurrency::transformer.](../../parallel/concrt/reference/transformer-class.md)

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

La clase `transformer` se deriva de `propagator_block` y, por tanto, actúa como bloque de origen y como bloque de destino. Acepta mensajes de tipo `_Input` y envía mensajes de tipo `_Output`. La clase `transformer` especifica `single_link_registry` como administrador de vínculos para los bloques de destino y `multi_link_registry` como administrador de vínculos para los bloques de origen. Por tanto, un objeto `transformer` puede tener hasta un destino y un número ilimitado de orígenes.

Una clase que `source_block` se deriva debe implementar seis métodos: [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets), [accept_message](reference/source-block-class.md#accept_message), [reserve_message](reference/source-block-class.md#reserve_message), [consume_message](reference/source-block-class.md#consume_message), [release_message](reference/source-block-class.md#release_message)y [resume_propagation](reference/source-block-class.md#resume_propagation). Una clase que `target_block` deriva de debe implementar el [propagate_message](reference/propagator-block-class.md#propagate_message) método y opcionalmente puede implementar el [send_message](reference/propagator-block-class.md#send_message) método. Derivar de `propagator_block` es funcionalmente equivalente a la derivación de `source_block` y `target_block`.

El runtime llama al método `propagate_to_any_targets` para procesar de forma sincrónica o asincrónica los mensajes entrantes y propagar los mensajes salientes. Los bloques de destino llaman al método `accept_message` para aceptar mensajes. Muchos tipos de bloques de mensajes, como `unbounded_buffer`, envían mensajes solo al primer destino que los recibiría. Por tanto, transfiere la propiedad del mensaje al destino. Otros tipos de bloques de mensajes, como [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md), ofrecen mensajes a cada uno de sus bloques de destino. Por tanto, `overwrite_buffer` crea una copia del mensaje para cada uno de sus destinos.

Los métodos `reserve_message`, `consume_message`, `release_message` y `resume_propagation` permiten a los bloques de mensajes participar en la reserva de mensajes. Los bloques de destino llaman al método `reserve_message` cuando se les ofrece un mensaje y tienen que reservar el mensaje para su uso posterior. Después de que un bloque de destino reserva un mensaje, puede llamar al método `consume_message` para usar ese mensaje o al método `release_message` para cancelar la reserva. Como sucede con el método `accept_message`, la implementación de `consume_message` puede transferir la propiedad del mensaje o devolver una copia del mensaje. Después de que un bloque de destino usa o libera un mensaje reservado, el runtime llama al método `resume_propagation`. Normalmente, este método continúa la propagación de mensajes, comenzando por el siguiente mensaje de la cola.

El runtime llama al método `propagate_message` para transferir de forma asincrónica un mensaje de otro bloque al actual. El método `send_message` es similar a `propagate_message`, excepto en que envía de forma sincrónica, en lugar de asincrónica, el mensaje a los bloques de destino. La implementación predeterminada de `send_message` rechaza todos los mensajes entrantes. El runtime no llama a ninguno de estos métodos si el mensaje no supera la función opcional de filtro asociada al bloque de destino. Para obtener más información acerca de los filtros de mensajes, vea Bloques de mensajes [asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md).

[[Superior](#top)]

## <a name="defining-the-priority_buffer-class"></a><a name="class"></a>Definición de la clase priority_buffer

La clase `priority_buffer` es un tipo de bloque de mensajes personalizado que ordena los mensajes entrantes primero por prioridad y, a continuación, en el orden en que se reciben los mensajes. La `priority_buffer` clase es similar a la [clase concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) porque contiene una cola de mensajes y también porque actúa como un bloque de mensajes de origen y de destino y puede tener varios orígenes y varios destinos. Sin embargo, `unbounded_buffer` basa la propagación de mensaje solo en el orden en que recibe mensajes de sus orígenes.

La `priority_buffer` clase recibe mensajes de tipo std:: `Type` [tupla](../../standard-library/tuple-class.md) que contienen `PriorityType` y elementos. `PriorityType` se refiere al tipo que contiene la prioridad de cada mensaje; `Type` se refiere a la parte de datos del mensaje. La clase `priority_buffer` envía mensajes de tipo `Type`. La `priority_buffer` clase también administra dos colas de mensajes: un objeto [std::priority_queue](../../standard-library/priority-queue-class.md) para los mensajes entrantes y un objeto de[cola](../../standard-library/queue-class.md) std:: para los mensajes salientes. Ordenar los mensajes por prioridad es útil cuando un objeto `priority_buffer` recibe varios mensajes simultáneamente o cuando recibe varios mensajes antes de que los consumidores lean cualquier mensaje.

Además de los siete métodos que una clase derivada de `propagator_block` debe implementar, la clase `priority_buffer` también invalida los métodos `link_target_notification` y `send_message`. La clase `priority_buffer` también define dos métodos del asistente públicos, `enqueue` y `dequeue`, y un método del asistente privado, `propagate_priority_order`.

En el procedimiento siguiente se describe cómo implementar la clase `priority_buffer`.

#### <a name="to-define-the-priority_buffer-class"></a>Para definir la clase priority_buffer

1. Cree un archivo de encabezado `priority_buffer.h`C++ y asímócelo . O bien, puede usar un archivo de encabezado existente que forme parte del proyecto.

1. En `priority_buffer.h`, agregue el código siguiente.

    [!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. En `std` el espacio de nombres, defina especializaciones de [std::less](../../standard-library/less-struct.md) y [std::greater](../../standard-library/greater-struct.md) que actúan sobre objetos de[mensaje](../../parallel/concrt/reference/message-class.md) concurrency::.

    [!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

   La clase `priority_buffer` almacena objetos `message` en un objeto `priority_queue`. Estas especializaciones de tipo permiten a la cola de prioridad ordenar los mensajes según su prioridad. La prioridad es el primer elemento del objeto `tuple`.

1. En el espacio de nombres `concurrencyex`, declare la clase `priority_buffer`.

    [!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

   La clase `priority_buffer` se deriva de `propagator_block`. Por tanto, puede enviar y recibir mensajes. La clase `priority_buffer` puede tener varios destinos que reciben mensajes de tipo `Type`. También puede tener varios orígenes que envían mensajes de tipo `tuple<PriorityType, Type>`.

1. En la sección `private` de la clase `priority_buffer`, agregue las variables miembro siguientes.

    [!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

   El objeto `priority_queue` contiene mensajes entrantes; el objeto `queue` contiene mensajes salientes. Un objeto `priority_buffer` puede recibir varios mensajes simultáneamente; el objeto `critical_section` sincroniza el acceso a la cola de mensajes entrantes.

1. En la sección `private`, defina el constructor de copias y el operador de asignación. Esto impide que los objetos `priority_queue` sean asignables.

    [!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. En la sección `public`, defina los constructores que son comunes a muchos tipos de bloques de mensajes. Defina también el destructor.

    [!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. En la sección `public`, defina los métodos `enqueue` y `dequeue`. Estos métodos del asistente proporcionan una manera alternativa de enviar mensajes a y recibir mensajes de un objeto `priority_buffer`.

    [!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

1. En la sección `protected`, defina el método `propagate_to_any_targets`.

    [!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

   El método `propagate_to_any_targets` transfiere a la cola de salida el mensaje que está al principio de la cola de entrada y propaga todos los mensajes de la cola de salida.

1. En la sección `protected`, defina el método `accept_message`.

    [!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

   Cuando un bloque de destino llama al método `accept_message`, la clase `priority_buffer` transfiere la propiedad del mensaje al primer bloque de destino que lo acepta. (Esto es similar al comportamiento de `unbounded_buffer`.)

1. En la sección `protected`, defina el método `reserve_message`.

    [!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

   La clase `priority_buffer` permite a un bloque de destino reservar un mensaje cuando el identificador de mensaje proporcionado coincide con el identificador de mensaje que está en el principio de la cola. Es decir, un destino puede reservar el mensaje si el objeto `priority_buffer` aún no ha recibido un mensaje adicional y aún no ha propagado el actual.

1. En la sección `protected`, defina el método `consume_message`.

    [!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

   Un bloque de destino llama a `consume_message` para transferir la propiedad del mensaje reservado.

1. En la sección `protected`, defina el método `release_message`.

    [!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

   Un bloque de destino llama a `release_message` para cancelar la reserva un mensaje.

1. En la sección `protected`, defina el método `resume_propagation`.

    [!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

   El runtime llama a `resume_propagation` después de que un bloque de destino use o libere un mensaje reservado. Este método propaga cualquier mensaje que esté en la cola de salida.

1. En la sección `protected`, defina el método `link_target_notification`.

    [!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

   La variable miembro `_M_pReservedFor` está definida por la clase base, `source_block`. Esta variable miembro apunta al bloque de destino, si existe, que mantiene una reserva del mensaje que está al principio de la cola de salida. El runtime llama a `link_target_notification` cuando un nuevo destino se vincula al objeto `priority_buffer`. Este método propaga cualquier mensaje que está en la cola de salida si ningún destino mantiene una reserva.

1. En la sección `private`, defina el método `propagate_priority_order`.

    [!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

   Este método propaga todos los mensajes de la cola de salida. Todos los mensajes de la cola se ofrecen a todos los bloques de destino hasta que uno de los bloques de destino acepta el mensaje. La clase `priority_buffer` conserva el orden de los mensajes salientes. Por tanto, un bloque de destino debe aceptar el primer mensaje de la cola de salida antes de que este método ofrezca ningún otro mensaje a los bloques de destino.

1. En la sección `protected`, defina el método `propagate_message`.

    [!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

   El método `propagate_message` permite que la clase `priority_buffer` actúe como receptor de mensajes o destino. Este método recibe el mensaje ofrecido por el bloque de origen proporcionado e inserta ese mensaje en la cola de prioridad. El método `propagate_message` envía de forma asincrónica todos los mensajes de salida a los bloques de destino.

   El tiempo de ejecución llama a este método cuando se llama a la función [concurrency::asend](reference/concurrency-namespace-functions.md#asend) o cuando el bloque de mensajes está conectado a otros bloques de mensajes.

1. En la sección `protected`, defina el método `send_message`.

    [!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

   El método `send_message` es similar a `propagate_message`. Sin embargo, envía los mensajes de salida sincrónicamente en lugar de hacerlo de forma asincrónica.

   El tiempo de ejecución llama a este método durante una operación de envío sincrónica, como cuando se llama a la función [concurrency::send.](reference/concurrency-namespace-functions.md#send)

La clase `priority_buffer` contiene sobrecargas del constructor que son típicas en muchos tipos de bloques de mensajes. Algunas sobrecargas de constructor toman [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) o [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objetos, que permiten que el bloque de mensajes sea administrado por un programador de tareas específico. Otras sobrecargas del constructor toman una función de filtro. Las funciones de filtro permiten a los bloques de mensajes aceptar o rechazar un mensaje en función de su carga. Para obtener más información acerca de los filtros de mensajes, vea Bloques de mensajes [asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md). Para obtener más información acerca de los programadores de tareas, vea [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Dado `priority_buffer` que la clase ordena los mensajes por prioridad y, a continuación, por el orden en que se reciben los mensajes, esta clase es más útil cuando recibe mensajes de forma asincrónica, por ejemplo, cuando se llama a la función [concurrency::asend](reference/concurrency-namespace-functions.md#asend) o cuando el bloque de mensajes está conectado a otros bloques de mensajes.

[[Superior](#top)]

## <a name="the-complete-example"></a><a name="complete"></a>El ejemplo completo

En el ejemplo siguiente se muestra la definición completa de la clase `priority_buffer`.

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

En el ejemplo siguiente se `asend` realizan simultáneamente un número `priority_buffer` de y [concurrency::receive](reference/concurrency-namespace-functions.md#receive) operaciones en un objeto.

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

Este ejemplo genera la siguiente salida de ejemplo.

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

La clase `priority_buffer` ordena los mensajes primero por prioridad y, a continuación, por el orden en que recibe los mensajes. En este ejemplo, los mensajes con mayor prioridad numérica se insertan al principio de la cola.

[[Superior](#top)]

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un `priority_buffer` proyecto de Visual `priority_buffer.h` Studio, o pegue la definición de la clase en un archivo con nombre y el programa de prueba en un archivo con nombre `priority_buffer.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe /EHsc priority_buffer.cpp**

## <a name="see-also"></a>Consulte también

[Tutoriales en tiempo de ejecución de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funciones de paso de mensajes](../../parallel/concrt/message-passing-functions.md)
