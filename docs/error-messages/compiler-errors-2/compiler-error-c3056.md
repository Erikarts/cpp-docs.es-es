---
title: Error del compilador C3056
ms.date: 11/04/2016
f1_keywords:
- C3056
helpviewer_keywords:
- C3056
ms.assetid: 9500173d-870b-49b3-8e88-0ee93586d19a
ms.openlocfilehash: d33aa6679c6dc68b7f1a62e75aff6fadc65dc7bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62265612"
---
# <a name="compiler-error-c3056"></a>Error del compilador C3056

'símbolo': el símbolo no está en el mismo ámbito de la directiva 'threadprivate'

Un símbolo usado en una cláusula [threadprivate](../../parallel/openmp/reference/threadprivate.md) debe estar en el mismo ámbito que la cláusula `threadprivate` .

El ejemplo siguiente genera la advertencia C3056:

```
// C3056.cpp
// compile with: /openmp
int x, y;
void test() {
   #pragma omp threadprivate(x, y)   // C3056
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```

Posible resolución:

```
// C3056b.cpp
// compile with: /openmp /LD
int x, y;
#pragma omp threadprivate(x, y)
void test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```