---
title: Puntos de secuencia de C
ms.date: 11/04/2016
helpviewer_keywords:
- sequence points
ms.assetid: c84885a5-4336-4eba-a643-058df4249903
ms.openlocfilehash: 13d6044269f60dc426a8b0b9b03463f387dfaa10
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152643"
---
# <a name="c-sequence-points"></a>Puntos de secuencia de C

Entre "puntos de secuencia" consecutivos, una expresión solo puede modificar una vez el valor de un objeto. El lenguaje C define los puntos de secuencia siguientes:

- Operando izquierdo del operador AND lógico (**&&**). El operando izquierdo del operador AND lógico se evalúa totalmente y todos los efectos secundarios se completan antes de continuar. Si el operando izquierdo se evalúa como false (0), el otro operando no se evalúa.

- Operando izquierdo del operador OR lógico (`||`). El operando izquierdo del operador OR lógico se evalúa totalmente y todos los efectos secundarios se completan antes de continuar. Si el operando izquierdo se evalúa como true (distinto de cero), el otro operando no se evalúa.

- Operando izquierdo del operador de coma. El operando izquierdo del operador de coma se evalúa totalmente y todos los efectos secundarios se completan antes de continuar. Los dos operandos del operador de coma se evalúan siempre. Observe que el operador de coma en una llamada de función no garantiza un orden de evaluación.

- Operador de llamada de función. Todos los argumentos de una función se evalúan y todos los efectos secundarios se completan antes de la entrada a la función. No se especifica ningún orden de evaluación entre los argumentos.

- Primer operando del operador condicional. El primer operando del operador condicional se evalúa totalmente y todos los efectos secundarios se completan antes de continuar.

- El final de una expresión completa de inicialización (es decir, una expresión que no forma parte de otra expresión tal como el final de una inicialización en una instrucción de declaración).

- La expresión de una instrucción de expresión. Las instrucciones de expresión constan de una expresión opcional seguida de un punto y coma (**;**). La expresión se evalúa para sus efectos secundarios y hay un punto de secuencia después de esta evaluación.

- La expresión de control de una instrucción de selección (**if** o `switch`). La expresión se evalúa completamente y todos los efectos secundarios se completan antes de que se ejecute el código dependiente de la selección.

- La expresión de control de una instrucción `while` o **do**. La expresión se evalúa completamente y todos los efectos secundarios se completan antes de que se ejecute ninguna instrucción de la siguiente iteración del bucle `while` o **do**.

- Cada una de las tres expresiones de una instrucción **for**. Las expresiones se evalúan completamente y todos los efectos secundarios se completan antes de que se ejecute ninguna instrucción de la siguiente iteración del bucle **for**.

- La expresión en una instrucción `return`. La expresión se evalúa completamente y todos los efectos secundarios se completan antes de devolver el control a la función de llamada.

## <a name="see-also"></a>Vea también

[Evaluación de expresiones](../c-language/expression-evaluation-c.md)
