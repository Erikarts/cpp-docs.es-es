---
title: stack (Clase)
ms.date: 11/04/2016
f1_keywords:
- stack/std::stack::container_type
- stack/std::stack::size_type
- stack/std::stack::value_type
- stack/std::stack::empty
- stack/std::stack::pop
- stack/std::stack::push
- stack/std::stack::size
- stack/std::stack::top
helpviewer_keywords:
- std::stack [C++], container_type
- std::stack [C++], size_type
- std::stack [C++], value_type
- std::stack [C++], empty
- std::stack [C++], pop
- std::stack [C++], push
- std::stack [C++], size
- std::stack [C++], top
ms.assetid: 02151c1e-eab0-41b8-be94-a839ead78ecf
ms.openlocfilehash: d282d3ea54528b422509f4259e2d9a191f88e091
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453786"
---
# <a name="stack-class"></a>stack (Clase)

Clase de adaptador de contenedor de plantilla que proporciona una restricción de la funcionalidad que limita el acceso al elemento agregado más recientemente a algún tipo de contenedor subyacente. La clase de pila se usa cuando es importante tener claro que solo se están realizando operaciones de pila en el contenedor.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type, class Container= deque <Type>>
class stack
```

### <a name="parameters"></a>Parámetros

*Automáticamente*\
Tipo de datos de los elementos que se van a almacenar en la pila.

*Contenedor*\
Tipo del contenedor subyacente que se usa para implementar la pila. El valor predeterminado es la clase `deque` *\<Type>* .

## <a name="remarks"></a>Comentarios

Los elementos de la `Type` clase estipulados en el primer parámetro de plantilla de un objeto de pila son sinónimos de [value_type](#value_type) y deben coincidir con el tipo de elemento `Container` de la clase contenedora subyacente estipulada por la segunda plantilla. parámetro. `Type` Debe ser asignable, para que sea posible copiar objetos de ese tipo y asignar valores a variables de ese tipo.

Entre las clases contenedoras subyacentes adecuadas para la pila se incluyen [deque](../standard-library/deque-class.md), [List Class](../standard-library/list-class.md)y [Vector Class](../standard-library/vector-class.md), o cualquier otro contenedor de `back`secuencias `push_back`que admita `pop_back`las operaciones de, y. La clase de contenedor subyacente se encapsula dentro del adaptador de contenedor, que solo expone el conjunto limitado de las funciones miembro de contenedor de secuencias como una interfaz pública.

Los objetos de pila son comparables por igualdad si y solo si `Type` los elementos de la clase son comparables de igualdad y son menos que comparables si y solo si los elementos de la clase `Type` son menos comparables.

- La clase de pila es compatible con una estructura de datos LIFO (el último en entrar es el primero en salir). Un buen símil sería una pila de platos. Solo se pueden insertar e inspeccionar elementos (platos) en la parte superior de la pila, que es el último elemento al final del contenedor base, y solo se pueden quitar de ahí. La restricción de acceder únicamente al elemento superior es el motivo por el que se usa la clase stack.

- La [clase queue](../standard-library/queue-class.md) es compatible con una estructura de datos FIFO (el primero en entrar es el primero en salir). Un buen símil sería el de personas que hacen cola en un banco. Se pueden agregar elementos (personas) a la parte posterior de la línea y quitarlos de la parte delantera de la línea. Se puede inspeccionar tanto la parte delantera como trasera de una línea. La restricción de acceder únicamente a los elementos delanteros y traseros de esta manera es el motivo por el que se usa la clase queue.

- La [clase priority_queue](../standard-library/priority-queue-class.md) ordena sus elementos de tal modo que el elemento más grande siempre esté en la parte superior. Admite la inserción de un elemento y la inspección y eliminación del elemento superior. Un buen símil sería el de personas alineadas y organizadas por edad, altura o cualquier otro criterio.

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|||
|-|-|
|[stack](#stack)|Construye una `stack` que está vacía o que es una copia de un objeto contenedor base.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[container_type](#container_type)|Tipo que proporciona el contenedor base que debe adaptarse mediante una `stack`.|
|[size_type](#size_type)|Tipo entero sin signo que puede representar el número de elementos de un `stack`.|
|[value_type](#value_type)|Tipo que representa el tipo de objeto almacenado como elemento en una `stack`.|

### <a name="functions"></a>Funciones

|||
|-|-|
|[empty](#empty)|Comprueba si la `stack` está vacía.|
|[pop](#pop)|Quita el elemento de la parte superior de la `stack`.|
|[push](#push)|Agrega un elemento a la parte superior de la `stack`.|
|[size](#size)|Devuelve el número de elementos de `stack`.|
|[top](#top)|Devuelve una referencia a un elemento en la parte superior de la `stack`.|

## <a name="container_type"></a>container_type

Un tipo que proporciona el contenedor base que debe adaptarse.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `Container`. Las tres clases de contenedor de secuencias de la biblioteca estándar de C++: la clase vector, la clase list y la clase deque (la predeterminada), cumplen los requisitos para usarse como el contenedor base para un objeto de pila. También pueden usarse tipos definidos por el usuario que cumplan estos requisitos.

Para más información sobre `Container`, vea la sección Comentarios del tema [stack (Clase)](../standard-library/stack-class.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [stack::stack](#stack) para obtener un ejemplo de cómo declarar y usar `container_type`.

## <a name="empty"></a>vacía

Comprueba si una pila está vacía.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si la pila está vacía, o bien **false** si no lo está.

### <a name="example"></a>Ejemplo

```cpp
// stack_empty.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   // Declares stacks with default deque base container
   stack <int> s1, s2;

   s1.push( 1 );

   if ( s1.empty( ) )
      cout << "The stack s1 is empty." << endl;
   else
      cout << "The stack s1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The stack s2 is empty." << endl;
   else
      cout << "The stack s2 is not empty." << endl;
}
```

```Output
The stack s1 is not empty.
The stack s2 is empty.
```

## <a name="pop"></a>emergente

Quita el elemento de la parte superior de la pila.

```cpp
void pop();
```

### <a name="remarks"></a>Comentarios

La pila no debe estar vacía para aplicar la función miembro. La parte superior de la pila es la posición ocupada por el elemento agregado más recientemente y es el último elemento al final del contenedor.

### <a name="example"></a>Ejemplo

```cpp
// stack_pop.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1, s2;

   s1.push( 10 );
   s1.push( 20 );
   s1.push( 30 );

   stack <int>::size_type i;
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   i = s1.top( );
   cout << "The element at the top of the stack is "
        << i << "." << endl;

   s1.pop( );

   i = s1.size( );
   cout << "After a pop, the stack length is "
        << i << "." << endl;

   i = s1.top( );
   cout << "After a pop, the element at the top of the stack is "
        << i << "." << endl;
}
```

```Output
The stack length is 3.
The element at the top of the stack is 30.
After a pop, the stack length is 2.
After a pop, the element at the top of the stack is 20.
```

## <a name="push"></a>enviar

Agrega un elemento a la parte superior de la pila.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parámetros

*Val*\
El elemento agregado a la parte superior de la pila.

### <a name="remarks"></a>Comentarios

La parte superior de la pila es la posición ocupada por el elemento agregado más recientemente y es el último elemento al final del contenedor.

### <a name="example"></a>Ejemplo

```cpp
// stack_push.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1;

   s1.push( 10 );
   s1.push( 20 );
   s1.push( 30 );

   stack <int>::size_type i;
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   i = s1.top( );
   cout << "The element at the top of the stack is "
        << i << "." << endl;
}
```

```Output
The stack length is 3.
The element at the top of the stack is 30.
```

## <a name="size"></a>ajusta

Devuelve el número de elementos de la pila.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud actual de la pila.

### <a name="example"></a>Ejemplo

```cpp
// stack_size.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1, s2;
   stack <int>::size_type i;

   s1.push( 1 );
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   s1.push( 2 );
   i = s1.size( );
   cout << "The stack length is now " << i << "." << endl;
}
```

```Output
The stack length is 1.
The stack length is now 2.
```

## <a name="size_type"></a>size_type

Un tipo entero sin signo que puede representar el número de elementos de una pila.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de `size_type` del contenedor base adaptado por la pila.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [size](#size) para obtener un ejemplo de cómo declarar y usar `size_type`.

## <a name="stack"></a>StackPanel

Construye una pila que está vacía o que es una copia de una clase contenedora base.

```cpp
stack();

