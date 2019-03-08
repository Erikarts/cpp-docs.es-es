---
title: Llamada de función (C)
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
ms.openlocfilehash: d22bdebc8fa832afb14a2cc09e6a441b7b9e8a5a
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147417"
---
# <a name="function-call-c"></a>Llamada de función (C)

Una *llamada a función* es una expresión que incluye el nombre de la función que se llama o el valor de un puntero a función y, opcionalmente, los argumentos que se pasan a la función.

## <a name="syntax"></a>Sintaxis

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **(**  *argument-expression-list*<sub>opt</sub> **)**

*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list* **,** *assignment-expression*

El elemento *postfix-expression* se debe evaluar como una dirección de función (por ejemplo, un identificador de función o el valor de un puntero de función) y el elemento *argument-expression-list* es una lista de expresiones (separadas por comas) cuyos valores (los "argumentos") se pasan a la función. El elemento *argument-expression-list* puede estar vacío.

Una expresión de llamada a función tiene el valor y el tipo del valor devuelto de la función. Una función no puede devolver un objeto de tipo de matriz. Si el tipo de valor devuelto de la función es `void` (es decir, la función nunca se ha declarado para devolver un valor), la expresión de llamada a función también tiene el tipo `void`. (Vea [Llamadas a función](../c-language/function-calls.md) para obtener más información).

## <a name="see-also"></a>Vea también

[Operador de llamada de función: ()](../cpp/function-call-operator-parens.md)
