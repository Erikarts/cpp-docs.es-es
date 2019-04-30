---
title: Operadores de acceso a miembro:. y -&gt;
ms.date: 11/04/2016
f1_keywords:
- .
- ->
helpviewer_keywords:
- member access, expressions
- operators [C++], member access
- dot operator (.)
- -> operator
- member access, operators
- postfix operators [C++]
- . operator
- member access
ms.assetid: f8fc3df9-d728-40c5-b384-276927f5f1b3
ms.openlocfilehash: 0f370aa04af2e78efd5edfb7836fb71a4c4516a7
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345981"
---
# <a name="member-access-operators--and--gt"></a>Operadores de acceso a miembro:. y -&gt;

## <a name="syntax"></a>Sintaxis

```
postfix-expression . name
postfix-expression -> name
```

## <a name="remarks"></a>Comentarios

Los operadores de acceso de miembro **.** y **->** se usan para hacer referencia a los miembros de estructuras, uniones y clases. Las expresiones de acceso a miembros tienen el valor y el tipo del miembro seleccionado.

Hay dos formas de expresiones de acceso de miembro:

1. En la primera forma, *postfix-expression* representa un valor de tipo de unión, clase o struct y *nombre* nombra un miembro de la estructura especificada, unión o clase. El valor de la operación es de *nombre* y es un valor l si *postfix-expression* es un valor l.

1. En la segunda forma, *postfix-expression* representa un puntero a una estructura, unión o clase, y *nombre* nombra un miembro de la estructura especificada, unión o clase. El valor es el de *nombre* y es un valor l. El **->** operador de desreferencia el puntero. Por lo tanto, las expresiones `e->member` y `(*e).member` (donde *e* representa un puntero) producen resultados idénticos (excepto cuando los operadores **->** o <strong>\*</strong> están sobrecargados).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran dos formas del operador de acceso a miembros.

```cpp
// expre_Selection_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct Date {
   Date(int i, int j, int k) : day(i), month(j), year(k){}
   int month;
   int day;
   int year;
};

int main() {
   Date mydate(1,1,1900);
   mydate.month = 2;
   cout  << mydate.month << "/" << mydate.day
         << "/" << mydate.year << endl;

   Date *mydate2 = new Date(1,1,2000);
   mydate2->month = 2;
   cout  << mydate2->month << "/" << mydate2->day
         << "/" << mydate2->year << endl;
   delete mydate2;
}
```

```Output
2/1/1900
2/1/2000
```

## <a name="see-also"></a>Vea también

[Expresiones postfijas](../cpp/postfix-expressions.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Clases y structs](../cpp/classes-and-structs-cpp.md)<br/>
[Miembros de estructura y de unión](../c-language/structure-and-union-members.md)