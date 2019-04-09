---
title: Error del compilador C3154
ms.date: 11/04/2016
f1_keywords:
- C3154
helpviewer_keywords:
- C3154
ms.assetid: 78005c74-eaaf-4ac2-88ae-6c25d01a302a
ms.openlocfilehash: 9f7af4e19fab5f5a0539e9fc3bf9dbeffb5c6fbf
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781385"
---
# <a name="compiler-error-c3154"></a>Error del compilador C3154

Se esperaba ',' antes de puntos suspensivos. No coma separada por puntos suspensivos no compatible con funciones de matriz.

No se declaró correctamente una función de argumento variable.

Para obtener más información, consulte [listas de argumentos variables (...) (C++ / C++ / CLI) ](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3154.

```
// C3154.cpp
// compile with: /clr
ref struct R {
   void Func(int ... array<int> ^);   // C3154
   void Func2(int i, ... array<int> ^){}   // OK
   void Func3(array<int> ^){}   // OK
   void Func4(... array<int> ^){}   // OK
};

int main() {
   R ^ r = gcnew R;
   r->Func4(1,2,3);
}
```