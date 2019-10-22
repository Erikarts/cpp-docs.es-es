---
title: move_iterator (Clase)
ms.date: 03/27/2019
f1_keywords:
- iterator/std::move_iterator
- iterator/std::move_iterator::iterator_type
- iterator/std::move_iterator::iterator_category
- iterator/std::move_iterator::value_type
- iterator/std::move_iterator::difference_type
- iterator/std::move_iterator::pointer
- iterator/std::move_iterator::reference
- iterator/std::move_iterator::base
helpviewer_keywords:
- std::move_iterator [C++]
- std::move_iterator [C++], iterator_type
- std::move_iterator [C++], iterator_category
- std::move_iterator [C++], value_type
- std::move_iterator [C++], difference_type
- std::move_iterator [C++], pointer
- std::move_iterator [C++], reference
- std::move_iterator [C++], base
ms.assetid: a5e5cdd8-a264-4c6b-9f9c-68b0e8edaab7
ms.openlocfilehash: 9e8334db52e05f4a61adb7256e87ed611f0d3ecb
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689280"
---
# <a name="move_iterator-class"></a>move_iterator (Clase)

La plantilla de clase `move_iterator` es un contenedor para un iterador. La plantilla move_iterator ofrece el mismo comportamiento que el iterador que contiene (almacena), con la excepción de que cambia el operador de desreferencia por una referencia rvalue y convierte una copia en un movimiento. Para obtener más información sobre rvalues, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="syntax"></a>Sintaxis

```cpp
class move_iterator;
```

## <a name="remarks"></a>Comentarios

La plantilla de clase describe un objeto que se comporta como un iterador salvo cuando se desreferencia. Almacena un iterador de acceso aleatorio de tipo `Iterator`, al que se tiene acceso mediante la función miembro `base()`. Todas las operaciones de `move_iterator` se realizan directamente en el iterador almacenado, con la excepción de que el resultado de `operator*` se convierte implícitamente en `value_type&&` para crear una referencia rvalue.

