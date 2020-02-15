---
title: bitset (Clase)
ms.date: 03/27/2019
f1_keywords:
- bitset/std::bitset
- bitset/std::bitset::element_type
- bitset/std::bitset::all
- bitset/std::bitset::any
- bitset/std::bitset::count
- bitset/std::bitset::flip
- bitset/std::bitset::none
- bitset/std::bitset::reset
- bitset/std::bitset::set
- bitset/std::bitset::size
- bitset/std::bitset::test
- bitset/std::bitset::to_string
- bitset/std::bitset::to_ullong
- bitset/std::bitset::to_ulong
- bitset/std::bitset::reference
helpviewer_keywords:
- std::bitset [C++]
- std::bitset [C++], element_type
- std::bitset [C++], all
- std::bitset [C++], any
- std::bitset [C++], count
- std::bitset [C++], flip
- std::bitset [C++], none
- std::bitset [C++], reset
- std::bitset [C++], set
- std::bitset [C++], size
- std::bitset [C++], test
- std::bitset [C++], to_string
- std::bitset [C++], to_ullong
- std::bitset [C++], to_ulong
- std::bitset [C++], reference
ms.assetid: 28b86964-87b4-429c-8124-b6c251b6c50b
ms.openlocfilehash: a4771e9c2c48bfe9c4c09629278533b031d60979
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "77258242"
---
# <a name="bitset-class"></a>bitset (Clase)

Describe un tipo de objeto que almacena una secuencia que consta de un número fijo de bits que proporcionan una manera compacta de mantener indicadores para un conjunto de elementos o condiciones. La clase bitset admite operaciones en objetos de tipo bitset que contienen una colección de bits y proporcionan acceso de tiempo constante a cada bit.

## <a name="syntax"></a>Sintaxis

```cpp
template <size_t N>
class bitset
```

### <a name="parameters"></a>Parámetros

*N*\
Especifica el número de bits del objeto BitSet con un entero distinto de cero de tipo `size_t` que debe conocerse en tiempo de compilación.

## <a name="remarks"></a>Observaciones

A diferencia de la clase similar [vector\<bool>](../standard-library/vector-bool-class.md), la clase bitset no tiene iteradores y no es un contenedor de la biblioteca estándar de C++. También se distingue de vector\<bool> en que es de un determinado tamaño específico que se fija en tiempo de compilación de acuerdo con el tamaño especificado por el parámetro de plantilla *N* cuando se declara **bitset\<N\>** .

Un bit se establece si su valor es 1 y se restablece si su valor es 0. Voltear o invertir un bit es cambiar su valor de 1 a 0 o de 0 a 1. Los bits *N* de un conjunto de bits están indexados por valores enteros de 0 a *N* -1, donde 0 indexa la posición del primer bit y, *N* -1, la posición del último bit.

## <a name="members"></a>Members

### <a name="constructors"></a>Constructores

