---
title: 'Operadores de adición: + y -'
ms.date: 11/04/2016
f1_keywords:
- +
- '-'
helpviewer_keywords:
- operators [C++], addition
- subtraction operator [C++], additive operators
- + operator [C++], additive operators
- additive operators [C++]
- arithmetic operators [C++], additive operators
- '- operator [C++], additive operators in C++'
ms.assetid: d4afafe7-e201-4c69-a649-37f17756e784
ms.openlocfilehash: be9e1830ea44223aa46ad9a7f5c6cee6734fa9e6
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330377"
---
# <a name="additive-operators--and--"></a>Operadores de adición: + y -

## <a name="syntax"></a>Sintaxis

```
expression + expression
expression - expression
```

## <a name="remarks"></a>Comentarios

Los operadores aditivos son:

- Suma (**+**)

- Resta (**-**)

Estos operadores binarios tienen asociatividad de izquierda a derecha.

Los operadores aditivos toman operandos de tipos aritméticos o de puntero. El resultado de la suma (**+**) operador es la suma de los operandos. El resultado de la resta (**-**) operador es la diferencia entre los operandos. Si uno o ambos operandos son punteros, deben ser punteros a objetos, no a funciones. Si ambos operandos son punteros, los resultados no son significativos a menos que ambos sean punteros a objetos de la misma matriz.

Operadores aditivos toman operandos de *aritmético*, *integral*, y *escalares* tipos. Se definen en la tabla siguiente.

### <a name="types-used-with-additive-operators"></a>Tipos utilizados con operadores de suma

|Tipo|Significado|
|----------|-------------|
|*operaciones aritméticas*|Los tipos enteros y de punto flotante se denominan colectivamente tipos “aritméticos”.|
|*Entero*|Los tipos char e int de todos los tamaños (long, short) y las enumeraciones son tipos “enteros”.|
|*escalar*|Los operandos escalares son operandos de tipo aritmético o puntero.|

Las combinaciones válidas para estos operadores son:

*aritmética* + *aritmético*

*escalar* + *integral*

*entero* + *escalares*

*aritmética* - *aritmético*

*escalar* - *escalares*

Tenga en cuenta que la suma y resta no son operaciones equivalentes.

Si ambos operandos son de tipo aritmético, las conversiones descritas en [conversiones estándar](standard-conversions.md) se aplican a los operandos y el resultado es del tipo convertido.

## <a name="example"></a>Ejemplo

```cpp
// expre_Additive_Operators.cpp
// compile with: /EHsc
#include <iostream>
#define SIZE 5
using namespace std;
int main() {
   int i = 5, j = 10;
   int n[SIZE] = { 0, 1, 2, 3, 4 };
   cout  << "5 + 10 = " << i + j << endl
         << "5 - 10 = " << i - j << endl;

   // use pointer arithmetic on array

   cout << "n[3] = " << *( n + 3 ) << endl;
}
```

## <a name="pointer-addition"></a>Adición de puntero

Si uno de los operandos de una operación de suma es un puntero a una matriz de objetos, el otro debe ser de tipo entero. El resultado es un puntero del mismo tipo que el puntero original y que apunta a otro elemento de la matriz. En el siguiente fragmento de código se muestra este concepto:

```cpp
short IntArray[10]; // Objects of type short occupy 2 bytes
short *pIntArray = IntArray;

for( int i = 0; i < 10; ++i )
{
    *pIntArray = i;
    cout << *pIntArray << "\n";
    pIntArray = pIntArray + 1;
}
```

Aunque el valor entero 1 se suma a `pIntArray`, eso no significa “sumar 1 a la dirección”, sino más bien "ajustar el puntero para que apunte al siguiente objeto de la matriz”, que resulta estar alejado 2 bytes (o `sizeof( int )`).

> [!NOTE]
>  El código con la forma `pIntArray = pIntArray + 1` raramente aparece en programas de C++; para realizar un incremento, son preferibles estas formas: `pIntArray++` o `pIntArray += 1`.

## <a name="pointer-subtraction"></a>Resta de puntero

Si ambos operandos son punteros, el resultado de la resta es la diferencia (en elementos de matriz) entre los operandos. La expresión de resta produce un resultado entero con signo de tipo `ptrdiff_t` (definido en el archivo de inclusión estándar \<stddef.h >).

Uno de los operandos puede ser de tipo entero, siempre y cuando sea el segundo operando. El resultado de la resta es del mismo tipo que el puntero original. El valor de la resta es un puntero a la (*n* - *i*) elemento de la matriz de n, donde *n* es el elemento al que señala el puntero original y *i* es el valor entero del segundo operando.

## <a name="see-also"></a>Vea también

[Expresiones con operadores binarios](../cpp/expressions-with-binary-operators.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores de adición de C](../c-language/c-additive-operators.md)