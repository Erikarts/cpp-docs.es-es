---
title: Error del compilador C2177
ms.date: 11/04/2016
f1_keywords:
- C2177
helpviewer_keywords:
- C2177
ms.assetid: 2a39a880-cddb-4d3e-a572-645a14c4c478
ms.openlocfilehash: 9beb8454804401f8b39f9976fe62faf6e2659537
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174593"
---
# <a name="compiler-error-c2177"></a>Error del compilador C2177

constante demasiado grande

Un valor de constante es demasiado grande para el tipo de variable al que está asignado.

El ejemplo siguiente genera la advertencia C2177:

```
// C2177.cpp
int main() {
   int a=18446744073709551616;   // C2177
   int b=18446744073709551615;   // OK
}
```