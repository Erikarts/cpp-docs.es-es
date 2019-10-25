---
title: Operadores de &lt;string&gt;
ms.date: 11/04/2016
f1_keywords:
- string/std::operator!=
- string/std::operator&gt;
- string/std::operator&gt;&gt;
- string/std::operator&gt;=
- string/std::operator&lt;
- string/std::operator&lt;&lt;
- string/std::operator&lt;=
- string/std::operator+
- string/std::operator==
ms.assetid: 33ce8f05-06c7-45d3-a0cb-bcd27cf93910
helpviewer_keywords:
- std::operator!= (string)
- std::operator&gt; (string)
- std::operator&gt;&gt; (string)
- std::operator&gt;= (string)
- std::operator&lt; (string)
- std::operator&lt;&lt; (string)
- std::operator&lt;= (string), std::operator== (string)
ms.openlocfilehash: f9aa07f7ca30ded5f61e77a327efafe91aa5c269
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685996"
---
# <a name="ltstringgt-operators"></a>Operadores de &lt;string&gt;

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;&gt;](#op_gt_gt)|
|[operator&gt;=](#op_gt_eq)|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|
|[operator&lt;=](#op_lt_eq)|[operator+](#op_add)|[operator==](#op_eq_eq)|

## <a name="op_add"></a>  operator+

Concatena dos objetos de cadena.

```cpp
template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const CharType left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    CharType right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    CharType left,
    const basic_string<CharType, Traits, Allocator>&& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Cadena de estilo C o un objeto del tipo `basic_string` que se va a concatenar.

\ *derecha*
Cadena de estilo C o un objeto del tipo `basic_string` que se va a concatenar.

### <a name="return-value"></a>Valor devuelto

Cadena que es la concatenación de las cadenas de entrada.

### <a name="remarks"></a>Comentarios

Las funciones de cada sobrecarga `operator+` concatenar dos objetos de la [clase basic_string](../standard-library/basic-string-class.md)de la plantilla de clase. Todos los `basic_string< CharType, Traits, Allocator>(Left).append(right)` devuelven de forma efectiva. Para obtener más información, vea [Append](../standard-library/basic-string-class.md#append).

### <a name="example"></a>Ejemplo

```cpp
// string_op_con.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an object of type basic_string<char>
   string s1 ( "anti" );
   string s2 ( "gravity" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "heroine";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // Declaring a character constant
   char c1 = '!';
   cout << "The character constant c1 = " << c1 << "." << endl;

   // First member function: concatenates an  object
   // of type basic_string with an object of type basic_string
   string s12 = s1 + s2;
   cout << "The string concatenating s1 & s2 is: " << s12 << endl;

   // Second & fourth member functions: concatenate an object
   // of type basic_string with an object of C-syle string type
   string s1s3 = s1 + s3;
   cout << "The string concatenating s1 & s3 is: " << s1s3 << endl;

   // Third & fifth member functions: concatenate an object
   // of type basic_string with a character constant
   string s1s3c1 = s1s3 + c1;
   cout << "The string concatenating s1 & s3 is: " << s1s3c1 << endl;
}
```

```Output
The basic_string s1 = anti.
The basic_string s2 = gravity.
The C-style string s3 = heroine.
The character constant c1 = !.
The string concatenating s1 & s2 is: antigravity
The string concatenating s1 & s3 is: antiheroine
The string concatenating s1 & s3 is: antiheroine!
```

## <a name="op_neq"></a>  operator!=

Comprueba si el objeto de cadena del lado izquierdo del operador no es igual que el objeto de cadena del lado derecho.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator!=(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator!=(
    const basic_string<CharType, Traits, Allocator>& left,
const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator!=(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Una cadena de estilo C o un objeto del tipo `basic_string` que se va a comparar.

\ *derecha*
Una cadena de estilo C o un objeto del tipo `basic_string` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si el objeto de cadena del lado izquierdo del operador no es lexicográficamente igual que el objeto de cadena del lado derecho. En caso contrario, es **false**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de cadena se basa en una comparación lexicográfica en pares de sus elementos. Dos cadenas son iguales si tienen el mismo número de caracteres y sus valores de carácter respectivos son los mismos. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// string_op_ne.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "pluck" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "pluck";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 != s2 )
      cout << "The strings s1 & s2 are not equal." << endl;
   else
      cout << "The strings s1 & s2 are equal." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s1 != s3 )
      cout << "The strings s1 & s3 are not equal." << endl;
   else
      cout << "The strings s1 & s3 are equal." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s3 != s2 )
      cout << "The strings s3 & s2 are not equal." << endl;
   else
      cout << "The strings s3 & s2 are equal." << endl;
}
```

```Output
The basic_string s1 = pluck.
The basic_string s2 = strum.
The C-style string s3 = pluck.
The strings s1 & s2 are not equal.
The strings s1 & s3 are equal.
The strings s3 & s2 are not equal.
```

## <a name="op_eq_eq"></a> operator==

Comprueba si el objeto de cadena del lado izquierdo del operador es igual que el objeto de cadena del lado derecho.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator==(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator==(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator==(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Una cadena de estilo C o un objeto del tipo `basic_string` que se va a comparar.

\ *derecha*
Una cadena de estilo C o un objeto del tipo `basic_string` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si el objeto de cadena del lado izquierdo del operador es lexicográficamente igual que el objeto de cadena del lado derecho. En caso contrario, es **false**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de cadena se basa en una comparación lexicográfica en pares de sus elementos. Dos cadenas son iguales si tienen el mismo número de caracteres y sus valores de carácter respectivos son los mismos. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// string_op_eq.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "pluck" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "pluck";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 == s2 )
      cout << "The strings s1 & s2 are equal." << endl;
   else
      cout << "The strings s1 & s2 are not equal." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s1 == s3 )
      cout << "The strings s1 & s3 are equal." << endl;
   else
      cout << "The strings s1 & s3 are not equal." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s3 == s2 )
      cout << "The strings s3 & s2 are equal." << endl;
   else
      cout << "The strings s3 & s2 are not equal." << endl;
}
```

```Output
The basic_string s1 = pluck.
The basic_string s2 = strum.
The C-style string s3 = pluck.
The strings s1 & s2 are not equal.
The strings s1 & s3 are equal.
The strings s3 & s2 are not equal.
```

## <a name="op_lt"></a>  operator&lt;

Comprueba si el objeto de cadena del lado izquierdo del operador es menor que el objeto de cadena del lado derecho.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator<(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator<(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator<(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Una cadena de estilo C o un objeto del tipo `basic_string` que se va a comparar.

\ *derecha*
Una cadena de estilo C o un objeto del tipo `basic_string` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si el objeto de cadena del lado izquierdo del operador es lexicográficamente menor que el objeto de cadena del lado derecho. En caso contrario, es **false**.

### <a name="remarks"></a>Comentarios

Una comparación lexicográfica entre cadenas las compara carácter por carácter hasta que:

- Encuentra dos caracteres correspondientes distintos y el resultado de la comparación se toma como el resultado de la comparación entre las cadenas.

- No encuentra ninguna desigualdad, pero una cadena tiene más caracteres que la otra y la cadena más corta se considera menor que la cadena más larga.

- No encuentra ninguna desigualdad y encuentra que las cadenas tienen el mismo número de caracteres, por lo que las cadenas son iguales.

### <a name="example"></a>Ejemplo

```cpp
// string_op_lt.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "strict";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 < s2 )
      cout << "The string s1 is less than the string s2." << endl;
   else
      cout << "The string s1 is not less than the string s2." << endl;

   // Second member function: comparison between left-hand object
   // of type basic_string & right-hand object of C-syle string type
   if ( s1 < s3 )
      cout << "The string s1 is less than the string s3." << endl;
   else
      cout << "The string s1 is not less than the string s3." << endl;

   // Third member function: comparison between left-hand object
   // of C-syle string type & right-hand object of type basic_string
   if ( s3 < s2 )
      cout << "The string s3 is less than the string s2." << endl;
   else
      cout << "The string s3 is not less than the string s2." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = strict.
The string s1 is less than the string s2.
The string s1 is not less than the string s3.
The string s3 is less than the string s2.
```

## <a name="op_lt_eq"></a> operator&lt;=

Comprueba si el objeto de cadena del lado izquierdo del operador es menor o igual que el objeto de cadena del lado derecho.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator<=(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator<=(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator<=(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Una cadena de estilo C o un objeto del tipo `basic_string` que se va a comparar.

\ *derecha*
Una cadena de estilo C o un objeto del tipo `basic_string` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si el objeto de cadena del lado izquierdo del operador es lexicográficamente menor o igual que el objeto de cadena del lado derecho. En caso contrario, es **false**.

### <a name="remarks"></a>Comentarios

Una comparación lexicográfica entre cadenas las compara carácter por carácter hasta que:

- Encuentra dos caracteres correspondientes distintos y el resultado de la comparación se toma como el resultado de la comparación entre las cadenas.

- No encuentra ninguna desigualdad, pero una cadena tiene más caracteres que la otra y la cadena más corta se considera menor que la cadena más larga.

- No encuentra ninguna desigualdad y encuentra que las cadenas tienen el mismo número de caracteres, por lo que las cadenas son iguales.

### <a name="example"></a>Ejemplo

```cpp
// string_op_le.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "strict";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 <= s2 )
      cout << "The string s1 is less than or equal to "
           << "the string s2." << endl;
   else
      cout << "The string s1 is greater than "
           << "the string s2." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s1 <= s3 )
      cout << "The string s1 is less than or equal to "
           << "the string s3." << endl;
   else
      cout << "The string s1 is greater than "
           << "the string s3." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type  & right-side object of type basic_string
   if ( s2 <= s3 )
      cout << "The string s2 is less than or equal to "
           << "the string s3." << endl;
   else
      cout << "The string s2 is greater than "
           << "the string s3." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = strict.
The string s1 is less than or equal to the string s2.
The string s1 is less than or equal to the string s3.
The string s2 is greater than the string s3.
```

## <a name="op_lt_lt"></a> operator&lt;&lt;

Una función de plantilla que escribe una cadena en el flujo de salida.

```cpp
template <class CharType, class Traits, class Allocator>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& _Ostr,
    const basic_string<CharType, Traits, Allocator>& str);
```

### <a name="parameters"></a>Parámetros

@No__t_1 *_Ostr*
El flujo de salida en el que se escribe.

\ *Str*
La cadena que se especifica en el flujo de salida.

### <a name="return-value"></a>Valor devuelto

Escribe el valor de la cadena especificada en el flujo de salida *_Ostr*.

### <a name="remarks"></a>Comentarios

La función de plantilla sobrecarga **< <** para insertar un objeto *Str* de la plantilla de clase [basic_string](../standard-library/basic-string-class.md) en el *\_Ostr*de flujo. La función devuelve `_Ostr.write( str.c_str, str.size )` de forma efectiva.

## <a name="op_gt"></a>  operator&gt;

Comprueba si el objeto de cadena del lado izquierdo del operador es mayor que el objeto de cadena del lado derecho.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator>(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator>(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator>(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Una cadena de estilo C o un objeto del tipo `basic_string` que se va a comparar.

\ *derecha*
Una cadena de estilo C o un objeto del tipo `basic_string` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si el objeto de cadena del lado izquierdo del operador es lexicográficamente mayor que el objeto de cadena del lado derecho. En caso contrario, es **false**.

### <a name="remarks"></a>Comentarios

Una comparación lexicográfica entre cadenas las compara carácter por carácter hasta que:

- Encuentra dos caracteres correspondientes distintos y el resultado de la comparación se toma como el resultado de la comparación entre las cadenas.

- No encuentra ninguna desigualdad, pero una cadena tiene más caracteres que la otra y la cadena más corta se considera menor que la cadena más larga.

- No encuentra ninguna desigualdad y encuentra que las cadenas tienen el mismo número de caracteres, por lo que las cadenas son iguales.

### <a name="example"></a>Ejemplo

```cpp
// string_op_gt.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "stricture";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 > s2 )
      cout << "The string s1 is greater than "
           << "the string s2." << endl;
   else
      cout << "The string s1 is not greater than "
           << "the string s2." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s3 > s1 )
      cout << "The string s3 is greater than "
           << "the string s1." << endl;
   else
      cout << "The string s3 is not greater than "
           << "the string s1." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s2 > s3 )
      cout << "The string s2 is greater than "
           << "the string s3." << endl;
   else
      cout << "The string s2 is not greater than "
           << "the string s3." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = stricture.
