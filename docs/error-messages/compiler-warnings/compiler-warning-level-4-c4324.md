---
title: Advertencia del compilador (nivel 4) C4324
ms.date: 11/04/2016
f1_keywords:
- C4324
helpviewer_keywords:
- C4324
ms.assetid: 420fa929-d9c0-40b4-8808-2d8ad3ca8090
ms.openlocfilehash: 696f53dff6398555355ca3a58e25d2c6d64eaaab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508360"
---
# <a name="compiler-warning-level-4-c4324"></a>Advertencia del compilador (nivel 4) C4324

'nombre_de_estructura': se rellenó la estructura debido a __declspec(align())

Se agregó relleno al final de una estructura porque se ha especificado un [__declspec (Align)](../../cpp/align-cpp.md) valor.

Por ejemplo, el código siguiente genera C4324:

```
// C4324.cpp
// compile with: /W4
struct __declspec(align(32)) A
{
   char a;
};   // C4324

int main()
{
}
```