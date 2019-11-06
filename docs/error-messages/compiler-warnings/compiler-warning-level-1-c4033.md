---
title: Advertencia del compilador (nivel 1) C4033
ms.date: 11/04/2016
f1_keywords:
- C4033
helpviewer_keywords:
- C4033
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
ms.openlocfilehash: 740be5fa45d0cd332cc7ac6b62a983ce00d05a8f
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623733"
---
# <a name="compiler-warning-level-1-c4033"></a>Advertencia del compilador (nivel 1) C4033

'function': la función debe devolver un valor

Esta función no devuelve ningún valor. Se devolvió un valor indefinido.

Las funciones que usan `return` sin un valor devuelto debe declararse como tipo `void`.

Este error corresponde al código de lenguaje C.

El ejemplo siguiente genera la advertencia C4033:

```c
// C4033.c
// compile with: /W1 /LD
int test_1(int x)   // C4033 expected
{
   if (x)
   {
      return;   // C4033
   }
}
```