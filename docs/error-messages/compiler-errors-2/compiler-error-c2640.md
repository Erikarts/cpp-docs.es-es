---
title: Error del compilador C2640
ms.date: 11/04/2016
f1_keywords:
- C2640
helpviewer_keywords:
- C2640
ms.assetid: e4d137ab-ed1d-457c-9eec-b70d97f1b0b4
ms.openlocfilehash: d0dc2dd514186a94811b816c5f3f470a057186f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436249"
---
# <a name="compiler-error-c2640"></a>Error del compilador C2640

'identifier': __based no es válido modificador para referencia

El `__based` modificador se puede utilizar en punteros solo.

El ejemplo siguiente genera C2640:

```
// C2640.cpp
void f(int i) {
    void *vp;
    int _based(vp) &vr = I;  // C2640
}
```