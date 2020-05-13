---
title: insert_iterator (Clase)
ms.date: 11/04/2016
f1_keywords:
- iterator/std::insert_iterator
- iterator/std::insert_iterator::container_type
- iterator/std::insert_iterator::reference
helpviewer_keywords:
- std::insert_iterator [C++]
- std::insert_iterator [C++], container_type
- std::insert_iterator [C++], reference
ms.assetid: d5d86405-872e-4e3b-9e68-c69a2b7e8221
ms.openlocfilehash: 2865db023425fa301ad5440a0dc8ed491213f33f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368057"
---
# <a name="insert_iterator-class"></a>insert_iterator (Clase)

Describe un adaptador de iterador que satisface los requisitos de un iterador de salida. Inserta, en lugar de sobrescribir, elementos en una secuencia y proporciona así la semántica que es diferente de la semántica que sobrescribe proporcionada por los iteradores de la secuencia de C++ y los contenedores asociativos. La clase `insert_iterator` se hace plantilla en el tipo de contenedor que se adapta.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Container>
class insert_iterator;
```

### <a name="parameters"></a>Parámetros

*Contenedor*\
Tipo de contenedor en el que un `insert_iterator` debe insertar los elementos.

## <a name="remarks"></a>Observaciones

El contenedor `Container` de tipo debe satisfacer los requisitos de un contenedor de tamaño variable `Container::iterator` y `Container::value_type` tener una `Container::iterator`función miembro de inserción de dos argumentos donde los parámetros son de tipo y que devuelve un tipo . Los contenedores asociativos ordenados y de secuencia de la biblioteca estándar de C++ cumplen estos requisitos y pueden adaptarse para su uso con `insert_iterator`. En los contenedores asociativos, el argumento de posición se trata como una sugerencia, algo que tiene potencial para mejorar o degradar el rendimiento, según la calidad de la sugerencia. Un `insert_iterator` debe inicializarse siempre con su contenedor.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[insert_iterator](#insert_iterator)|Construye `insert_iterator` que inserta un elemento en una posición especificada de un contenedor.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[container_type](#container_type)|Tipo que representa el contenedor en el que se va a crear una inserción general.|
|[Referencia](#reference)|Tipo que proporciona una referencia a un elemento de una secuencia controlada por el contenedor asociado.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operador*](#op_star)|Operador de desreferencia usado para implementar la expresión del iterador de salida * `i` = `x` para una inserción general.|
|[operador++](#op_add_add)|Incrementa el `insert_iterator` a la siguiente ubicación en la que puede almacenarse un valor.|
|[operador](#op_eq)|Operador de asignación usado para implementar la expresión del iterador de salida * `i` = `x` para una inserción general.|

## <a name="requirements"></a>Requisitos

**Encabezado** \<: iterador>

**Espacio de nombres:** std

## <a name="insert_iteratorcontainer_type"></a><a name="container_type"></a>insert_iterator::container_type

Tipo que representa el contenedor en el que se va a crear una inserción general.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla *Container*.

### <a name="example"></a>Ejemplo

```cpp
// insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   insert_iterator<list<int> >::container_type L2 = L1;
   inserter ( L2, L2.end ( ) ) = 20;
   inserter ( L2, L2.end ( ) ) = 10;
   inserter ( L2, L2.begin ( ) ) = 40;

   list <int>::iterator vIter;
   cout << "The list L2 is: ( ";
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L2 is: ( 40 20 10 ).
*/
```

## <a name="insert_iteratorinsert_iterator"></a><a name="insert_iterator"></a>insert_iterator::insert_iterator

Construye `insert_iterator` que inserta un elemento en una posición especificada de un contenedor.

```cpp
insert_iterator(Container& _Cont, typename Container::iterator _It);
```

### <a name="parameters"></a>Parámetros

*_Cont*\
Contenedor en el que `insert_iterator` va a insertar elementos.

*_It*\
Posición de la inserción.

### <a name="remarks"></a>Observaciones

Todos los contenedores tienen la función miembro insert a la que llama `insert_iterator`. En el caso de los contenedores asociativos, el parámetro de posición es simplemente una sugerencia. La función inserter ofrece una manera cómoda de insertar valores.

### <a name="example"></a>Ejemplo

```cpp
// insert_iterator_insert_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for (i = 1 ; i < 4 ; ++i )
   {
      L.push_back ( 10 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the member function to insert an element
   inserter ( L, L.begin ( ) ) = 2;

   // Alternatively, you may use the template version
   insert_iterator< list < int> > Iter(L, L.end ( ) );
*Iter = 300;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( 10 20 30 ).
After the insertions, the list L is:
( 2 10 20 30 300 ).
*/
```

## <a name="insert_iteratoroperator"></a><a name="op_star"></a>insert_iterator::operador*

Desreferencia el iterador de inserción que devuelve el elemento direccionado.

```cpp
insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Valor devuelto

La función miembro devuelve el valor del elemento al que se dirige.

### <a name="remarks"></a>Observaciones

Se utiliza para implementar la expresión = **value** ** \*** de iterador de salida Iter value . Si `Iter` es un iterador que direcciona un elemento de una secuencia, el = **value** ** \*** valor de Iter reemplaza ese elemento por valor y no cambia el número total de elementos de la secuencia.

### <a name="example"></a>Ejemplo

```cpp
// insert_iterator_op_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for (i = 0 ; i < 4 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The original list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   insert_iterator< list < int> > Iter(L, L.begin ( ) );
*Iter = 10;
*Iter = 20;
*Iter = 30;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The original list L is:
( 0 2 4 6 ).
After the insertions, the list L is:
( 10 20 30 0 2 4 6 ).
*/
```

## <a name="insert_iteratoroperator"></a><a name="op_add_add"></a>insert_iterator::operador++

Incrementa el `insert_iterator` a la siguiente ubicación en la que puede almacenarse un valor.

```cpp
insert_iterator<Container>& operator++();

insert_iterator<Container> operator++(int);
```

### <a name="parameters"></a>Parámetros

`insert_iterator` que dirige a la siguiente ubicación en la que se puede almacenar un valor.

### <a name="remarks"></a>Observaciones

Ambos operadores de incremento previo e incremento posterior devuelven el mismo resultado.

### <a name="example"></a>Ejemplo

```cpp
// insert_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 5 ; ++i )
   {
      vec.push_back (  i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is:\n ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   insert_iterator<vector<int> > ii ( vec, vec.begin ( ) );
*ii = 30;
   ii++;
*ii = 40;
   ii++;
*ii = 50;

   cout << "After the insertions, the vector vec becomes:\n ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The vector vec is:
( 1 2 3 4 ).
After the insertions, the vector vec becomes:
( 30 40 50 1 2 3 4 ).
*/
```

## <a name="insert_iteratoroperator"></a><a name="op_eq"></a>insert_iterator::operador ?

Inserta un valor en el contenedor y devuelve el iterador actualizado para apuntar al nuevo elemento.

```cpp
insert_iterator<Container>& operator=(
    typename Container::const_reference val,);

insert_iterator<Container>& operator=(
    typename Container::value_type&& val);
```

### <a name="parameters"></a>Parámetros

*Val*\
Valor que se va a asignar al contenedor.

### <a name="return-value"></a>Valor devuelto

Referencia al elemento insertado en el contenedor.

### <a name="remarks"></a>Observaciones

El primer operador miembro evalúa

`Iter = container->insert(Iter, val)`;

`++Iter;`

después, devuelve `*this`.

El segundo operador miembro evalúa

`Iter = container->insert(Iter, std::move(val));`

`++Iter;`

después, devuelve `*this`.

### <a name="example"></a>Ejemplo

```cpp
// insert_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for (i = 0 ; i < 4 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The original list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   insert_iterator< list < int> > Iter(L, L.begin ( ) );
*Iter = 10;
*Iter = 20;
*Iter = 30;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The original list L is:
( 0 2 4 6 ).
After the insertions, the list L is:
( 10 20 30 0 2 4 6 ).
*/
```

## <a name="insert_iteratorreference"></a><a name="reference"></a>insert_iterator::referencia

Tipo que proporciona una referencia a un elemento de una secuencia controlada por el contenedor asociado.

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>Observaciones

El tipo describe una referencia a un elemento de la secuencia controlada por el contenedor asociado.

### <a name="example"></a>Ejemplo

```cpp
// insert_iterator_container_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L;
   insert_iterator<list<int> > iivIter( L , L.begin ( ) );
*iivIter = 10;
*iivIter = 20;
*iivIter = 30;

   list<int>::iterator LIter;
   cout << "The list L is: ( ";
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++ )
      cout << *LIter << " ";
   cout << ")." << endl;

   insert_iterator<list<int> >::reference
        RefFirst = *(L.begin ( ));
   cout << "The first element in the list L is: "
        << RefFirst << "." << endl;
}
/* Output:
The list L is: ( 10 20 30 ).
The first element in the list L is: 10.
*/
```

## <a name="see-also"></a>Consulte también

[\<iterador>](../standard-library/iterator.md)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de la biblioteca estándar C++](../standard-library/cpp-standard-library-reference.md)
