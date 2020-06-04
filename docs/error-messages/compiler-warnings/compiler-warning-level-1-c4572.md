---
title: Advertencia del compilador (nivel 1) C4572
ms.date: 11/04/2016
f1_keywords:
- C4572
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
ms.openlocfilehash: 4a1931032f6d1f8db0679dd782ff2f0ce7ff428c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162210"
---
# <a name="compiler-warning-level-1-c4572"></a>Advertencia del compilador (nivel 1) C4572

El atributo [ParamArray] está en desuso en/CLR, use '... ' en lugar

Se usó un estilo obsoleto para especificar una lista de argumentos de variable. Al compilar para CLR, use la sintaxis de puntos suspensivos en lugar de <xref:System.ParamArrayAttribute>. Para obtener más información, vea [listas de argumentos variables (...C++) (/CLI)](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4572.

```cpp
// C4572.cpp
// compile with: /clr /W1
void Func([System::ParamArray] array<int> ^);   // C4572
void Func2(... array<int> ^){}   // OK

int main() {
   Func2(1, 2, 3);
}
```
