---
title: Advertencia del compilador (nivel 4) C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: afb4fb493c7c3e34ca691720a30d74517b0ab5b7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661414"
---
# <a name="compiler-warning-level-4-c4559"></a>Advertencia del compilador (nivel 4) C4559

> '*función*': redefinición; el __declspec ganancias de función (*modificador*)

## <a name="remarks"></a>Comentarios

Una función volvió a definir o declarar de nuevo y la segunda definición o declaración agrega un **__declspec** modificador (*modificador*). La advertencia es informativa. Para corregir esta advertencia, elimine una de las definiciones.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4559:

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```