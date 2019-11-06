---
title: Advertencia del compilador (nivel 1) C4085
ms.date: 11/04/2016
f1_keywords:
- C4085
helpviewer_keywords:
- C4085
ms.assetid: 2bc6eb25-058f-4597-b351-fd69587b5170
ms.openlocfilehash: bf006a2e566fe79b44f71192e95278392fe4f59e
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626862"
---
# <a name="compiler-warning-level-1-c4085"></a>Advertencia del compilador (nivel 1) C4085

se esperaba que el parámetro de tipo pragma fuera 'on' u 'off'

El pragma requiere un **on** u **off** . La función pragma se ignorará.

El ejemplo siguiente genera la advertencia C4085:

```cpp
// C4085.cpp
// compile with: /W1 /LD
#pragma optimize( "t", maybe )  // C4085
```