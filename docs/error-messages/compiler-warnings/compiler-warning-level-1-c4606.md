---
title: Advertencia del compilador (nivel 1) C4606
ms.date: 11/04/2016
f1_keywords:
- C4606
helpviewer_keywords:
- C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
ms.openlocfilehash: e471ca3e478d1166b150e49bf25efa4b9d5803cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402520"
---
# <a name="compiler-warning-level-1-c4606"></a>Advertencia del compilador (nivel 1) C4606

\#advertencia pragma: 'advertencia_número'; Advertencias de análisis de código no están asociadas con niveles de advertencia

Para las advertencias de análisis de código, solo `error`, `once`, y `default` son compatibles con el [advertencia](../../preprocessor/warning.md) pragma.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4606.

```
// C4606.cpp
// compile with: /c /W1
#pragma warning(1: 6001)   // C4606
#pragma warning(once: 6001)   // OK
```