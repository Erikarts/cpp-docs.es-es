---
title: Advertencia del compilador (nivel 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: b655dcfb456d32e45833e89e5a48926ad70d1d9e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588687"
---
# <a name="compiler-warning-level-4-c4565"></a>Advertencia del compilador (nivel 4) C4565

> '*función*': redefinición; el símbolo se declaró previamente con __declspec (*modificador*)

## <a name="remarks"></a>Comentarios

Volvió a definir o declarar de nuevo un símbolo y la segunda definición o declaración, a diferencia de la primera definición o declaración, no tenía un `__declspec` modificador (*modificador*). La advertencia es informativa. Para corregir esta advertencia, elimine una de las definiciones.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4565:

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```