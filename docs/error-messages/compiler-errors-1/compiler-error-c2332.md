---
title: Error del compilador C2332
ms.date: 11/04/2016
f1_keywords:
- C2332
helpviewer_keywords:
- C2332
ms.assetid: fb05cd68-e271-4bea-9fb7-ef4edb0a26ac
ms.openlocfilehash: c9b8fe3665199e4a502de965fd1e592252e97bf2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300867"
---
# <a name="compiler-error-c2332"></a>Error del compilador C2332

'definición de tipo': falta el nombre de etiqueta

El compilador encontró una definición de tipo incompletas.

El ejemplo siguiente genera el error C2332:

```
// C2332.cpp
// compile with: /c
struct S {
   int i;
};

typedef struct * pS;   // C2332
typedef struct S* pS;   // OK

int get_S_i(pS p) {
   return p->i;
}
```