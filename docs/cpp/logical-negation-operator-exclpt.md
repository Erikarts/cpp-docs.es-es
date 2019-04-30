---
title: 'Operador lógico de negación: !'
ms.date: 08/27/2018
f1_keywords:
- '!'
- Not
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
ms.openlocfilehash: 7b37e5108ca01d782c13508c0cd7a96b096cd745
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62216413"
---
# <a name="logical-negation-operator-"></a>Operador lógico de negación: !

## <a name="syntax"></a>Sintaxis

```
! cast-expression
```

## <a name="remarks"></a>Comentarios

El operador lógico de negación (**!**) invierte el significado del operando. El operando debe ser de tipo aritmético o de puntero (o una expresión que se evalúe como un tipo aritmético o de puntero). El operando se convierte implícitamente al tipo **bool**. El resultado es TRUE si el operando convertido es FALSE. el resultado es FALSE si el operando convertido es TRUE. El resultado es de tipo **bool**.

Para una expresión *e*, la expresión unaria `!e` es equivalente a la expresión `(e == 0)`, excepto donde intervienen operadores sobrecargados.

## <a name="operator-keyword-for-"></a>Palabra clave del operador para !

El **no** operador es un término alternativo de **!**. Hay dos maneras de acceder a la **no** operador en los programas: incluir el archivo de encabezado \<iso646.h >, o compilar con la [/Za](../build/reference/za-ze-disable-language-extensions.md) opción del compilador (deshabilitar extensiones de lenguaje).

## <a name="example"></a>Ejemplo

```cpp
// expre_Logical_NOT_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    if (!i)
        cout << "i is zero" << endl;
}
```

## <a name="see-also"></a>Vea también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores aritméticos unarios](../c-language/unary-arithmetic-operators.md)<br/>
