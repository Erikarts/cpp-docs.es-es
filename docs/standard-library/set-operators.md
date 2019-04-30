---
title: Operadores de &lt;set&gt;
ms.date: 03/27/2019
f1_keywords:
- set/std::operator!=
- set/std::operator&gt;
- set/std::operator&gt;=
- set/std::operator&lt;
- set/std::operator&lt;=
- set/std::operator==
ms.assetid: b4256ebc-c449-4688-95db-fced42d20d4d
helpviewer_keywords:
- std::operator!= (set)
- std::operator&gt; (set)
- std::operator&gt;= (set)
- std::operator&lt; (set)
- std::operator&lt;= (set)
- std::operator== (set)
ms.openlocfilehash: 16308623a845fdbf804f4e72f2159bc2a2dbc76b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412597"
---
# <a name="ltsetgt-operators"></a>Operadores de &lt;set&gt;

||||
|-|-|-|
|[operator!= (set)](#op_neq)|[operator&gt; (set)](#op_gt)|[operator&gt;= (set)](#op_gt_eq)|
|[operator&lt; (set)](#op_lt)|[operator&lt;= (set)](#op_lt_eq)|[operator== (set)](#op_eq_eq)|
|[operator!= (multiset)](#op_neq_multiset)|[operator&gt; (multiset)](#op_gt_multiset)|[operator&gt;= (multiset)](#op_gt_eq_multiset)|
|[operator&lt; (multiset)](#op_lt_multiset)|[operator&lt;= (multiset)](#op_lt_eq_multiset)|[operator== (multiset)](#op_eq_eq_multiset)|

## <a name="op_neq"></a>  operator!= (set)

Comprueba si el objeto de conjunto en el lado izquierdo del operador no es igual al objeto de conjunto del lado derecho.

```cpp
bool operator!=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto de tipo `set`.

*right*<br/>
Objeto de tipo `set`.

### <a name="return-value"></a>Valor devuelto

**true** si los conjuntos no son iguales, o bien **false** si son iguales.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de conjunto se basa en una comparación en pares de sus elementos. Dos conjuntos son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// set_op_ne.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 != s2 )
      cout << "The sets s1 and s2 are not equal." << endl;
   else
      cout << "The sets s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The sets s1 and s3 are not equal." << endl;
   else
      cout << "The sets s1 and s3 are equal." << endl;
}
/* Output:
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
*/
```

## <a name="op_lt"></a>  operator&lt; (set)

Comprueba si el objeto de conjunto en el lado izquierdo del operador es menor que el objeto de conjunto del lado derecho.

```cpp
bool operator<(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto de tipo `set`.

*right*<br/>
Objeto de tipo `set`.

### <a name="return-value"></a>Valor devuelto

Es **true** si el conjunto del lado izquierdo del operador es estrictamente menor que el conjunto del lado derecho del operador. En caso contrario, es **false**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de conjunto se basa en una comparación en pares de sus elementos. La relación de menor que entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// set_op_lt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 < s2 )
      cout << "The set s1 is less than the set s2." << endl;
   else
      cout << "The set s1 is not less than the set s2." << endl;

   if ( s1 < s3 )
      cout << "The set s1 is less than the set s3." << endl;
   else
      cout << "The set s1 is not less than the set s3." << endl;
}
/* Output:
The set s1 is less than the set s2.
The set s1 is not less than the set s3.
*/
```

## <a name="op_lt_eq"></a>  operator&lt;= (set)

Comprueba si el objeto de conjunto del lado izquierdo del operador es menor o igual que el objeto de conjunto del lado derecho.

```cpp
bool operator!<=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto de tipo `set`.

*right*<br/>
Objeto de tipo `set`.

### <a name="return-value"></a>Valor devuelto

Es **true** si el conjunto del lado izquierdo del operador es menor o igual que el conjunto del lado derecho del operador. En caso contrario, es **false**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de conjunto se basa en una comparación en pares de sus elementos. La relación de menor o igual entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// set_op_le.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 <= s2 )
      cout << "Set s1 is less than or equal to the set s2." << endl;
   else
      cout << "The set s1 is greater than the set s2." << endl;

   if ( s1 <= s3 )
      cout << "Set s1 is less than or equal to the set s3." << endl;
   else
      cout << "The set s1 is greater than the set s3." << endl;

   if ( s1 <= s4 )
      cout << "Set s1 is less than or equal to the set s4." << endl;
   else
      cout << "The set s1 is greater than the set s4." << endl;
}
/* Output:
Set s1 is less than or equal to the set s2.
The set s1 is greater than the set s3.
Set s1 is less than or equal to the set s4.
*/
```

## <a name="op_eq_eq"></a>  operator== (set)

Comprueba si el objeto de conjunto en el lado izquierdo del operador es igual al objeto de conjunto del lado derecho.

```cpp
bool operator!==(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto de tipo `set`.

*right*<br/>
Objeto de tipo `set`.

### <a name="return-value"></a>Valor devuelto

Es **true** si el conjunto del lado izquierdo del operador es igual que el conjunto del lado derecho del operador. En caso contrario, es **false**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de conjunto se basa en una comparación en pares de sus elementos. Dos conjuntos son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// set_op_eq.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The sets s1 and s2 are equal." << endl;
   else
      cout << "The sets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The sets s1 and s3 are equal." << endl;
   else
      cout << "The sets s1 and s3 are not equal." << endl;
}
/* Output:
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
*/
```

## <a name="op_gt"></a>  operator&gt; (set)

Comprueba si el objeto de conjunto en el lado izquierdo del operador es mayor que el objeto de conjunto del lado derecho.

```cpp
bool operator>(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto de tipo `set`.

*right*<br/>
Objeto de tipo `set`.

### <a name="return-value"></a>Valor devuelto

Es **true** si el conjunto del lado izquierdo del operador es mayor que el conjunto del lado derecho del operador. En caso contrario, es **false**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de conjunto se basa en una comparación en pares de sus elementos. La relación de mayor que entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// set_op_gt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 > s2 )
      cout << "The set s1 is greater than the set s2." << endl;
   else
      cout << "The set s1 is not greater than the set s2." << endl;

   if ( s1 > s3 )
      cout << "The set s1 is greater than the set s3." << endl;
   else
      cout << "The set s1 is not greater than the set s3." << endl;
}
/* Output:
The set s1 is not greater than the set s2.
The set s1 is greater than the set s3.
*/
```

## <a name="op_gt_eq"></a>  operator&gt;= (set)

Comprueba si el objeto de conjunto en el lado izquierdo del operador es mayor o igual que el objeto de conjunto del lado derecho.

```cpp
bool operator!>=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto de tipo `set`.

*right*<br/>
Objeto de tipo `set`.

### <a name="return-value"></a>Valor devuelto

Es **true** si el conjunto del lado izquierdo del operador es mayor o igual que el conjunto del lado derecho del operador. En caso contrario, es **false**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de conjunto se basa en una comparación en pares de sus elementos. La relación de mayor o igual entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// set_op_ge.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 >= s2 )
      cout << "Set s1 is greater than or equal to set s2." << endl;
   else
      cout << "The set s1 is less than the set s2." << endl;

   if ( s1 >= s3 )
      cout << "Set s1 is greater than or equal to set s3." << endl;
   else
      cout << "The set s1 is less than the set s3." << endl;

   if ( s1 >= s4 )
      cout << "Set s1 is greater than or equal to set s4." << endl;
   else
      cout << "The set s1 is less than the set s4." << endl;
}
/* Output:
The set s1 is less than the set s2.
Set s1 is greater than or equal to set s3.
Set s1 is greater than or equal to set s4.
*/
```

## <a name="op_neq_multiset"></a>  operator!= (multiset)

Comprueba si el objeto de conjunto múltiple a la izquierda del operador no es igual que el objeto de conjunto múltiple situado a la derecha del operador.

```cpp
bool operator!=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto de tipo `multiset`.

*right*<br/>
Objeto de tipo `multiset`.

### <a name="return-value"></a>Valor devuelto

**true** si los conjuntos o conjuntos múltiples no son iguales, o bien **false** si son iguales.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de conjunto múltiple se basa en una comparación en pares de sus elementos. Dos conjuntos o conjuntos múltiples son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// multiset_op_ne.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 != s2 )
      cout << "The multisets s1 and s2 are not equal." << endl;
   else
      cout << "The multisets s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The multisets s1 and s3 are not equal." << endl;
   else
      cout << "The multisets s1 and s3 are equal." << endl;
}
/* Output:
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
*/
```

## <a name="op_lt_multiset"></a>  operator&lt; (multiset)

Comprueba si el objeto de conjunto múltiple a la izquierda del operador es menor que el objeto de conjunto múltiple situado a la derecha del operador.

```cpp
bool operator<(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto de tipo `multiset`.

*right*<br/>
Objeto de tipo `multiset`.

### <a name="return-value"></a>Valor devuelto

Es **true** si el conjunto múltiple del lado izquierdo del operador es estrictamente menor que el conjunto múltiple del lado derecho del operador. En caso contrario, es **false**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de conjunto múltiple se basa en una comparación en pares de sus elementos. La relación de menor que entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// multiset_op_lt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 < s2 )
      cout << "The multiset s1 is less than "
           << "the multiset s2." << endl;
   else
      cout << "The multiset s1 is not less than "
           << "the multiset s2." << endl;

   if ( s1 < s3 )
      cout << "The multiset s1 is less than "
           << "the multiset s3." << endl;
   else
      cout << "The multiset s1 is not less than "
           << "the multiset s3." << endl;
}
/* Output:
The multiset s1 is less than the multiset s2.
The multiset s1 is not less than the multiset s3.
*/
```

## <a name="op_lt_eq_multiset"></a>  operator&lt;= (multiset)

Comprueba si el objeto de conjunto múltiple a la izquierda del operador es menor o igual que el objeto de conjunto múltiple situado a la derecha del operador.

```cpp
bool operator!<=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto de tipo `multiset`.

*right*<br/>
Objeto de tipo `multiset`.

### <a name="return-value"></a>Valor devuelto

Es **true** si el conjunto múltiple del lado izquierdo del operador es menor o igual que el conjunto múltiple del lado derecho del operador. En caso contrario, es **false**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de conjunto múltiple se basa en una comparación en pares de sus elementos. La relación de menor o igual entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// multiset_op_le.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 <= s2 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s2." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s2." << endl;

   if ( s1 <= s3 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s3." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s3." << endl;

   if ( s1 <= s4 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s4." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s4." << endl;
}
/* Output:
The multiset s1 is less than or equal to the multiset s2.
The multiset s1 is greater than the multiset s3.
The multiset s1 is less than or equal to the multiset s4.
*/
```

## <a name="op_eq_eq_multiset"></a>  operator== (multiset)

Comprueba si el objeto de conjunto múltiple a la izquierda del operador es igual que el objeto de conjunto múltiple situado a la derecha del operador.

```cpp
bool operator!==(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto de tipo `multiset`.

*right*<br/>
Objeto de tipo `multiset`.

### <a name="return-value"></a>Valor devuelto

Es **true** si el conjunto múltiple del lado izquierdo del operador es igual al conjunto múltiple del lado derecho del operador. En caso contrario, es **false**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de conjunto múltiple se basa en una comparación en pares de sus elementos. Dos conjuntos o conjuntos múltiples son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// multiset_op_eq.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The multisets s1 and s2 are equal." << endl;
   else
      cout << "The multisets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The multisets s1 and s3 are equal." << endl;
   else
      cout << "The multisets s1 and s3 are not equal." << endl;
}
/* Output:
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
*/
```

## <a name="op_gt_multiset"></a>  operator&gt; (multiset)

Comprueba si el objeto de conjunto múltiple a la izquierda del operador es mayor que el objeto de conjunto múltiple situado a la derecha del operador.

```cpp
bool operator>(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto de tipo `multiset`.

*right*<br/>
Objeto de tipo `multiset`.

### <a name="return-value"></a>Valor devuelto

Es **true** si el conjunto múltiple del lado izquierdo del operador es mayor que el conjunto múltiple del lado derecho del operador. En caso contrario, es **false**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de conjunto múltiple se basa en una comparación en pares de sus elementos. La relación de mayor que entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// multiset_op_gt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 > s2 )
      cout << "The multiset s1 is greater than "
           << "the multiset s2." << endl;
   else
      cout << "The multiset s1 is not greater "
           << "than the multiset s2." << endl;

   if ( s1 > s3 )
      cout << "The multiset s1 is greater than "
           << "the multiset s3." << endl;
   else
      cout << "The multiset s1 is not greater than "
           << "the multiset s3." << endl;
}
/* Output:
The multiset s1 is not greater than the multiset s2.
The multiset s1 is greater than the multiset s3.
*/
```

## <a name="op_gt_eq_multiset"></a>  operator&gt;= (multiset)

Comprueba si el objeto de conjunto múltiple a la izquierda del operador es mayor o igual que el objeto de conjunto múltiple situado a la derecha del operador.

```cpp
bool operator!>=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto de tipo `multiset`.

*right*<br/>
Objeto de tipo `multiset`.

### <a name="return-value"></a>Valor devuelto

Es **true** si el conjunto múltiple del lado izquierdo del operador es mayor o igual que el conjunto múltiple del lado derecho del operador. En caso contrario, es **false**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de conjunto múltiple se basa en una comparación en pares de sus elementos. La relación de mayor o igual entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// multiset_op_ge.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 >= s2 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s2." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s2." << endl;

   if ( s1 >= s3 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s3." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s3." << endl;

   if ( s1 >= s4 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s4." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s4." << endl;
}
/* Output:
The multiset s1 is less than the multiset s2.
The multiset s1 is greater than or equal to the multiset s3.
The multiset s1 is greater than or equal to the multiset s4.
*/
```

## <a name="see-also"></a>Vea también

[\<set>](../standard-library/set.md)<br/>
