---
title: Error irrecuperable C1310
ms.date: 11/04/2016
f1_keywords:
- C1310
helpviewer_keywords:
- C1310
ms.assetid: ac48aa51-8023-42fe-b844-3f8bf228fbef
ms.openlocfilehash: 1b0fca9a5e453fd354a4efc6960a54386795ccf6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266433"
---
# <a name="fatal-error-c1310"></a>Error irrecuperable C1310

las optimizaciones guiadas por perfiles no están disponibles con OpenMP

No podrá vincular con [/LTCG: PGI](../../build/reference/ltcg-link-time-code-generation.md) ningún módulo compilado con [/GL](../../build/reference/gl-whole-program-optimization.md).

El ejemplo siguiente genera la advertencia C1310:

```
// C1310.cpp
// compile with: /openmp /GL /link /LTCG:PGI
// C1310 expected
int main()
{
   int i = 0, j = 10;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i < 0; i++)
         --j;
   }
}
```