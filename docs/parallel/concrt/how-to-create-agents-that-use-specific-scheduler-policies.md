---
title: 'Cómo: Crear agentes que usen directivas de Scheduler específicas'
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
ms.openlocfilehash: ece6b113e3fe10c2c3179517f73137df281acf87
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141733"
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>Cómo: Crear agentes que usen directivas de Scheduler específicas

Un agente es un componente de aplicación que funciona de forma asincrónica con otros componentes para resolver tareas de computación mayores. Normalmente, un agente tiene un ciclo de vida establecido y mantiene el estado.

Cada agente puede tener requisitos de aplicación únicos. Por ejemplo, un agente que permite la interacción con el usuario (ya sea al recuperar la entrada o al mostrar la salida) puede requerir un acceso más prioritario a los recursos informáticos. Las directivas de Scheduler permiten controlar la estrategia que el programador utiliza cuando administra tareas. En este tema se muestra cómo crear agentes que usen directivas de programador específicas.

Para obtener un ejemplo básico en el que se usan directivas de programador personalizadas junto con bloques de mensajes asincrónicos, vea [Cómo: especificar directivas de programador específicas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).

En este tema se usa la funcionalidad de la Biblioteca de agentes asincrónicos, como agentes, bloques de mensaje y funciones para pasar mensajes, para realizar el trabajo. Para obtener más información sobre la biblioteca de agentes asincrónicos, vea [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se definen dos clases que derivan de [Concurrency:: Agent](../../parallel/concrt/reference/agent-class.md): `permutor` y `printer`. La clase `permutor` calcula todas las permutaciones de una cadena de entrada determinada. La clase `printer` imprime los mensajes de progreso en la consola. La clase `permutor` realiza una operación que requiere gran cantidad de recursos de computación y que podría usar todos los recursos disponibles. Para ser útil, la clase `printer` debe imprimir cada mensaje de progreso de una manera puntual.

Para proporcionar a la clase `printer` el acceso equitativo a los recursos informáticos, en este ejemplo se usan los pasos que se describen en [Cómo: administrar una instancia del programador](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) para crear una instancia de Scheduler que tenga una directiva personalizada. La directiva personalizada especifica la prioridad del subproceso como la clase de prioridad máxima.

Para mostrar las ventajas de utilizar un programador que tiene una directiva personalizada, en el ejemplo se realiza la tarea dos veces. Primero se usa el programador predeterminado para programar ambas tareas. A continuación, se usa el programador predeterminado para programar el objeto `permutor` y un programador con una directiva personalizada para programar el objeto `printer`.

[!code-cpp[concrt-permute-strings#1](../../parallel/concrt/codesnippet/cpp/how-to-create-agents-that-use-specific-scheduler-policies_1.cpp)]

Este ejemplo produce el siguiente resultado:

```Output
With default scheduler:
Computing all permutations of 'Grapefruit'...
100% complete...

With higher context priority:
Computing all permutations of 'Grapefruit'...
100% complete...
```

Aunque ambos conjuntos de tareas generan el mismo resultado, la versión que usa la directiva personalizada permite que el objeto `printer` se ejecute con una prioridad elevada y, por tanto, con una mayor capacidad de respuesta.

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `permute-strings.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

> **cl. exe/EHsc permute-Strings. cpp**

## <a name="see-also"></a>Consulte también

[Directivas de Scheduler](../../parallel/concrt/scheduler-policies.md)<br/>
[Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)
