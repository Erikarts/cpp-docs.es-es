---
title: Error del compilador C2055
ms.date: 11/04/2016
f1_keywords:
- C2055
helpviewer_keywords:
- C2055
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
ms.openlocfilehash: 9cb6e4d5891c5aefc9d66e7d70a5cd7685ccd393
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302047"
---
# <a name="compiler-error-c2055"></a>Error del compilador C2055

se esperaba una lista de parámetros formales, no una lista de tipos

Una definición de función contiene una lista de tipos de parámetros en lugar de una lista de parámetros formales. ANSI C requiere que se llame a los parámetros formales a menos que sean nulos o puntos suspensivos (`...`).

En el ejemplo siguiente se genera C2055:

```c
// C2055.c
// compile with: /c
void func(int, char) {}  // C2055
void func (int i, char c) {}   // OK
```
