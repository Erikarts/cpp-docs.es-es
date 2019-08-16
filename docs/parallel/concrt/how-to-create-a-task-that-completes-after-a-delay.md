---
title: Procedimiento Crear una tarea que finaliza después de un retraso
ms.date: 11/04/2016
helpviewer_keywords:
- task_completion_event class, example
- create a task that completes after a delay, example [C++]
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
ms.openlocfilehash: 3292043d7900d5dc2bfba0afa5fdc237853a5be0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413910"
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>Procedimiento Crear una tarea que finaliza después de un retraso

En este ejemplo se muestra cómo usar el [Concurrency:: Task](../../parallel/concrt/reference/task-class.md), [Concurrency:: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md), [cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md), [ Concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), [Concurrency:: Timer](../../parallel/concrt/reference/timer-class.md), y [Concurrency:: call](../../parallel/concrt/reference/call-class.md) las clases para crear una tarea que finaliza después de un retraso. Puede usar este método para crear bucles que ocasionalmente sondear en busca de datos, introducen los tiempos de espera, retrasar el control de entrada de usuario para un tiempo predeterminado y así sucesivamente.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran las funciones `complete_after` y `cancel_after_timeout`. El `complete_after` función crea un `task` objeto que se complete después del retraso especificado. Usa un `timer` objeto y un `call` objeto para establecer un `task_completion_event` objeto después del retraso especificado. Mediante el uso de la `task_completion_event` (clase), puede definir una tarea que finaliza después de que un subproceso o de otra tarea señala que un valor está disponible. Cuando se establece el evento, completen las tareas de agente de escucha y sus continuaciones se programan para ejecutarse.

> [!TIP]
>  Para obtener más información sobre la `timer` y `call` clases, que forman parte de la biblioteca de agentes asincrónicos, vea [bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md).

El `cancel_after_timeout` función se basa en el `complete_after` función para cancelar una tarea si no se completa dicha tarea antes de un tiempo de espera especificado. El `cancel_after_timeout` función crea dos tareas. Indica el éxito de la primera tarea y se completa una vez completada la tarea proporcionada; la segunda tarea indica un error y finaliza tras el tiempo de espera especificado. El `cancel_after_timeout` función crea una tarea de continuación que se ejecuta cuando se completa la tarea de éxito o error. Si la tarea de error completa la primera, la continuación cancela el origen del token para cancelar la tarea global.

[!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]

## <a name="example"></a>Ejemplo

El ejemplo siguiente calcula el recuento de números primos en el intervalo [0, 100000] varias veces. La operación produce un error si no se completa en un límite de tiempo determinado. El `count_primes` función muestra cómo utilizar el `cancel_after_timeout` función. Cuenta el número de bloqueos del intervalo especificado y se produce un error si no se completa la tarea en el tiempo proporcionado. El `wmain` llamadas de función el `count_primes` función varias veces. Cada vez, lo mitades del límite de tiempo. El programa finaliza después de la operación no se lleva a cabo en el límite de tiempo actual.

[!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]

Cuando se usa esta técnica para cancelar las tareas después de un retraso, no se iniciará ninguna tarea sin iniciar después de cancela la tarea global. Sin embargo, es importante para las tareas de ejecución prolongada responder a la cancelación de manera oportuna. Para obtener más información sobre la cancelación de tareas, consulte [cancelación en PPL](cancellation-in-the-ppl.md).

## <a name="example"></a>Ejemplo

Este es el código completo de este ejemplo:

[!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]

## <a name="compiling-the-code"></a>Compilar el código

Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `task-delay.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**tarea/EHsc-delay.cpp de CL.exe**

## <a name="see-also"></a>Vea también

[Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[task (clase) (Runtime de simultaneidad)](../../parallel/concrt/reference/task-class.md)<br/>
[cancellation_token_source (clase)](../../parallel/concrt/reference/cancellation-token-source-class.md)<br/>
[cancellation_token (clase)](../../parallel/concrt/reference/cancellation-token-class.md)<br/>
[task_completion_event (clase)](../../parallel/concrt/reference/task-completion-event-class.md)<br/>
[timer (clase)](../../parallel/concrt/reference/timer-class.md)<br/>
[call (clase)](../../parallel/concrt/reference/call-class.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)
