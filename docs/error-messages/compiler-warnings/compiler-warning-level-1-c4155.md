---
title: Advertencia del compilador (nivel 1) C4155
ms.date: 11/04/2016
f1_keywords:
- C4155
helpviewer_keywords:
- C4155
ms.assetid: ba233353-09e3-4195-8127-13a27ddd8d70
ms.openlocfilehash: 9359012d7782e9f8eb9054cbcc7fa3d53b3c6697
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624962"
---
# <a name="compiler-warning-level-1-c4155"></a>Advertencia del compilador (nivel 1) C4155

eliminación de expresión de matriz sin utilizar el formato de matriz de 'delete'

El formato de matriz **delete** debe usarse para eliminar una matriz. Esta advertencia se produce solo si existe compatibilidad con ANSI (/Za).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4155:

```cpp
// C4155.cpp
// compile with: /Za /W1
#include <stdio.h>

int main(void)
{
    int (*array)[ 10 ] = new int[ 5 ] [ 10 ];
    array[0][0] = 8;

    printf_s("%d\n", array[0][0]);

   delete array;   // C4155
    // try the following line instead
    // delete [] array;   // C4155
}
```