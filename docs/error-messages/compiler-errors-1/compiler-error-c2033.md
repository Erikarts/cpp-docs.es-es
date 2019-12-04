---
title: Error del compilador C2033
ms.date: 11/04/2016
f1_keywords:
- C2033
helpviewer_keywords:
- C2033
ms.assetid: fd5a1637-9db2-4c98-a7cc-b63b39737cd9
ms.openlocfilehash: 6fec222117f28e885d6187e6733559433f4943d3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750967"
---
# <a name="compiler-error-c2033"></a>Error del compilador C2033

'identificador': el campo de bits no puede tener direccionamiento indirecto.

El campo de bits se declaró como un puntero, lo cual no está permitido.

El ejemplo siguiente genera la advertencia C2033:

```cpp
// C2033.cpp
struct S {
   int *b : 1;  // C2033
};
```

Solución posible:

```cpp
// C2033b.cpp
// compile with: /c
struct S {
   int b : 1;
};
```
