---
title: Error del compilador C3736
ms.date: 11/04/2016
f1_keywords:
- C3736
helpviewer_keywords:
- C3736
ms.assetid: 579b773c-41e7-40ea-8382-2e3ce2667f4c
ms.openlocfilehash: e31d68a13ebd9c5267fd285d43ebc66ae8b53182
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328021"
---
# <a name="compiler-error-c3736"></a>Error del compilador C3736

'evento': debe ser un método o, en el caso de eventos administrados, opcionalmente, un miembro de datos

Nativos y eventos COM deben ser métodos. Los eventos de .NET también pueden ser miembros de datos.

El ejemplo siguiente genera C3736:

```
// C3736.cpp
struct A {
   __event int e();
};

struct B {
   int f;   // C3736
   // The following line resolves the error.
   // int f();
   B(A* a) {
      __hook(&A::e, a, &B::f);
   }
};

int main() {
}
```