The string s1 is not greater than the string s2.
The string s3 is greater than the string s1.
The string s2 is greater than the string s3.
```

## <a name="op_gt_eq"></a> operator&gt;=

Comprueba si el objeto de cadena del lado izquierdo del operador es mayor o igual que el objeto de cadena del lado derecho.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator>=(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator>=(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator>=(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Una cadena de estilo C o un objeto del tipo `basic_string` que se va a comparar.

\ *derecha*
Una cadena de estilo C o un objeto del tipo `basic_string` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si el objeto de cadena del lado izquierdo del operador es lexicográficamente mayor o igual que el objeto de cadena del lado derecho. En caso contrario, es **false**.

### <a name="remarks"></a>Comentarios

Una comparación lexicográfica entre cadenas las compara carácter por carácter hasta que:

- Encuentra dos caracteres correspondientes distintos y el resultado de la comparación se toma como el resultado de la comparación entre las cadenas.

- No encuentra ninguna desigualdad, pero una cadena tiene más caracteres que la otra y la cadena más corta se considera menor que la cadena más larga.

- No encuentra ninguna desigualdad y encuentra que las cadenas tienen el mismo número de caracteres, por lo que las cadenas son iguales.

### <a name="example"></a>Ejemplo

```cpp
// string_op_ge.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "stricture";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 >= s2 )
      cout << "The string s1 is greater than or equal to "
           << "the string s2." << endl;
   else
      cout << "The string s1 is less than "
           << "the string s2." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s3 >= s1 )
      cout << "The string s3 is greater than or equal to "
           << "the string s1." << endl;
   else
      cout << "The string s3 is less than "
           << "the string s1." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s2 >= s3 )
      cout << "The string s2 is greater than or equal to "
           << "the string s3." << endl;
   else
      cout << "The string s2 is less than "
           << "the string s3." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = stricture.
