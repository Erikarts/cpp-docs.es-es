---
title: Error del compilador C2675
ms.date: 11/04/2016
f1_keywords:
- C2675
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
ms.openlocfilehash: aea79509d0e1ae5c31fcf0cf369c28af39a21154
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367933"
---
# <a name="compiler-error-c2675"></a>Error del compilador C2675

'operador' unario: 'tipo' no define este operador o una conversión a un tipo aceptable para el operador predefinido

C2675 también puede producirse al usar un operador unario y el tipo no define el operador o una conversión a un tipo aceptable para el operador predefinido. Para usar este operador, debe sobrecargarlo para el tipo especificado o definir una conversión a un tipo para el que esté definido el operador.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2675.

```
// C2675.cpp
struct C {
   C(){}
} c;

struct D {
   D(){}
   void operator-(){}
} d;

int main() {
   -c;   // C2675
   -d;   // OK
}
```