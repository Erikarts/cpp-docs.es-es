---
title: Error del compilador C2117
ms.date: 11/04/2016
f1_keywords:
- C2117
helpviewer_keywords:
- C2117
ms.assetid: b947379d-5861-42fc-ac26-170318579cbd
ms.openlocfilehash: 2f6a1e26972f093e50c5e655935f750195ab7d3b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338576"
---
# <a name="compiler-error-c2117"></a>Error del compilador C2117

'identifier': desbordamiento de límites de matriz

Una matriz tiene demasiados inicializadores:

- Inicializadores y elementos de la matriz no coinciden en tamaño y cantidad.

- No hay espacio para el terminador nulo en una cadena.

El ejemplo siguiente genera C2117:

```
// C2117.cpp
int main() {
   char abc[4] = "abcd";   // C2117
   char def[4] = "abd";   // OK
}
```