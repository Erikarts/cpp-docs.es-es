---
title: Error del compilador C2790
ms.date: 11/04/2016
f1_keywords:
- C2790
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
ms.openlocfilehash: c63fe7bb3686692818337e890de7fe4c80a18158
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739563"
---
# <a name="compiler-error-c2790"></a>Error del compilador C2790

' Super ': esta palabra clave solo se puede usar dentro del cuerpo de la función miembro de clase

Este mensaje de error aparece si el usuario intenta usar la palabra clave [Super](../../cpp/super.md) fuera del contexto de una función miembro.

En el ejemplo siguiente se genera C2790:

```cpp
// C2790.cpp
void f() {
   __super::g();   // C2790
}
```
