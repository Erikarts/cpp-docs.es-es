---
title: Advertencia del compilador (nivel 4) C4816
ms.date: 11/04/2016
f1_keywords:
- C4816
helpviewer_keywords:
- C4816
ms.assetid: 60f730ae-d942-4db9-ab97-41d4a874d8da
ms.openlocfilehash: e96cb81d78b0e49e6978ff6ec78cdbfcfdc89e6d
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990064"
---
# <a name="compiler-warning-level-4-c4816"></a>Advertencia del compilador (nivel 4) C4816

'parámetro': el parámetro tiene una matriz de tamaño cero que se truncará (a menos que el objeto se pase por referencia)

Un parámetro para un objeto con una matriz de tamaño cero no se pasó por referencia. La matriz no se copiará cuando se pase el objeto.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4816:

```cpp
// C4816.cpp
// compile with: /W4
#include <stdio.h>

extern "C" int printf_s(const char *, ...);

#pragma warning(disable : 4200)

struct S1
{
    int i;
    char cArr[];
};

void TestErr(S1 s1)   // C4816 param with zero-array
                      // not passed by reference
{
    printf_s("%d %c %c\n", s1.i, s1.cArr[0], s1.cArr[1]);
}

void TestOk(S1 &s1)
{
    printf_s("%d %c %c\n", s1.i, s1.cArr[0], s1.cArr[1]);
}

int main()
{
    S1 myS_1 = { 6, 'a', 'b', 'c' };
    TestErr(myS_1);
    TestOk(myS_1);
}
```
