---
title: Error del compilador C2694
ms.date: 11/04/2016
f1_keywords:
- C2694
helpviewer_keywords:
- C2694
ms.assetid: 8dc2cec2-67ae-4e16-8c0c-374425aca8bc
ms.openlocfilehash: 4897512f6bd27465b7281d7a27757918128202d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367751"
---
# <a name="compiler-error-c2694"></a>Error del compilador C2694

'override': función virtual de invalidación tiene especificación de excepción menos restrictiva que la clase base virtual miembro función 'base'

Se ha reemplazado una función virtual, pero en [/Za](../../build/reference/za-ze-disable-language-extensions.md), el reemplazo de la función tenía menos restrictivo [especificación de excepción](../../cpp/exception-specifications-throw-cpp.md).

El ejemplo siguiente genera C2694:

```
// C2694.cpp
// compile with: /Za /c
class MyBase {
public:
   virtual void f(void) throw(int) {
   }
};

class Derived : public MyBase {
public:
   void f(void) throw(...) {}   // C2694
   void f2(void) throw(int) {}   // OK
};
```