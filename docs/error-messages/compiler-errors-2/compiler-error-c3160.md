---
title: Error del compilador C3160
ms.date: 11/04/2016
f1_keywords:
- C3160
helpviewer_keywords:
- C3160
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
ms.openlocfilehash: 96fd97aa5021b7e1bc5226162f9c54ff4d6211b1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175232"
---
# <a name="compiler-error-c3160"></a>Error del compilador C3160

'pointer': un miembro de datos de una clase administrada o WinRT no puede ser de este tipo

Los punteros interiores de recolección de elementos no utilizados pueden apuntar al interior de una clase administrada o WinRT. Ya que son más lentos que los punteros de objetos completos y requieren un tratamiento especial por parte del recolector de elementos no utilizados, no puede declarar punteros interiores administrados como miembros de una clase.

El ejemplo siguiente genera el error C3160:

```
// C3160.cpp
// compile with: /clr
ref struct A {
   // cannot create interior pointers inside a class
   interior_ptr<int> pg;   // C3160
   int g;   // OK
   int* pg2;   // OK
};

int main() {
   interior_ptr<int> pg2;   // OK
}
```
