---
title: Advertencia del compilador (nivel 1) C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 98ea72bef0cb95163604144c1069a13c3b27d81c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616260"
---
# <a name="compiler-warning-level-1-c4630"></a>Advertencia del compilador (nivel 1) C4630

'símbolo': especificador de clase de almacenamiento 'extern' no es válido en la definición de miembro

Un miembro de datos o la función miembro se define como `extern`. Los miembros no pueden ser externos, aunque pueden objetos completos. El compilador omite la `extern` palabra clave. El ejemplo siguiente genera C4630:

```
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```