Un `move_iterator` puede llevar a cabo operaciones no definidas por el iterador contenedor. Estas operaciones no se deben usar.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[move_iterator](#move_iterator)|Constructor para los objetos de tipo `move_iterator`.|

### <a name="typedefs"></a>Definiciones de tipo

|Nombre de tipo|Descripción|
|-|-|
|[iterator_type](#iterator_type)|Sinónimo del parámetro de plantilla `RandomIterator`.|
|[iterator_category](#iterator_category)|Un sinónimo de una expresión **TypeName** más larga con el mismo nombre, `iterator_category` identifica las capacidades generales del iterador.|
|[value_type](#value_type)|Un sinónimo de una expresión **TypeName** más larga con el mismo nombre, `value_type` describe el tipo de los elementos del iterador.|
|[difference_type](#difference_type)|Un sinónimo de una expresión **TypeName** más larga con el mismo nombre, `difference_type` describe el tipo entero necesario para expresar los valores de diferencia entre los elementos.|
|[pointer](#pointer)|Sinónimo del parámetro de plantilla `RandomIterator`.|
|[reference](#reference)|Sinónimo de la referencia `rvalue` `value_type&&`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[base](#base)|La función miembro devuelve el iterador almacenado contenido en este `move_iterator`.|

### <a name="operators"></a>Operadores

|"??"|Descripción|
|-|-|
|[move_iterator::operator*](#op_star)|Devuelve `(reference)*base().`|
|[move_iterator::operator++](#op_add_add)|Incrementa el iterador almacenado. El comportamiento exacto depende de si se trata de una operación de incremento previo o posterior.|
|[move_iterator::operator--](#operator--)|Disminuye el iterador almacenado. El comportamiento exacto depende de si se trata de una operación de disminución previa o posterior.|
|[move_iterator::operator-&gt;](#op_arrow)|Devuelve `&**this`.|
|[move_iterator::operator-](#operator-)|Devuelve `move_iterator(*this) -=` restando primero el valor situado a la derecha de la posición actual.|
|[move_iterator::operator[]](#op_at)|Devuelve `(reference)*(*this + off)`. Permite especificar una posición de desplazamiento a partir de la base actual para obtener el valor que se encuentra en esa ubicación.|
|[move_iterator::operator+](#op_add)|Devuelve el valor `move_iterator(*this) +=`. Permite agregar una posición de desplazamiento a la base para obtener el valor que se encuentra en esa ubicación.|
|[move_iterator::operator+=](#op_add_eq)|Agrega el valor situado a la derecha del iterador almacenado y devuelve `*this`.|
|[move_iterator::operator-=](#operator-_eq)|Resta el valor situado a la derecha del iterador almacenado y devuelve `*this`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iterator>

**Espacio de nombres:** std

## <a name="base"></a> move_iterator::base

Devuelve el iterador almacenado para este `move_iterator`.

```cpp
RandomIterator base() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el iterador almacenado.

## <a name="difference_type"></a> move_iterator::difference_type

El tipo `difference_type` es un `move_iterator` `typedef` que se basa en el rasgo iterador `difference_type`, y se puede usar indistintamente.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type difference_type;
```

### <a name="remarks"></a>Comentarios

Tipo sinónimo del rasgo iterador `typename iterator_traits<RandomIterator>::pointer`.

## <a name="iterator_category"></a> move_iterator::iterator_category

El tipo `iterator_category` es un `move_iterator` `typedef` que se basa en el rasgo iterador `iterator_category`, y se puede usar indistintamente.

```cpp
typedef typename iterator_traits<RandomIterator>::iterator_category  iterator_category;
```

### <a name="remarks"></a>Comentarios

Tipo sinónimo del rasgo iterador `typename iterator_traits<RandomIterator>::iterator_category`.

## <a name="iterator_type"></a> move_iterator::iterator_type

El tipo `iterator_type` se basa en el parámetro de plantilla `RandomIterator` para la plantilla de clase `move_iterator` y se puede usar indistintamente en su lugar.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `RandomIterator`.

## <a name="move_iterator"></a> move_iterator::move_iterator

Construye un iterador de movimiento. Usa el parámetro como iterador almacenado.

```cpp
move_iterator();
explicit move_iterator(RandomIterator right);
template <class Type>
move_iterator(const move_iterator<Type>& right);
```

### <a name="parameters"></a>Parámetros

\ *derecha*
Iterador que se va a usar como iterador almacenado.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa el iterador almacenado con su constructor predeterminado. Los demás constructores inicializan el iterador almacenado con `base.base()`.

## <a name="op_add_eq"></a> move_iterator::operator+=

Agrega un desplazamiento al iterador almacenado, de modo que el iterador almacenado apunta al elemento en la nueva ubicación actual. Luego, el operador mueve el nuevo elemento actual.

```cpp
move_iterator& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Parámetros

@No__t_1 *_Off*
Un desplazamiento para agregar a la posición actual con el fin de determinar la nueva posición actual.

### <a name="return-value"></a>Valor devuelto

Devuelve el nuevo elemento actual.

### <a name="remarks"></a>Comentarios

El operador agrega *_Off* al iterador almacenado. Después devuelve `*this`.

## <a name="operator-_eq"></a> move_iterator::operator-=

Se desplaza por un número especificado de elementos anteriores. Este operador resta un desplazamiento al iterador almacenado.

```cpp
move_iterator& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Parámetros

### <a name="remarks"></a>Comentarios

El operador realiza la evaluación `*this += -_Off`. Después devuelve `*this`.

## <a name="op_add_add"></a> move_iterator::operator++

Incrementa el iterador almacenado que pertenece a este `move_iterator.`. El operador de postincremento accede al elemento actual. El operador de preincremento accede al siguiente elemento.

```cpp
move_iterator& operator++();
move_iterator operator++(int);
```

### <a name="parameters"></a>Parámetros

### <a name="remarks"></a>Comentarios

El primer operador (preincremento) incrementa el iterador almacenado. Después devuelve `*this`.

El segundo operador (postincremento) hace una copia de `*this` y realiza la evaluación `++*this`. Después devuelve la copia.

## <a name="op_add"></a> move_iterator::operator+

Devuelve la posición del iterador avanzada un número de elementos.

```cpp
move_iterator operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Parámetros

### <a name="remarks"></a>Comentarios

El operador devuelve `move_iterator(*this) +=` `_Off`.

## <a name="op_at"></a> move_iterator::operator[]

Permite el acceso del índice de matriz a elementos en el rango de `move iterator`.

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Parámetros

### <a name="remarks"></a>Comentarios

El operador devuelve `(reference)*(*this + _Off)`.

## <a name="operator--"></a> move_iterator::operator--

Los operadores de miembro de predecremento y postdecremento realizan una reducción en el iterador almacenado.

```cpp
move_iterator& operator--();
move_iterator operator--();
```

### <a name="parameters"></a>Parámetros

### <a name="remarks"></a>Comentarios

El primer operador de miembro (predecremento) disminuye el iterador almacenado. Después devuelve `*this`.

El segundo operador (postdecremento) hace una copia de `*this` y evalúa `--*this`. Después devuelve la copia.

## <a name="operator-"></a> move_iterator::operator-

Disminuye el iterador almacenado y devuelve el valor indicado.

```cpp
move_iterator operator-(difference_type _Off) const;
```

### <a name="parameters"></a>Parámetros

### <a name="remarks"></a>Comentarios

El operador devuelve `move_iterator(*this) -= _Off`.

## <a name="op_star"></a> move_iterator::operator*

Desreferencia el iterador almacenado y devuelve el valor. Se comporta como un `rvalue reference` y efectúa una asignación de movimiento. El operador transfiere el elemento actual fuera del iterador base. El elemento que sigue se convierte en el nuevo elemento actual.

```cpp
reference operator*() const;
```

### <a name="remarks"></a>Comentarios

El operador devuelve `(reference)*base()`.

## <a name="op_arrow"></a> move_iterator::operator-&gt;

Al igual que un `RandomIterator` `operator->` normal, proporciona acceso a los campos que pertenecen al elemento actual.

```cpp
pointer operator->() const;
```

### <a name="remarks"></a>Comentarios

El operador devuelve `&**this`.

## <a name="pointer"></a> move_iterator::pointer

El tipo `pointer` es un **typedef** basado en el iterador aleatorio `RandomIterator` para `move_iterator` y se puede usar indistintamente.

```cpp
typedef RandomIterator  pointer;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de `RandomIterator`.

## <a name="reference"></a> move_iterator::reference

El tipo `reference` es un **typedef** basado en `value_type&&` para `move_iterator` y se puede usar indistintamente con `value_type&&`.

```cpp
typedef value_type&& reference;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de `value_type&&`, que es una referencia rvalue.

## <a name="value_type"></a> move_iterator::value_type

El tipo `value_type` es un `move_iterator` `typedef` que se basa en el rasgo iterador `value_type`, y se puede usar indistintamente.

```cpp
typedef typename iterator_traits<RandomIterator>::value_type   value_type;
```

### <a name="remarks"></a>Comentarios

Tipo sinónimo del rasgo iterador `typename iterator_traits<RandomIterator>::value_type`.

## <a name="see-also"></a>Vea también

[\<iterator>](../standard-library/iterator.md)\
[Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)\
[Constructores de movimiento y operadores de asignación de movimiento (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
