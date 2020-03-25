---
title: Error del compilador C3286
ms.date: 11/04/2016
f1_keywords:
- C3286
helpviewer_keywords:
- C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
ms.openlocfilehash: 4c87e98f11a560d0d92be8ea7bc624edd4e09ad2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201401"
---
# <a name="compiler-error-c3286"></a>Error del compilador C3286

> '*especificador*': una variable de iteración no puede tener especificadores de clase de almacenamiento

No se puede especificar una clase de almacenamiento en una variable de iteración. Para obtener más información, vea [clases deC++almacenamiento ()](../../cpp/storage-classes-cpp.md) y [para cada una de ellas en](../../dotnet/for-each-in.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3286 y también se muestra el uso correcto.

```cpp
// C3286.cpp
// compile with: /clr
int main() {
   array<int> ^p = { 1, 2, 3 };
   for each (static int i in p) {}   // C3286
   for each (int j in p) {}   // OK
}
```
