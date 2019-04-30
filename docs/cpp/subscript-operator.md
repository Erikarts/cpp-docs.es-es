---
title: Operador de subíndice]
ms.date: 11/04/2016
f1_keywords:
- '[]'
helpviewer_keywords:
- operators [C++], subscript
- postfix operators [C++]
- '[] operator'
- subscript operator [C++], syntax
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
ms.openlocfilehash: 2d55c18d2c9faa1a704bea129f2551937e76133c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266899"
---
# <a name="subscript-operator-"></a>Operador de subíndice]

## <a name="syntax"></a>Sintaxis

```
postfix-expression [ expression ]
```

## <a name="remarks"></a>Comentarios

Una expresión de postfijo (que también se puede ser una expresión primaria) seguida del operador de subíndice, **[]**, especifica la indexación de matrices.

Para obtener información sobre las matrices administradas en C++ / c++ / CLI, consulte [matrices](../extensions/arrays-cpp-component-extensions.md).

Normalmente, el valor representado por *postfix-expression* es un valor de puntero, como un identificador de matriz y *expresión* es un valor entero (incluidos los tipos enumerados). Sin embargo, todo lo que se necesita desde el punto de vista sintáctico es que una de las expresiones sea de tipo puntero y que la otra sea de tipo entero. Por tanto, el valor entero podría estar en el *postfix-expression* posición y el valor de puntero podría estar en los corchetes en la *expresión* o posición de subíndice. Observe el fragmento de código siguiente:

```cpp
int nArray[5] = { 0, 1, 2, 3, 4 };
cout << nArray[2] << endl;            // prints "2"
cout << 2[nArray] << endl;            // prints "2"
```

En el ejemplo anterior, la expresión `nArray[2]` es idéntica a `2[nArray]`. El motivo es que el resultado de una expresión de subíndice `e1[e2]` viene dado por:

`*((e2) + (e1))`

La dirección producida por la expresión no es *e2* bytes desde la dirección *e1*. En su lugar, la dirección se ha ampliado para producir el siguiente objeto de la matriz *e2*. Por ejemplo:

```cpp
double aDbl[2];
```

Las direcciones de `aDb[0]` y `aDb[1]` están alejadas 8 bytes, el tamaño de un objeto de tipo **doble**. Esta ampliación según el tipo de objeto se realiza automáticamente en el lenguaje C++ y se define en [operadores aditivos](../cpp/additive-operators-plus-and.md) donde se describe la suma y resta de operandos de tipo de puntero.

Una expresión de subíndice también puede tener varios subíndices, como se indica a continuación:

*expression1* **[** *expression2* **] [** *expression3* **]** ...

Las expresiones de subíndice se asocian de izquierda a derecha. La expresión de subíndice del extremo izquierdo, *expression1* **[** *expression2* **]**, se evalúa primero. La dirección resultante de agregar *expression1* y *expression2* forma una expresión de puntero; entonces, se agrega *expression3* a esta expresión de puntero para formar una nueva expresión de puntero, y así sucesivamente, hasta que se haya agregado la última expresión de subíndice. El operador de direccionamiento indirecto (<strong>\*</strong>) se aplica después de evaluar la última expresión subíndice, a menos que el valor del puntero final trata de un tipo de matriz.

Las expresiones con varios subíndices hacen referencia a elementos de matrices multidimensionales. Una matriz multidimensional es una matriz cuyos elementos son matrices. Por ejemplo, el primer elemento de una matriz tridimensional es una matriz con dos dimensiones. En el ejemplo siguiente se declara y se inicializa una matriz bidimensional de caracteres simple:

```cpp
// expre_Subscript_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
#define MAX_ROWS 2
#define MAX_COLS 2

int main() {
  char c[ MAX_ROWS ][ MAX_COLS ] = { { 'a', 'b' }, { 'c', 'd' } };
  for ( int i = 0; i < MAX_ROWS; i++ )
     for ( int j = 0; j < MAX_COLS; j++ )
        cout << c[ i ][ j ] << endl;
}
```

## <a name="positive-and-negative-subscripts"></a>Subíndices positivos y negativos

El primer elemento de una matriz es el elemento 0. El intervalo de un C++ proviene de la matriz *matriz*[0] a *matriz*[*tamaño* - 1]. Sin embargo, C++ admite subíndices positivos y negativos. Los subíndices negativos deben situarse dentro de los límites de la matriz, ya que de lo contrario los resultados son impredecibles. En el código siguiente se muestran subíndices de matriz positivos y negativos:

```cpp
#include <iostream>
using namespace std;

int main() {
    int intArray[1024];
    for (int i = 0, j = 0; i < 1024; i++)
    {
        intArray[i] = j++;
    }

    cout << intArray[512] << endl;   // 512

    cout << 257[intArray] << endl;   // 257

    int *midArray = &intArray[512];  // pointer to the middle of the array

    cout << midArray[-256] << endl;  // 256

    cout << intArray[-256] << endl;  // unpredictable, may crash
}
```

El subíndice negativo de la última línea puede producir un error en tiempo de ejecución porque señala a una dirección 256 **int** posiciones inferior en la memoria que el origen de la matriz. El puntero `midArray` se inicializa en el centro de `intArray`; por lo tanto, es posible (aunque peligroso) usar ambos índices de matriz positivos y negativos en él. Los errores de subíndice de matriz no generan errores en tiempo de compilación, pero producen resultados imprevisibles.

El operador de subíndice es conmutativo. Por lo tanto, las expresiones *matriz*[*índice*] y *índice*[*matriz*] se garantiza que sean equivalentes siempre que el subíndice operador no esté sobrecargado (vea [operadores sobrecargados](../cpp/operator-overloading.md)). La primera forma es la práctica más común de codificación, pero cualquiera de ellas funciona.

## <a name="see-also"></a>Vea también

[Expresiones postfijas](../cpp/postfix-expressions.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Matrices](../cpp/arrays-cpp.md)<br/>
[Matrices unidimensionales](../c-language/one-dimensional-arrays.md)<br/>
[Matrices multidimensionales](../c-language/multidimensional-arrays-c.md)<br/>
