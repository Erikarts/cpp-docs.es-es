---
title: Error del compilador C2724
ms.date: 11/04/2016
f1_keywords:
- C2724
helpviewer_keywords:
- C2724
ms.assetid: 4e4664bc-8c96-4156-b79f-03436f532ea8
ms.openlocfilehash: f48bf45eeed491469b161ac1edcdb57d04eb5863
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760691"
---
# <a name="compiler-error-c2724"></a>Error del compilador C2724

' Identifier ': ' Static ' no se debe usar en funciones miembro definidas en el ámbito de archivo

Las funciones miembro estáticas se deben declarar con vinculación externa.

En el ejemplo siguiente se genera C2724:

```cpp
// C2724.cpp
class C {
   static void func();
};

static void C::func(){};   // C2724
// try the following line instead
// void C::func(){};
```
