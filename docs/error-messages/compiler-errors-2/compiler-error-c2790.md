---
title: Error del compilador C2790
ms.date: 11/04/2016
f1_keywords:
- C2790
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
ms.openlocfilehash: e377c18b5c0774a466dc535f2a1fba3411bd15b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530252"
---
# <a name="compiler-error-c2790"></a>Error del compilador C2790

'super': esta palabra clave solo puede usarse dentro del cuerpo de función miembro de clase

Este mensaje de error aparece si el usuario intenta utilizar la palabra clave [super](../../cpp/super.md) fuera del contexto de una función miembro.

El ejemplo siguiente genera C2790:

```
// C2790.cpp
void f() {
   __super::g();   // C2790
}
```