---
title: Advertencia del compilador (nivel 1) C4602
ms.date: 11/04/2016
f1_keywords:
- C4602
helpviewer_keywords:
- C4602
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
ms.openlocfilehash: c719ae23ed3799debf2db9c8f2d82b3c49db3156
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406462"
---
# <a name="compiler-warning-level-1-c4602"></a>Advertencia del compilador (nivel 1) C4602

\#pragma pop_macro: 'macro name' ninguna #pragma push_macro anterior para este identificador

Si usa [pop_macro](../../preprocessor/pop-macro.md) para una macro concreta, primero debe haber pasado ese nombre de macro a [push_macro](../../preprocessor/push-macro.md). Por ejemplo, El ejemplo siguiente genera el error C4602:

```
// C4602.cpp
// compile with: /W1
int main()
{
   #pragma pop_macro("x")   // C4602 x is not on the stack
}
```