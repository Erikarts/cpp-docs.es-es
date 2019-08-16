---
title: Advertencia del compilador (nivel 1) C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: 28b3e49717993a3bf20c8cfec5938d698266c0f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406540"
---
# <a name="compiler-warning-level-1-c4804"></a>Advertencia del compilador (nivel 1) C4804

'operación': uso no seguro del tipo 'bool' en la operación

Esta advertencia es para cuando usa un `bool` variable o un valor de forma inesperada. Por ejemplo, se genera C4804 si usa operadores como el operador unario negativo (**-**) o el operador de complemento (`~`). El compilador evalúa la expresión.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4804:

```
// C4804.cpp
// compile with: /W1

int main()
{
   bool i = true;
   if (-i)   // C4804, remove the '-' to resolve
   {
      i = false;
   }
}
```