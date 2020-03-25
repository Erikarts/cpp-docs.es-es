---
title: ADVERTENCIA del compilador (nivel 1) C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: 551309757f5e76e230d0a275da94ac94ec30fb13
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163928"
---
# <a name="compiler-warning-level-1-c4090"></a>ADVERTENCIA del compilador (nivel 1) C4090

' Operation ': distintos calificadores ' Modifier '

Una variable que se usa en una operación se define con un modificador especificado que impide que el compilador modifique sin detección. La expresión se compila sin modificarla.

Esta advertencia puede deberse a que un puntero a un elemento **const** o `volatile` se asigna a un puntero no declarado como que apunta a **const** o `volatile`.

Esta advertencia se emite para programas de C. En un C++ programa, el compilador emite un error: [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).

En el ejemplo siguiente se genera C4090:

```c
// C4090.c
// compile with: /W1
int *volatile *p;
int *const *q;
int **r;

int main() {
   p = q;   // C4090
   p = r;
   q = p;   // C4090
   q = r;
   r = p;   // C4090
   r = q;   // C4090
}
```