explicit stack(const container_type& right);
```

### <a name="parameters"></a>Parámetros

*correcta*\
El contenedor del que la pila construida va a ser una copia.

### <a name="example"></a>Ejemplo

```cpp
// stack_stack.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stack with default deque base container
   stack <char> dsc1;

   //Explicitly declares a stack with deque base container
   stack <char, deque<char> > dsc2;

   // Declares a stack with vector base containers
   stack <int, vector<int> > vsi1;

   // Declares a stack with list base container
   stack <int, list<int> > lsi;

   // The second member function copies elements from a container
   vector<int> v1;
   v1.push_back( 1 );
   stack <int, vector<int> > vsi2( v1 );
   cout << "The element at the top of stack vsi2 is "
        << vsi2.top( ) << "." << endl;
}
```

```Output
The element at the top of stack vsi2 is 1.
```

## <a name="top"></a>Arriba

Devuelve una referencia a un elemento en la parte superior de la pila.

```cpp
reference top();

const_reference top() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia al último elemento del contenedor en la parte superior de la pila.

### <a name="remarks"></a>Comentarios

La pila no debe estar vacía para aplicar la función miembro. La parte superior de la pila es la posición ocupada por el elemento agregado más recientemente y es el último elemento al final del contenedor.

Si el valor devuelto `top` de se asigna a `const_reference`un, el objeto de pila no se puede modificar. Si el valor devuelto `top` de se asigna a `reference`un, el objeto de pila se puede modificar.

### <a name="example"></a>Ejemplo

```cpp
// stack_top.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1;

   s1.push( 1 );
   s1.push( 2 );

   int& i = s1.top( );
   const int& ii = s1.top( );

   cout << "The top integer of the stack s1 is "
        << i << "." << endl;
   i--;
   cout << "The next integer down is "<< ii << "." << endl;
}
```

```Output
The top integer of the stack s1 is 2.
The next integer down is 1.
```

## <a name="value_type"></a>value_type

Un tipo que representa el tipo de objeto almacenado como elemento en una pila.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de `value_type` del contenedor base adaptado por la pila.

### <a name="example"></a>Ejemplo

```cpp
// stack_value_type.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   // Declares stacks with default deque base container
   stack<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   stack<int> s1;
   s1.push( AnInt );
   cout << "The element at the top of the stack is "
        << s1.top( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the top of the stack is 69.
```

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