|||
|-|-|
|[bitset](#bitset)|Construye un objeto de clase `bitset\<N>` e inicializa los bits a cero, hasta un valor especificado o hasta los valores obtenidos de los caracteres de una cadena.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[element_type](#element_type)|Un tipo que es un sinónimo del tipo de datos **bool** y se puede usar para hacer referencia a bits de elemento en un `bitset`.|

### <a name="functions"></a>Functions

|||
|-|-|
|[all](#all)|Comprueba todos los bits de este `bitset` para determinar si están establecidos en **true**.|
|[cualquiera](#any)|Función miembro que comprueba si cualquiera de los bits de la secuencia está establecido en 1.|
|[count](#count)|Función miembro que devuelve el número de bits establecidos en la secuencia de bits.|
|[flip](#flip)|Invierte el valor de todos los bits de un `bitset` o de un solo bit en una posición especificada.|
|[Ninguna](#none)|Comprueba si no se ha establecido ningún bit en 1 en un objeto `bitset`.|
|[reset](#reset)|Restablece todos los bits en un `bitset` en 0 o restablece un bit en una posición especificada en 0.|
|[set](#set)|Establece todos los bits en un `bitset` en 1 o establece un bit en una posición especificada en 1.|
|[size](#size)|Devuelve el número de bits de un objeto `bitset`.|
|[test](#test)|Comprueba si el bit de una posición especificada en un `bitset` está establecido en 1.|
|[to_string](#to_string)|Convierte un objeto `bitset` en una representación de cadena.|
|[to_ullong](#to_ullong)|Devuelve la suma de los valores de bit de la `bitset` como **unsigned Long Long**.|
|[to_ulong](#to_ulong)|Convierte un objeto de `bitset` en la **longitud sin signo** que generaría la secuencia de bits contenida si se utiliza para inicializar el `bitset`.|

### <a name="classes"></a>Clases

|||
|-|-|
|[reference](#reference)|Clase de proxy que proporciona referencias a los bits que contiene un `bitset` y que se usa para acceder y manipular los bits individuales como una clase del asistente para el `operator[]` de clase `bitset`.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator!=](#op_neq)|Comprueba si hay desigualdad entre un `bitset` de destino y un `bitset` especificado.|
|[operator&=](#op_and_eq)|Realiza una combinación bit a bit de los conjuntos de bits con la operación `AND` lógica.|
|[operator<<](#op_lshift)|Desplaza los bits de un `bitset` a la izquierda un número especificado de posiciones y devuelve el resultado a un nuevo `bitset`.|
|[operator<<=](#op_lshift_eq)|Desplaza los bits de un `bitset` a la izquierda un número especificado de posiciones y devuelve el resultado al `bitset` de destino.|
|[operator==](#op_eq_eq)|Comprueba si hay igualdad entre un `bitset` de destino y un `bitset` especificado.|
|[operator>>](#op_rshift)|Desplaza los bits de un `bitset` a la derecha un número especificado de posiciones y devuelve el resultado a un nuevo `bitset`.|
|[operator>>=](#op_rshift_eq)|Desplaza los bits de un `bitset` a la derecha un número especificado de posiciones y devuelve el resultado al `bitset` de destino.|
|[operator&#91;&#93;](#op_at)|Devuelve una referencia a un bit en una posición especificada en un `bitset` si el `bitset` es modificable; en caso contrario, devuelve el valor del bit en esa posición.|
|[operator^=](#op_xor_eq)|Realiza una combinación bit a bit de los conjuntos de bits con la operación `OR` exclusiva.|
|[operator&#124;=](#op_or_eq)|Realiza una combinación bit a bit de los conjuntos de bits con la operación `OR` inclusiva.|
|[operator~](#op_not)|Invierte todos los bits en un `bitset` de destino y devuelve el resultado.|

### <a name="structures"></a>Estructuras

|||
|-|-|
|[hash](#hash)||

### <a name="all"></a>todos

Comprueba todos los bits de este conjunto de bits para determinar si están establecidos en true.

```cpp
bool all() const;
```

#### <a name="return-value"></a>Valor devuelto

Devuelve true si todos los bits de este conjunto son true. Devuelve **False** si uno o más bits son False.

### <a name="any"></a>cualquier

Comprueba si algún bit de la secuencia está establecido en 1.

```cpp
bool any() const;
```

#### <a name="return-value"></a>Valor devuelto

**True** si algún bit del conjunto de bits está establecido en 1; **False** si todos los bits son 0.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_any.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   bool b, rb;

   cout << "The original bitset b1( 6 ) is: ( "<< b1 << " )"
        << endl;

   b = b1.any ( );

   if ( b )
      cout << "At least one of the bits in bitset is set to 1."
           << endl;
   else
      cout << "None of the bits in bitset are set to 1."
           << endl;

   bitset<5> rb1;
   rb1 = b1.reset ( );

   cout << "The reset bitset is: ( "<< b1 << " )"
        << endl;

   rb = rb1.any ( );

   if ( rb )
      cout << "At least one of the bits in the reset bitset "
           << "are set to 1." << endl;
   else
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
}
```

```Output
The original bitset b1( 6 ) is: ( 00110 )
At least one of the bits in bitset is set to 1.
The reset bitset is: ( 00000 )
None of the bits in bitset b1 are set to 1.
```

### <a name="bitset"></a>BitSet

Construye un objeto de clase `bitset\<N>` e inicializa los bits a cero, hasta un valor especificado o hasta los valores obtenidos de los caracteres de una cadena.

```cpp
bitset();

bitset(
    unsigned long long val);

explicit bitset(
    const char* _CStr);

template <class CharType,
    class Traits,
    class Allocator>
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos = 0);

template <class CharType,
    class Traits,
    class Allocator>
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos,
    typename basic_string<CharType, Traits, Allocator>::size_type count,
    CharType _Zero = CharType ('0'),
    CharType _One = CharType ('1'));
```

#### <a name="parameters"></a>Parámetros

\ *Val*
El entero sin signo cuya representación de base dos se usa para inicializar los bits del conjunto de bits que se está construyendo.

\ *Str*
La cadena de ceros y unos que se usa para inicializar los valores de bits del conjunto de bits.

*_CStr*\
Una cadena de estilo C de ceros y unos que se usa para inicializar los valores de bits del conjunto de bits.

*_Pos*\
La posición del carácter en la cadena, contando de izquierda a derecha y a partir de cero, que se usa para inicializar el primer bit del conjunto de bits.

*recuento*\
El número de caracteres de la cadena que se usa para proporcionar los valores iniciales de los bits del conjunto de bits.

*_Zero*\
El carácter que se usa para representar un cero. El valor predeterminado es "0".

*_One*\
El carácter que se usa para representar un uno. El valor predeterminado es "1".

#### <a name="remarks"></a>Observaciones

Se pueden usar tres constructores para crear objetos de clase `bitset\<N>`:

- El primer constructor no acepta parámetros, crea un objeto de clase `bitset\<N>` e inicializa todos los bits N en un valor predeterminado de cero.

- El segundo constructor crea un objeto de la clase `bitset\<N>` e inicializa los bits mediante el parámetro único **unsigned Long Long** .

- El tercer constructor crea un objeto de clase `bitset\<N>`, inicializando los bits N en valores que corresponden a los caracteres proporcionados en una cadena de caracteres de estilo c de ceros y unos. Llame al constructor sin convertir la cadena a un tipo de cadena: `bitset<5> b5("01011");`

También se proporcionan dos plantillas de constructor:

- La primera plantilla de constructor crea un objeto de clase `bitset\<N>` e inicializa bits de los caracteres proporcionados en una cadena de ceros y unos. Si algún carácter de la cadena es distinto de 0 o 1, el constructor produce un objeto de clase [argumento no válido](../standard-library/invalid-argument-class.md). Si la posición especificada ( *_Pos*) está más allá de la longitud de la cadena, el constructor produce un objeto de la clase [out_of_range](../standard-library/out-of-range-class.md). El constructor establece solo esos bits en la posición *j* en el conjunto de bits que tiene 1 como carácter de la cadena en la posición `_Pos + j`. De forma predeterminada, *_Pos* es 0.

- La segunda plantilla de constructor es similar a la primera, pero incluye un parámetro adicional (*Count*) que se usa para especificar el número de bits que se va a inicializar. También tiene dos parámetros opcionales, *_Zero* y *_One*, que indican qué carácter de *Str* se va a interpretar para indicar un bit 0 y un bit 1, respectivamente.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_bitset.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   // Using the default constructor
   using namespace std;
   bitset<2> b0;
   cout << "The set of bits in bitset<2> b0 is: ( "
        << b0 << " )." << endl;

   // Using the second member function
   bitset<5> b1 ( 6 );
   cout << "The set of bits in bitset<5> b1( 6 ) is: ( "
        << b1 << " )." << endl;

   // The template parameter N can be an expresssion
   bitset< 2 * sizeof ( int ) > b2;
   cout << "The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( "
        << b2 << " )." << endl;

   // The base two representation will be truncated
   // if its length exceeds the size of the bitset
   bitset<3> b3 ( 6 );
   cout << "The set of bits in bitset<3> b3( 6 ) is ( "
        << b3 << " )." << endl;

   // Using a c-style string to initialize the bitset
    bitset<7> b3andahalf ( "1001001" );
    cout << "The set of bits in bitset<7> b3andahalf ( \"1001001\" )"
         << " is ( " << b3andahalf << " )." << endl;

   // Using the fifth member function with the first parameter
   string bitval4 ( "10011" );
   bitset<5> b4 ( bitval4 );
   cout << "The set of bits in bitset<5> b4( bitval4 ) is ( "
        << b4 << " )." << endl;

   // Only part of the string may be used for initialization

   // Starting at position 3 for a length of 6 (100110)
   string bitval5 ("11110011011");
   bitset<6> b5 ( bitval5, 3, 6 );
   cout << "The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( "
        << b5 << " )." << endl;

   // The bits not initialized with part of the string
   // will default to zero
   bitset<11> b6 ( bitval5, 3, 5 );
   cout << "The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( "
        << b6 << " )." << endl;

   // Starting at position 2 and continue to the end of the string
   bitset<9> b7 ( bitval5, 2 );
   cout << "The set of bits in bitset<9> b7( bitval, 2 ) is ( "
        << b7 << " )." << endl;
}
```

```Output
The set of bits in bitset<2> b0 is: ( 00 ).
The set of bits in bitset<5> b1( 6 ) is: ( 00110 ).
The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( 00000000 ).
The set of bits in bitset<3> b3( 6 ) is ( 110 ).
The set of bits in bitset<5> b4( bitval4 ) is ( 10011 ).
The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( 100110 ).
The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( 00000010011 ).
The set of bits in bitset<9> b7( bitval, 2 ) is ( 110011011 ).
```

### <a name="count"></a>contabiliza

Devuelve el número de bits establecidos en la secuencia de bits.

```cpp
size_t count() const;
```

#### <a name="return-value"></a>Valor devuelto

Número de bits establecidos en la secuencia de bits.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_count.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
    using namespace std;

    bitset<5> b1(4);

    cout << "The collection of bits in the original bitset is: ( "
         << b1 << " )" << endl;

    size_t i;
    i = b1.count();
    cout << "The number of bits in the bitset set to 1 is: "
         << i << "." << endl;

    bitset<5> fb1;
    fb1 = b1.flip();

    cout << "The collection of flipped bits in the modified bitset "
         << "is: ( " << b1 << " )" << endl;

    size_t ii;
    ii = fb1.count();
    cout << "The number of bits in the bitset set to 1 is: "
         << ii << "." << endl;
}
```

```Output
The collection of bits in the original bitset is: ( 00100 )
The number of bits in the bitset set to 1 is: 1.
The collection of flipped bits in the modified bitset is: ( 11011 )
The number of bits in the bitset set to 1 is: 4.
```

### <a name="element_type"></a>element_type

Un tipo que es un sinónimo del tipo de datos **bool** y se puede usar para hacer referencia a bits de elemento en un BitSet.

```cpp
typedef bool element_type;
```

#### <a name="example"></a>Ejemplo

```cpp
// bitset_elem_type.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<3> b1 ( 2 );
   cout << "Original bitset b1(6) is: ( "<< b1 << " )"
        << endl;

   //Compare two ways to reference bits in a bitset
   bool b;
   bitset<5>::element_type e;

   b = b1.test ( 2 );
   if ( b )
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 1." << endl;
   else
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 0." << endl;
   b1[2] = 1;
   cout << "Bitset b1 modified by b1[2] = 1 is: ( "<< b1 << " )"
        << endl;

   e = b1.test ( 2 );
   if ( e )
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 1." << endl;
   else
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 0." << endl;
}
```

```Output
Original bitset b1(6) is: ( 010 )
The bit at position 2 of bitset b1has a value of 0.
Bitset b1 modified by b1[2] = 1 is: ( 110 )
The bit at position 2 of bitset b1has a value of 1.
```

### <a name="flip"></a>horizontal

Invierte el valor de todos los bits de un conjunto de bits o de un solo bit en una posición especificada.

```cpp
bitset\<N>& flip();
bitset\<N>& flip(size_t _Pos);
```

#### <a name="parameters"></a>Parámetros

*_Pos*\
La posición del bit cuyo valor se va a invertir.

#### <a name="return-value"></a>Valor devuelto

Una copia del conjunto de bits modificado para el que se ha invocado la función miembro.

#### <a name="remarks"></a>Observaciones

La segunda función miembro produce una excepción [out_of_range](../standard-library/out-of-range-class.md) si la posición especificada como parámetro es mayor que el tamaño *n* de **BitSet\<** *n* **>** cuyo bit se invierte.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_flip.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 6 );

   cout << "The collection of bits in the original bitset is: ( "
        << b1 << " )" << endl;

   bitset<5> fb1;
   fb1 = b1.flip ( );

   cout << "After flipping all the bits, the bitset becomes: ( "
        << fb1 << " )" << endl;

   bitset<5> f3b1;
   f3b1 = b1.flip ( 3 );

   cout << "After flipping the fourth bit, the bitset becomes: ( "
        << f3b1 << " )" << endl << endl;

   bitset<5> b2;
   int i;
   for ( i = 0 ; i <= 4 ; i++ )
   {
      b2.flip(i);
      cout << b2 << "  The bit flipped is in position "
           << i << ".\n";
   }
}
```

```Output
The collection of bits in the original bitset is: ( 00110 )
After flipping all the bits, the bitset becomes: ( 11001 )
After flipping the fourth bit, the bitset becomes: ( 10001 )

00001  The bit flipped is in position 0.
00011  The bit flipped is in position 1.
00111  The bit flipped is in position 2.
01111  The bit flipped is in position 3.
11111  The bit flipped is in position 4.
```

### <a name="hash"></a>LM

```cpp
template <class T> struct hash;
template <size_t N> struct hash<bitset<N>>;
```

### <a name="none"></a>ninguna

Comprueba si no se ha establecido ningún bit en 1 en un objeto bitset.

```cpp
bool none() const;
```

#### <a name="return-value"></a>Valor devuelto

**True** si no se ha establecido ningún bit en el conjunto de bits en 1; **False** si se ha establecido al menos un bit en 1.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_none.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   bool b, rb;

   cout << "Original bitset b1(6) is: ( " << b1 << " )"
        << endl;

   b = b1.none ( );

   if ( b )
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
   else
      cout << "At least one of the bits in bitset b1 is set to 1."
           << endl;

   bitset<5> rb1;
   rb1 = b1.reset ( );
   rb = rb1.none ( );
   if ( rb )
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
   else
      cout << "At least one of the bits in bitset b1 is set to 1."
           << endl;
}
```

```Output
Original bitset b1(6) is: ( 00110 )
At least one of the bits in bitset b1 is set to 1.
None of the bits in bitset b1 are set to 1.
```

### <a name="op_neq"></a>operador! =

Comprueba si hay desigualdad entre un conjunto de bits de destino y un conjunto de bits especificado.

```cpp
bool operator!=(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>Parámetros

\ *derecha*
Conjunto de bits que va a compararse con el conjunto de bits de destino para comprobar si son iguales.

#### <a name="return-value"></a>Valor devuelto

**True** si los conjuntos de bits son diferentes; **False** si son iguales.

#### <a name="remarks"></a>Observaciones

Los conjuntos de bits deben ser del mismo tamaño para que la función de operador miembro compruebe si son iguales.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_op_NE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 7 );
   bitset<5> b3 ( 2 );
   bitset<4> b4 ( 7 );

   if ( b1 != b2 )
      cout << "Bitset b1 is different from bitset b2." << endl;
   else
      cout << "Bitset b1 is the same as bitset b2." << endl;

   if ( b1 != b3 )
      cout << "Bitset b1 is different from bitset b3." << endl;
   else
      cout << "Bitset b1 is the same as bitset b3." << endl;

   // This would cause an error because bitsets must have the
   // same size to be tested
   // if ( b1 != b4 )
   //   cout << "Bitset b1 is different from bitset b4." << endl;
   // else
   //   cout << "Bitset b1 is the same as bitset b4." << endl;
}
```

```Output
Bitset b1 is the same as bitset b2.
Bitset b1 is different from bitset b3.
```

### <a name="op_and_eq"></a>operador&amp;=

Realiza una combinación bit a bit de los conjuntos de bits con la operación `AND` lógica.

```cpp
bitset\<N>& operator&=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Parámetros

\ *derecha*
El conjunto de bits que se va a combinar bit a bit con el conjunto de bits de destino.

#### <a name="return-value"></a>Valor devuelto

BitSet de destino modificado que es el resultado de la operación de `AND` bit a bit con el BitSet especificado como parámetro.

#### <a name="remarks"></a>Observaciones

Dos bits combinados mediante el operador `AND` devuelven **true** si cada bit es true; de lo contrario, su combinación devuelve **false**.

Conjuntos debe ser del mismo tamaño para que la función de operador miembro los combine bit a bit con el operador `AND`.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_op_bitwise.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 &= b2;
   cout << "After bitwise AND combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset is unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 &= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise AND combination,
the target bitset b1 becomes:   ( 00011 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="op_lshift"></a>operador\<\<

Desplaza los bits de un conjunto de bits a la izquierda un número especificado de posiciones y devuelve el resultado a un nuevo conjunto de bits.

```cpp
bitset\<N> operator<<(size_t _Pos) const;
```

#### <a name="parameters"></a>Parámetros

*_Pos*\
El número de posiciones a la izquierda que se desplazarán los bits en el conjunto de bits.

#### <a name="return-value"></a>Valor devuelto

Conjunto de bits modificado con los bits que se han desplazado a la izquierda el número de posiciones requerido.

#### <a name="remarks"></a>Observaciones

La función de operador miembro devuelve **bitset**( **\*this**) **<<= pos,** donde [<<=](#op_lshift_eq) desplaza los bits de un conjunto de bits a la izquierda un número especificado de posiciones y devuelve el resultado al conjunto de bits de destino.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_op_LS.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;

   bitset<5> b2;
   b2 = b1 << 2;

   cout << "After shifting the bits 2 positions to the left,\n"
        << " the bitset b2 is: ( "<< b2 << " )."
        << endl;

   bitset<5> b3 = b2 >> 1;

   cout << "After shifting the bits 1 position to the right,\n"
        << " the bitset b3 is: ( " << b3 << " )."
        << endl;
}
```

### <a name="op_lshift_eq"></a>operador&lt;&lt;=

Desplaza los bits de un conjunto de bits a la izquierda un número especificado de posiciones y devuelve el resultado al conjunto de bits de destino.

```cpp
bitset\<N>& operator<<=(size_t _Pos);
```

#### <a name="parameters"></a>Parámetros

*_Pos*\
El número de posiciones a la izquierda que se desplazarán los bits en el conjunto de bits.

#### <a name="return-value"></a>Valor devuelto

Conjunto de bits de destino modificado de modo que los bits se hayan desplazado a la izquierda el número de posiciones requerido.

#### <a name="remarks"></a>Observaciones

Si no existe ningún elemento para desplazar en la posición, la función pone el bit en un valor de 0.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_op_LSE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;
   b1 <<= 2;
   cout << "After shifting the bits 2 positions to the left,\n"
        << "the target bitset b1 becomes: ( "<< b1 << " )."
        << endl;
}
```

```Output
The target bitset b1 is: ( 00111 ).
After shifting the bits 2 positions to the left,
the target bitset b1 becomes: ( 11100 ).
```

### <a name="op_eq_eq"></a>operador = =

Comprueba si hay igualdad entre un conjunto de bits de destino y un conjunto de bits especificado.

```cpp
bool operator==(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>Parámetros

\ *derecha*
Conjunto de bits que va a compararse con el conjunto de bits de destino para comprobar si hay igualdad.

#### <a name="return-value"></a>Valor devuelto

**True** si los conjuntos de bits son iguales; **False** si son diferentes.

#### <a name="remarks"></a>Observaciones

Los conjuntos de bits deben ser del mismo tamaño para que la función de operador miembro compruebe su igualdad.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_op_EQ.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 7 );
   bitset<5> b3 ( 2 );
   bitset<4> b4 ( 7 );

   if ( b1 == b2 )
      cout << "Bitset b1 is the same as bitset b2." << endl;
   else
      cout << "Bitset b1 is different from bitset b2." << endl;

   if ( b1 == b3 )
      cout << "Bitset b1 is the same as bitset b3." << endl;
   else
      cout << "Bitset b1 is different from bitset b3." << endl;

   // This would cause an error because bitsets must have the
   // same size to be tested
   // if ( b1 == b4 )
   //   cout << "Bitset b1 is the same as bitset b4." << endl;
   // else
   //   cout << "Bitset b1 is different from bitset b4." << endl;
}
```

```Output
Bitset b1 is the same as bitset b2.
Bitset b1 is different from bitset b3.
```

### <a name="op_rshift"></a>operador&gt;&gt;

Desplaza los bits de un conjunto de bits a la derecha un número especificado de posiciones y devuelve el resultado a un nuevo conjunto de bits.

```cpp
bitset\<N> operator>>(size_t _Pos) const;
```

#### <a name="parameters"></a>Parámetros

*_Pos*\
El número de posiciones a la derecha que se desplazarán los bits en el conjunto de bits.

#### <a name="return-value"></a>Valor devuelto

Un nuevo conjunto de bits en que los bits se han desplazado a la derecha el número de posiciones requerido en relación con el conjunto de bits de destino.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_op_RS.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;

   bitset<5> b2;
   b2 = b1 << 2;

   cout << "After shifting the bits 2 positions to the left,\n"
        << "the bitset b2 is: ( "<< b2 << " )."
        << endl;
   bitset<5> b3 = b2 >> 1;

   cout << "After shifting the bits 1 position to the right,\n"
        << "the bitset b3 is: ( " << b3 << " )."
        << endl;
}
```

```Output
The bitset b1 is: ( 00111 ).
After shifting the bits 2 positions to the left,
the bitset b2 is: ( 11100 ).
After shifting the bits 1 position to the right,
the bitset b3 is: ( 01110 ).
```

### <a name="op_rshift_eq"></a>operador&gt;&gt;=

Desplaza los bits de un conjunto de bits a la derecha un número especificado de posiciones y devuelve el resultado en el conjunto de bits de destino.

```cpp
bitset\<N>& operator>>=(size_t _Pos);
```

#### <a name="parameters"></a>Parámetros

*_Pos*\
El número de posiciones a la derecha que se desplazarán los bits en el conjunto de bits.

#### <a name="return-value"></a>Valor devuelto

Conjunto de bits de destino modificado de modo que los bits se hayan desplazado a la derecha el número de posiciones requerido.

#### <a name="remarks"></a>Observaciones

Si no existe ningún elemento para desplazar en la posición, la función pone el bit en un valor de 0.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_op_RSE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 28 );
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;

   b1 >>= 2;
   cout << "After shifting the bits 2 positions to the right,\n"
        << "the target bitset b1 becomes: ( "<< b1 << " )."
        << endl;
}
```

```Output
The target bitset b1 is: ( 11100 ).
After shifting the bits 2 positions to the right,
the target bitset b1 becomes: ( 00111 ).
```

### <a name="op_at"></a>operador []

Devuelve una referencia a un bit en una posición especificada en un conjunto de bits si este es modificable; en caso contrario, devuelve el valor del bit en esa posición.

```cpp
bool operator[](size_t _Pos) const;
reference operator[](size_t _Pos);
```

#### <a name="parameters"></a>Parámetros

*_Pos*\
La posición que localiza el bit en el conjunto de bits.

#### <a name="remarks"></a>Observaciones

Al definir [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md) como 1 o 2 en la compilación, se producirá un error en tiempo de ejecución en el ejecutable si intenta obtener acceso a un elemento fuera de los límites del conjunto de bits. Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

#### <a name="example"></a>Ejemplo

```cpp
// bitset_op_REF.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bool b;
   bitset<5> b1 ( 6 );
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."
        << endl;

   int i;
   for ( i = 0 ; i <= 4 ; i++ )
   {
      b = b1[ i ];
      cout << "  The bit in position "
           << i << " is " << b << ".\n";
   }
}
```

### <a name="op_xor_eq"></a>operador ^ =

Realiza una combinación bit a bit de los conjuntos de bits con la operación `OR` exclusiva.

```cpp
bitset\<N>& operator^=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Parámetros

\ *derecha*
El conjunto de bits que se va a combinar bit a bit con el conjunto de bits de destino.

#### <a name="return-value"></a>Valor devuelto

Conjunto de bits de destino modificado resultante de la operación `OR` exclusiva bit a bit con el conjunto de bits especificado como parámetro.

#### <a name="remarks"></a>Observaciones

Dos bits combinados mediante el operador exclusivo **OR** devuelven **True** si al menos uno de los bits, pero no ambos, es **True**; en caso contrario, la combinación devuelve **False**.

Los conjuntos de bits deben ser del mismo tamaño para que la función de operador miembro los combine bit a bit con el operador exclusivo `OR`.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_op_bitwiseOR.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 ^= b2;
   cout << "After bitwise exclusive OR combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset in unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 |= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise exclusive OR combination,
the target bitset b1 becomes:   ( 01100 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="op_or_eq"></a>operador&#124;=

Realiza una combinación bit a bit de los conjuntos de bits con la operación `OR` inclusiva.

```cpp
bitset\<N>& operator|=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Parámetros

\ *derecha*
El conjunto de bits que se va a combinar bit a bit con el conjunto de bits de destino.

#### <a name="return-value"></a>Valor devuelto

Conjunto de bits de destino modificado resultante de la operación `OR` inclusiva bit a bit con el conjunto de bits especificado como parámetro.

#### <a name="remarks"></a>Observaciones

Dos bits combinados mediante el operador inclusivo `OR` devuelven **True** si al menos uno de los bits es **True**; si los dos bits son **False**, la combinación devuelve **False**.

Los conjuntos de bits deben ser del mismo tamaño para que la función de operador miembro los combine bit a bit con el operador inclusivo `OR`.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_op_BIO.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 |= b2;
   cout << "After bitwise inclusive OR combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset in unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 |= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise inclusive OR combination,
the target bitset b1 becomes:   ( 01111 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="op_not"></a>operador ~

Invierte todos los bits en un conjunto de bits de destino y devuelve el resultado.

```cpp
bitset\<N> operator~() const;
```

#### <a name="return-value"></a>Valor devuelto

Conjunto de bits con todos sus bits invertidos con respecto al conjunto de bits de destino.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_op_invert.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <bitset>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2;
   b2 = ~b1;

   cout << "Bitset b1 is: ( "<< b1 << " )." << endl;
   cout << "Bitset b2 = ~b1 is: ( "<< b2 << " )." << endl;

   // These bits could also be flipped using the flip member function
   bitset<5> b3;
   b3 = b1.flip( );
   cout << "Bitset b3 = b1.flip( ) is: ( "<< b2 << " )." << endl;
}
```

```Output
Bitset b1 is: ( 00111 ).
Bitset b2 = ~b1 is: ( 11000 ).
Bitset b3 = b1.flip( ) is: ( 11000 ).
```

### <a name="reference"></a>referencia

Clase de proxy que proporciona referencias a los bits que contiene un conjunto de bits y que se usa para acceder y manipular los bits individuales como una clase del asistente para el `operator[]` de clase bitset.

```cpp
class reference {
   friend class bitset\<N>;
public:
   reference& operator=(bool val);
   reference& operator=(const reference& _Bitref);
   bool operator~() const;
   operator bool() const;
   reference& flip();
};
```

#### <a name="parameters"></a>Parámetros

\ *Val*
Valor del objeto de tipo **bool** que se va a asignar a un bit en un BitSet.

*_Bitref*\
Una referencia con el formato *x [ i ]* al bit en la posición *i* en el conjunto de bits *x*.

#### <a name="return-value"></a>Valor devuelto

Una referencia al bit en el conjunto de bits especificado por la posición del argumento para la primera, segunda y quinta función miembro de referencia de clase, y **True** o **False**, para reflejar el valor del bit modificado en el conjunto de bits para la tercera y cuarta función miembro de referencia de clase.

#### <a name="remarks"></a>Observaciones

La clase `reference` solo existe como una clase del asistente para el conjunto de bits `operator[]`. La clase de miembro describe un objeto que puede tener acceso a un bit individual dentro de un conjunto de bits. Permita que *b* sea un objeto de tipo **bool**, x *e y* de tipo **BitSet\<** *N* **>** y las posiciones válidas *i* y *j* dentro de dicho objeto. La notación *x [i]* hace referencia al bit en la posición *i* en el conjunto de bits *x*. Las funciones miembro de clase `reference` proporcionan, en orden, las siguientes operaciones:

|Operación|Definición|
|---------------|----------------|
|*x*[*i*] = *b*|Almacena el valor **booleano** *b* en la posición de bit *i* en BitSet *x*.|
|*x*[*i*] = *y*[*j*]|Almacena el valor del bit *y*[ *j*] en la posición de bit *i* en el conjunto de bits *x*.|
|*b* = ~ *x*[*i*]|Almacena el valor volteado del bit *x*[ *i*] en **bool** *b*.|
|*b* = *x*[*i*]|Almacena el valor del bit *x*[ *i*] en **bool** *b*.|
|*x*[*i*]. `flip`( )|Vuelve a almacenar el valor volteado del bit *x*[ *i*] en la posición del bit *i* en *x*.|

#### <a name="example"></a>Ejemplo

```cpp
// bitset_reference.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 2 );
   bitset<5> b2 ( 6 );
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."
        << endl;
   cout << "The initialized bitset<5> b2( 6 ) is: ( "<< b2 << " )."
        << endl;

   // Example of x [i] = b storing bool b at bit position i
   // in bitset x
   b1[ 0 ] = true;
   cout << "The bitset<5> b1 with the bit at position 0 set to 1"
        << "is: ( "<< b1 << " )" << endl;

   // Example of x [i] = y [j] storing the bool value of the
   // bit at position j in bitset y at bit position i in bitset x
   b2 [4] = b1 [0];      // b1 [0] = true
   cout << "The bitset<5> b2 with the bit at position 4 set to the "
        << "value\nof the bit at position 0 of the bit in "
        << "bitset<5> b1 is: ( "<<  b2  << " )" << endl;

   // Example of b = ~x [i] flipping the value of the bit at
   // position i of bitset x and storing the value in an
   // object b of type bool
   bool b = ~b2 [4];      // b2 [4] = false
   if ( b )
      cout << "The value of the object b = ~b2 [4] "
           << "of type bool is true." << endl;
   else
      cout << "The value of the object b = ~b2 [4] "
           << "of type bool is false." << endl;

   // Example of b = x [i] storing the value of the bit at
   // position i of bitset x in the object b of type bool
   b = b2 [4];
   if ( b )
      cout << "The value of the object b = b2 [4] "
           << "of type bool is true." << endl;
   else
      cout << "The value of the object b = b2 [4] "
           << "of type bool is false." << endl;

   // Example of x [i] . flip ( ) toggling the value of the bit at
   // position i of bitset x
   cout << "Before flipping the value of the bit at position 4 in "
        << "bitset b2,\nit is ( "<<  b2  << " )." << endl;
   b2 [4].flip( );
   cout << "After flipping the value of the bit at position 4 in "
        << "bitset b2,\nit becomes ( "<<  b2  << " )." << endl;
   bool c;
   c = b2 [4].flip( );
   cout << "After a second flip, the value of the position 4 "
        << "bit in b2 is now: " << c << ".";
}
```

```Output
The initialized bitset<5> b1( 2 ) is: ( 00010 ).
The initialized bitset<5> b2( 6 ) is: ( 00110 ).
The bitset<5> b1 with the bit at position 0 set to 1 is: ( 00011 )
The bitset<5> b2 with the bit at position 4 set to the value
of the bit at position 0 of the bit in bitset<5> b1 is: ( 10110 )
The value of the object b = ~b2 [4] of type bool is false.
The value of the object b = b2 [4] of type bool is true.
Before flipping the value of the bit at position 4 in bitset b2,
it is ( 10110 ).
After flipping the value of the bit at position 4 in bitset b2,
it becomes ( 00110 ).
After a second flip, the value of the position 4 bit in b2 is now: 1.
```

### <a name="reset"></a>determinado

Restablece todos los bits en un conjunto de bits en 0 o restablece un bit en una posición especificada en 0.

```cpp
bitset\<N>& reset();
bitset\<N>& reset(size_t _Pos);
```

#### <a name="parameters"></a>Parámetros

*_Pos*\
La posición del bit en el conjunto de bits que se restablecerá en 0.

#### <a name="return-value"></a>Valor devuelto

Una copia del conjunto de bits para el que se ha invocado la función miembro.

#### <a name="remarks"></a>Observaciones

La segunda función miembro produce una excepción [out_of_range](../standard-library/out-of-range-class.md) si la posición especificada es mayor que el tamaño del conjunto de bits.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_reset.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 13 );
   cout << "The set of bits in bitset<5> b1(13) is: ( "<< b1 << " )"
        << endl;

   bitset<5> b1r3;
   b1r3 = b1.reset( 2 );
   cout << "The collecion of bits obtained from resetting the\n"
        << "third bit of bitset b1 is: ( "<< b1r3 << " )"
        << endl;

   bitset<5> b1r;
   b1r = b1.reset( );
   cout << "The collecion of bits obtained from resetting all\n"
        << "the elements of the bitset b1 is: ( "<< b1r << " )"
        << endl;
}
```

```Output
The set of bits in bitset<5> b1(13) is: ( 01101 )
The collecion of bits obtained from resetting the
third bit of bitset b1 is: ( 01001 )
The collecion of bits obtained from resetting all
the elements of the bitset b1 is: ( 00000 )
```

### <a name="set"></a>conjunto

Establece todos los bits en un conjunto de bits en 1 o establece un bit en una posición especificada en 1.

```cpp
bitset\<N>& set();

bitset\<N>& set(
    size_t _Pos,
    bool val = true);
```

#### <a name="parameters"></a>Parámetros

*_Pos*\
La posición del bit en el conjunto de bits que se establecerá para que asigne un valor.

\ *Val*
Valor que se asignará al bit en la posición especificada.

#### <a name="return-value"></a>Valor devuelto

Una copia del conjunto de bits para el que se ha invocado la función miembro.

#### <a name="remarks"></a>Observaciones

La segunda función miembro produce una excepción [out_of_range](../standard-library/out-of-range-class.md) si la posición especificada es mayor que el tamaño del conjunto de bits.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_set.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   cout << "The set of bits in bitset<5> b1(6) is: ( "<< b1 << " )"
        << endl;

   bitset<5> b1s0;
   b1s0 = b1.set( 0 );
   cout << "The collecion of bits obtained from setting the\n"
        << "zeroth bit of bitset b1 is: ( "<< b1s0 << " )"
        << endl;

   bitset<5> bs1;
   bs1 = b1.set( );
   cout << "The collecion of bits obtained from setting all the\n"
        << "elements of the bitset b1 is: ( "<< bs1 << " )"
        << endl;
}
```

```Output
The set of bits in bitset<5> b1(6) is: ( 00110 )
The collecion of bits obtained from setting the
zeroth bit of bitset b1 is: ( 00111 )
The collecion of bits obtained from setting all the
elements of the bitset b1 is: ( 11111 )
```

### <a name="size"></a>ajusta

Devuelve el número de bits de un objeto bitset.

```cpp
size_t size() const;
```

#### <a name="return-value"></a>Valor devuelto

Número de bits, *N*, de un conjunto de bits\<N>.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_size.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main()
{
    using namespace std;

    bitset<5> b1(6);
    size_t i;

    cout << "The set of bits in bitset<5> b1( 6 ) is: ( "<< b1 << " )"
         << endl;

    i = b1.size();

    cout << "The number of bits in bitset b1 is: " << i << "."
         << endl;
}
```

```Output
The set of bits in bitset<5> b1( 6 ) is: ( 00110 )
The number of bits in bitset b1 is: 5.
```

### <a name="test"></a>muestre

Comprueba si el bit de una posición especificada en un conjunto de bits está establecido en 1.

```cpp
bool test(size_t _Pos) const;
```

#### <a name="parameters"></a>Parámetros

*_Pos*\
La posición del bit en el conjunto de bits al que se comprobará el valor.

#### <a name="return-value"></a>Valor devuelto

**True** si el bit especificado por la posición del argumento está establecido en 1; de lo contrario, **False**.

#### <a name="remarks"></a>Observaciones

La función miembro produce un [out_of_range](../standard-library/out-of-range-class.md)

### <a name="to_string"></a>to_string

Convierte un objeto BitSet en una representación de cadena.

```cpp
template <class charT = char, class traits = char_traits<charT>, class Allocator = allocator<charT> >
   basic_string<charT, traits, Allocator> to_string(charT zero = charT('0'), charT one = charT('1')) const;
```

#### <a name="return-value"></a>Valor devuelto

Objeto de cadena de la clase `basic_string`, donde cada bit establecido en BitSet tiene un carácter correspondiente de 1 y un carácter de 0 si el bit no está establecido.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_to_string.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The ordered set of bits in the bitset<5> b1( 7 )"
        << "\n  that was generated by the number 7 is: ( "
        << b1 << " )" << endl;

   string s1;
   s1 =  b1.template to_string<char,
   char_traits<char>, allocator<char> >( );
   cout << "The string returned from the bitset b1"
        << "\n  by the member function to_string( ) is: "
        << s1 << "." << endl;
}
```

```Output
The ordered set of bits in the bitset<5> b1( 7 )
  that was generated by the number 7 is: ( 00111 )
The string returned from the bitset b1
  by the member function to_string( ) is: 00111.
```

### <a name="to_ullong"></a>to_ullong

Devuelve un valor Long Long **sin signo** que contiene los mismos bits establecidos como el contenido del objeto BitSet.

```cpp
unsigned long long to_ullong() const;
```

#### <a name="return-value"></a>Valor devuelto

Devuelve la suma de los valores de bit que se encuentran en la secuencia de bits como **unsigned Long Long**. Este valor **unsigned Long Long** creará de nuevo los mismos bits de conjunto si se usa para inicializar un BitSet.

#### <a name="exceptions"></a>Excepciones

Produce una [overflow_error](overflow-error-class.md) objeto si algún bit de la secuencia de bits tiene un valor de bit que no se puede representar como un valor de tipo **unsigned Long Long**.

#### <a name="remarks"></a>Observaciones

Devuelve la suma de los valores de bit que se encuentran en la secuencia de bits como **unsigned Long Long**.

### <a name="to_ulong"></a>to_ulong

Convierte un objeto BitSet en el entero que generaría la secuencia de bits contenida si se usa para inicializar el BitSet.

```cpp
unsigned long to_ulong( ) const;
```

#### <a name="return-value"></a>Valor devuelto

Un entero que generaría los bits en un BitSet si se usa en la inicialización de BitSet.

#### <a name="remarks"></a>Observaciones

Al aplicar la función miembro, se devolvería el entero que tiene la misma secuencia de 1 y 0 dígitos que se encuentra en la secuencia de bits contenida en BitSet.

La función miembro produce un objeto [overflow_error](overflow-error-class.md) si algún bit de la secuencia de bits tiene un valor de bit que no se puede representar como un valor de tipo **unsigned Long**.

#### <a name="example"></a>Ejemplo

```cpp
// bitset_to_ulong.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The ordered set of bits in the bitset<5> b1( 7 )"
        << "\n  that was generated by the number 7 is: ( "
        << b1 << " )" << endl;

   unsigned long int i;
   i = b1.to_ulong( );
   cout << "The integer returned from the bitset b1,"
        << "\n  by the member function to_long( ), that"
        << "\n  generated the bits as a base two number is: "
        << i << "." << endl;
}
```

```Output
The ordered set of bits in the bitset<5> b1( 7 )
  that was generated by the number 7 is: ( 00111 )
The integer returned from the bitset b1,
  by the member function to_long( ), that
  generated the bits as a base two number is: 7.
```
