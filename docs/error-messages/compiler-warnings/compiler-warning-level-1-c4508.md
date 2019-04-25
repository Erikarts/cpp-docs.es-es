---
title: Advertencia del compilador (nivel 1) C4508
ms.date: 11/04/2016
f1_keywords:
- C4508
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
ms.openlocfilehash: c96db3d4bd1124c96b22363531b7739d0757b613
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160814"
---
# <a name="compiler-warning-level-1-c4508"></a>Advertencia del compilador (nivel 1) C4508

'function': función debe devolver un valor; 'void' tipo de valor devuelto asumido

La función no tiene especificado ningún tipo de valor devuelto. En este caso, también se desencadena C4430 y el compilador implementa la corrección indicada por C4430 (valor predeterminado es de tipo int).

Para resolver esta advertencia, debe declarar explícitamente el tipo de valor devuelto de funciones.

El ejemplo siguiente genera C4508:

```
// C4508.cpp
// compile with: /W1 /c
#pragma warning (disable : 4430)
func() {}   // C4508
void func2() {}   // OK
```