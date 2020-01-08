---
title: Error del compilador C3002
ms.date: 11/04/2016
f1_keywords:
- C3002
helpviewer_keywords:
- C3002
ms.assetid: 2d4241a7-c8eb-4d43-a128-dca255d137bc
ms.openlocfilehash: 677c88747198a2ac95a84e788a5fd16456b6372b
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302203"
---
# <a name="compiler-error-c3002"></a>Error del compilador C3002

'nombre1 nombre2': nombres de directiva de OpenMP múltiples

No se permite usar nombres de directiva múltiples.

El ejemplo siguiente genera la advertencia C3002:

```c
// C3002.c
// compile with: /openmp
int main()
{
   #pragma omp parallel single   // C3002
}
```
