---
title: Error del compilador C2118
ms.date: 11/04/2016
f1_keywords:
- C2118
helpviewer_keywords:
- C2118
ms.assetid: bf4315d0-f085-4323-b813-96ee61a13bde
ms.openlocfilehash: 71b8273aaee52420f8a9c9c2dd2d015bea72ddf6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338914"
---
# <a name="compiler-error-c2118"></a>Error del compilador C2118

subíndice negativo

El valor que define el tamaño de la matriz es menor que cero o mayor que el tamaño máximo de la matriz.

El ejemplo siguiente genera C2118:

```
// C2118.cpp
int main() {
   int array1[-1];   // C2118
   int array2[3];   // OK
}
```