The string s1 is less than the string s2.
The string s3 is greater than or equal to the string s1.
The string s2 is greater than or equal to the string s3.
```

## <a name="op_gt_gt"></a> operator&gt;&gt;

Una función de plantilla que lee una cadena de un flujo de entrada.

```cpp
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& operator>>(
    basic_istream<CharType, Traits>& _Istr,
    basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

@No__t_1 *_Istr*
El flujo de entrada que se usa para extraer la secuencia.

\ *derecha*
La cadena que se extrae del flujo de entrada.

### <a name="return-value"></a>Valor devuelto

Lee el valor de la cadena especificada de *_Istr* y lo devuelve a la *derecha*.

### <a name="remarks"></a>Comentarios

El operador omite los espacios en blanco iniciales a menos que la marca `skipws` esté establecida. Lee todos los caracteres siguientes hasta que el siguiente carácter es un espacio en blanco o se alcanza el final del archivo.

La función de plantilla sobrecarga **> >** para reemplazar la secuencia controlada por *right* con una secuencia de elementos extraídos de la secuencia *_Istr*. La extracción se detiene:

- Al final del archivo.

- Después de que la función Extraiga `_Istr`. elementos de **ancho** , si el valor es distinto de cero.

Después de que la función Extraiga `_Istr`. elementos [max_size](../standard-library/basic-string-class.md#max_size) .

- Después de que la función extraiga un elemento *ch* para el que [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype**\< **CharType**> >( `getloc`). **is**( **ctype**\< **CharType**>:: **space**, *ch*) es true, en cuyo caso el carácter se vuelve a poner.

Si la función no extrae ningún elemento, llama a [setstate](../standard-library/basic-ios-class.md#setstate)(`ios_base::failbit`). En cualquier caso, llama a **istr**. **ancho**(0) y devuelve \* **this**.

### <a name="example"></a>Ejemplo

```cpp
// string_op_read_.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string c0;
   cout << "Input a string c0 ( try: Fibonacci numbers ): ";
   cin >> c0;
   cout << "The string entered is c0 = " << c0 << endl;
}
```

## <a name="see-also"></a>Vea también

[\<string>](../standard-library/string.md)
