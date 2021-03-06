---
title: Error del compilador C3768
ms.date: 11/04/2016
f1_keywords:
- C3768
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
ms.openlocfilehash: e9c385fd178dc967e72f5e0ca7fab27b28ad962f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676752"
---
# <a name="compiler-error-c3768"></a>Error del compilador C3768

> no se puede adquirir la dirección de una función vararg virtual en código administrado puro

## <a name="remarks"></a>Comentarios

El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

Cuando se compila con **/CLR: pure**, no puede tomar la dirección de una memoria virtual `vararg` función.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3768:

```cpp
// C3768.cpp
// compile with: /clr:pure
struct A
{
   virtual void f(...);
};

int main()
{
   &(A::f);   // C3768
}
```