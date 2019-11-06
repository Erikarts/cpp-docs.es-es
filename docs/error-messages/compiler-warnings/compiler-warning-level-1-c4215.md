---
title: ADVERTENCIA del compilador (nivel 1) C4215
ms.date: 11/04/2016
f1_keywords:
- C4215
helpviewer_keywords:
- C4215
ms.assetid: f2aab64d-1bab-4f75-95ee-89e1263047b1
ms.openlocfilehash: 91be04f927c63ccbb0668bbe70cbd7c5813f8dfc
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627344"
---
# <a name="compiler-warning-level-1-c4215"></a>ADVERTENCIA del compilador (nivel 1) C4215

se ha utilizado una extensión no estándar: Long Float

Las extensiones predeterminadas de Microsoft (/ZE) tratan **Long Float** como **Double**. La compatibilidad con ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) no. Utilice **Double** para mantener la compatibilidad.

En el ejemplo siguiente se genera C4215:

```cpp
// C4215.cpp
// compile with: /W1 /LD
long float a;   // C4215

// use the line below to resolve the warning
// double a;
```