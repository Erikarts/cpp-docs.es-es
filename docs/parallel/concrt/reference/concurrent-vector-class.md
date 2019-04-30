---
title: Clase concurrent_vector
ms.date: 11/04/2016
f1_keywords:
- concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::assign
- CONCURRENT_VECTOR/concurrency::concurrent_vector::at
- CONCURRENT_VECTOR/concurrency::concurrent_vector::back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::begin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::capacity
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::clear
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::empty
- CONCURRENT_VECTOR/concurrency::concurrent_vector::end
- CONCURRENT_VECTOR/concurrency::concurrent_vector::front
- CONCURRENT_VECTOR/concurrency::concurrent_vector::get_allocator
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_by
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_to_at_least
- CONCURRENT_VECTOR/concurrency::concurrent_vector::max_size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::push_back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::reserve
- CONCURRENT_VECTOR/concurrency::concurrent_vector::resize
- CONCURRENT_VECTOR/concurrency::concurrent_vector::shrink_to_fit
- CONCURRENT_VECTOR/concurrency::concurrent_vector::size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::swap
helpviewer_keywords:
- concurrent_vector class
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
ms.openlocfilehash: 7c2ca35239dfb3ce4c0f710259f54005ff9f3c94
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224212"
---
# <a name="concurrentvector-class"></a>Clase concurrent_vector

La clase `concurrent_vector` es una clase de contenedor de secuencia que permite el acceso aleatorio a cualquier elemento. Habilita las operaciones de anexión segura para simultaneidad, acceso de elemento, acceso de iterador e iterador transversal.

## <a name="syntax"></a>Sintaxis

```
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
private details::_Concurrent_vector_base_v4;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos de los elementos que se almacenará en el vector.

*_Ax*<br/>
El tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria para el vector simultáneo. Este argumento es opcional y el valor predeterminado es `allocator<T>`.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`allocator_type`|Tipo que representa la clase de asignador del vector simultáneo.|
|`const_iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer un `const` elemento en un vector simultáneo.|
|`const_pointer`|Un tipo que proporciona un puntero a un `const` elemento en un vector simultáneo.|
|`const_reference`|Un tipo que proporciona una referencia a un `const` elemento almacenado en un vector simultáneo para leer y realizar `const` operaciones.|
|`const_reverse_iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier `const` elemento del vector simultáneo.|
|`difference_type`|Un tipo que proporciona la distancia con signo entre dos elementos en un vector simultáneo.|
|`iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento en un vector simultáneo. Modificación de un elemento mediante el iterador no es segura para simultaneidad.|
|`pointer`|Un tipo que proporciona un puntero a un elemento en un vector simultáneo.|
|`reference`|Un tipo que proporciona una referencia a un elemento almacenado en un vector simultáneo.|
|`reverse_iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento en un vector invertido simultáneo. Modificación de un elemento mediante el iterador no es segura para simultaneidad.|
|`size_type`|Un tipo que cuenta el número de elementos de un vector simultáneo.|
|`value_type`|Tipo que representa el tipo de datos almacenados en un vector simultáneo.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[concurrent_vector](#ctor)|Sobrecargado. Construye un vector simultáneo.|
|[~ concurrent_vector (destructor)](#dtor)|Borra todos los elementos y se destruye este vector simultáneo.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[assign](#assign)|Sobrecargado. Borra los elementos del vector simultáneo y le asigna bien `_N` copias de `_Item`, o los valores especificados por el rango de iterador [ `_Begin`, `_End`). Este método no es seguro para la simultaneidad.|
|[at](#at)|Sobrecargado. Proporciona acceso al elemento en el índice especificado del vector simultáneo. Este método es seguro para simultaneidad para las operaciones de lectura así como al aumento del vector, siempre que se ha asegurado de que el valor `_Index` es menor que el tamaño del vector simultáneo.|
|[back](#back)|Sobrecargado. Devuelve una referencia o un `const` hacen referencia al último elemento del vector simultáneo. Si el vector simultáneo está vacía, el valor devuelto es indefinido. Este método es seguro para simultaneidad.|
|[begin](#begin)|Sobrecargado. Devuelve un iterador de tipo `iterator` o `const_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.|
|[capacity](#capacity)|Devuelve el tamaño máximo que puede alcanzar el vector simultáneo sin tener que asignar más memoria. Este método es seguro para simultaneidad.|
|[cbegin](#cbegin)|Devuelve un iterador de tipo `const_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.|
|[cend](#cend)|Devuelve un iterador de tipo `const_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.|
|[clear](#clear)|Borra todos los elementos del vector simultáneo. Este método no es seguro para la simultaneidad.|
|[crbegin](#crbegin)|Devuelve un iterador de tipo `const_reverse_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.|
|[crend](#crend)|Devuelve un iterador de tipo `const_reverse_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.|
|[empty](#empty)|Comprueba si el vector simultáneo está vacío en el momento en que se llama a este método. Este método es seguro para simultaneidad.|
|[end](#end)|Sobrecargado. Devuelve un iterador de tipo `iterator` o `const_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.|
|[front](#front)|Sobrecargado. Devuelve una referencia o un `const` referencia al primer elemento del vector simultáneo. Si el vector simultáneo está vacía, el valor devuelto es indefinido. Este método es seguro para simultaneidad.|
|[get_allocator](#get_allocator)|Devuelve una copia del asignador usado para construir el vector simultáneo. Este método es seguro para simultaneidad.|
|[grow_by](#grow_by)|Sobrecargado. Aumenta este vector simultáneo por `_Delta` elementos. Este método es seguro para simultaneidad.|
|[grow_to_at_least](#grow_to_at_least)|Aumenta este vector simultáneo hasta que tenga al menos `_N` elementos. Este método es seguro para simultaneidad.|
|[max_size](#max_size)|Devuelve el número máximo de elementos que puede contener el vector simultáneo. Este método es seguro para simultaneidad.|
|[push_back](#push_back)|Sobrecargado. Anexa el elemento especificado al final del vector simultáneo. Este método es seguro para simultaneidad.|
|[rbegin](#rbegin)|Sobrecargado. Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.|
|[rend](#rend)|Sobrecargado. Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.|
|[reserve](#reserve)|Asigna espacio suficiente para crecer el vector simultáneo al tamaño `_N` sin tener que asignar más memoria más adelante. Este método no es seguro para la simultaneidad.|
|[resize](#resize)|Sobrecargado. Cambia el tamaño del vector simultáneo al tamaño solicitado, eliminando o agregando elementos según sea necesario. Este método no es seguro para la simultaneidad.|
|[shrink_to_fit](#shrink_to_fit)|Compacta la representación interna del vector simultáneo para reducir la fragmentación y optimizar el uso de memoria. Este método no es seguro para la simultaneidad.|
|[size](#size)|Devuelve el número de elementos del vector simultáneo. Este método es seguro para simultaneidad.|
|[swap](#swap)|Intercambia el contenido de dos vectores simultáneos. Este método no es seguro para la simultaneidad.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator\[\]](#operator_at)|Sobrecargado. Proporciona acceso al elemento en el índice especificado del vector simultáneo. Este método es seguro para simultaneidad para las operaciones de lectura así como al aumento del vector, siempre que se haya asegurado de que el valor `_Index` es menor que el tamaño del vector simultáneo.|
|[operator=](#operator_eq)|Sobrecargado. Asigna el contenido de otro objeto `concurrent_vector` a este. Este método no es seguro para la simultaneidad.|

## <a name="remarks"></a>Comentarios

Para obtener información detallada sobre la `concurrent_vector` de clases, vea [contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_Concurrent_vector_base_v4`

`_Allocator_base`

`concurrent_vector`

## <a name="requirements"></a>Requisitos

**Encabezado:** concurrent_vector.h

**Espacio de nombres:** simultaneidad

##  <a name="assign"></a> Asignar

Borra los elementos del vector simultáneo y le asigna bien `_N` copias de `_Item`, o los valores especificados por el rango de iterador [ `_Begin`, `_End`). Este método no es seguro para la simultaneidad.

```
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>Parámetros

*_InputIterator*<br/>
El tipo del iterador especificado.

*_N*<br/>
El número de elementos que se va a copiar en el vector simultáneo.

*_Item*<br/>
Referencia a un valor utilizado para rellenar el vector simultáneo.

*_Begin*<br/>
Un iterador al primer elemento del intervalo de origen.

*_End*<br/>
Un iterador a uno más allá del último elemento del intervalo de origen.

### <a name="remarks"></a>Comentarios

`assign` no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso invoca métodos en el vector simultáneo al llamar a este método.

##  <a name="at"></a> en el

Proporciona acceso al elemento en el índice especificado del vector simultáneo. Este método es seguro para simultaneidad para las operaciones de lectura así como al aumento del vector, siempre que se ha asegurado de que el valor `_Index` es menor que el tamaño del vector simultáneo.

```
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
El índice del elemento que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Una referencia al elemento en el índice especificado.

### <a name="remarks"></a>Comentarios

La versión de la función `at` que devuelve una que no sean de `const` referencia no se puede usar para escribir simultáneamente en el elemento desde diferentes subprocesos. Debe usarse un objeto de sincronización diferentes para sincronizar simultáneas de lectura y las operaciones de escritura al mismo elemento de datos.

El método produce `out_of_range` si `_Index` es mayor o igual que el tamaño del vector simultáneo, y `range_error` si el índice es para una parte rota del vector. Para obtener más información sobre cómo un vector puede se dividirán, consulte [contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).

##  <a name="back"></a> Atrás

Devuelve una referencia o un `const` hacen referencia al último elemento del vector simultáneo. Si el vector simultáneo está vacía, el valor devuelto es indefinido. Este método es seguro para simultaneidad.

```
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia o una `const` hacen referencia al último elemento del vector simultáneo.

##  <a name="begin"></a> comenzar

Devuelve un iterador de tipo `iterator` o `const_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.

```
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `iterator` o `const_iterator` al principio del vector simultáneo.

##  <a name="capacity"></a> capacidad

Devuelve el tamaño máximo que puede alcanzar el vector simultáneo sin tener que asignar más memoria. Este método es seguro para simultaneidad.

```
size_type capacity() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño máximo que puede alcanzar el vector simultáneo sin tener que asignar más memoria.

### <a name="remarks"></a>Comentarios

A diferencia de una biblioteca estándar de C++ `vector`, un `concurrent_vector` objeto no mueve los elementos existentes si asigna más memoria.

##  <a name="cbegin"></a> cbegin

Devuelve un iterador de tipo `const_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.

```
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `const_iterator` al principio del vector simultáneo.

##  <a name="cend"></a> cend

Devuelve un iterador de tipo `const_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.

```
const_iterator cend() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `const_iterator` al final del vector simultáneo.

##  <a name="clear"></a> Borrar

Borra todos los elementos del vector simultáneo. Este método no es seguro para la simultaneidad.

```
void clear();
```

### <a name="remarks"></a>Comentarios

`clear` no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso invoca métodos en el vector simultáneo al llamar a este método. `clear` no se libera las matrices internas. Para liberar las matrices internas, llame a la función `shrink_to_fit` después `clear`.

##  <a name="ctor"></a> concurrent_vector

Construye un vector simultáneo.

```
explicit concurrent_vector(
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector(
    const concurrent_vector<T,
    M>& _Vector,
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    concurrent_vector&& _Vector);

explicit concurrent_vector(
    size_type _N);

concurrent_vector(
    size_type _N,
    const_reference _Item,
    const allocator_type& _Al = allocator_type());

template<class _InputIterator>
concurrent_vector(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());
```

### <a name="parameters"></a>Parámetros

*M*<br/>
El tipo de asignador del vector de origen.

*_InputIterator*<br/>
El tipo de iterador de entrada.

*_Al*<br/>
La clase de asignador que se usa con este objeto.

*_Vector*<br/>
El objeto de origen `concurrent_vector` del que copiar o mover elementos.

*_N*<br/>
Capacidad inicial del objeto `concurrent_vector`.

*_Item*<br/>
El valor de elementos en el objeto construido.

*_Begin*<br/>
Posición del primer elemento en el intervalo de elementos que se va a copiar.

*_End*<br/>
Posición del primer elemento más allá del intervalo de elementos que se va a copiar.

### <a name="remarks"></a>Comentarios

Todos los constructores almacenan un objeto de asignador `_Al` e inicializan el vector.

El primer constructor especifica un vector inicial vacío y especifica explícitamente el tipo de asignador. que se usará.

El segundo y tercer constructor especifican una copia del vector simultáneo `_Vector`.

El cuarto constructor especifica un movimiento del vector simultáneo `_Vector`.

El quinto constructor especifica una repetición de un número especificado ( `_N`) de elementos del valor predeterminado para la clase `T`.

El sexto constructor especifica una repetición de ( `_N`) elementos del valor `_Item`.

El último constructor especifica los valores proporcionados por el rango de iterador [ `_Begin`, `_End`).

##  <a name="dtor"></a> ~concurrent_vector

Borra todos los elementos y se destruye este vector simultáneo.

```
~concurrent_vector();
```

##  <a name="crbegin"></a> crbegin

Devuelve un iterador de tipo `const_reverse_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.

```
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `const_reverse_iterator` al principio del vector simultáneo.

##  <a name="crend"></a> crend

Devuelve un iterador de tipo `const_reverse_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.

```
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `const_reverse_iterator` al final del vector simultáneo.

##  <a name="empty"></a> vacío

Comprueba si el vector simultáneo está vacío en el momento en que se llama a este método. Este método es seguro para simultaneidad.

```
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si el vector está vacío en el momento en que se llamó a la función, **false** en caso contrario.

##  <a name="end"></a> final

Devuelve un iterador de tipo `iterator` o `const_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.

```
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `iterator` o `const_iterator` al final del vector simultáneo.

##  <a name="front"></a> front

Devuelve una referencia o un `const` referencia al primer elemento del vector simultáneo. Si el vector simultáneo está vacía, el valor devuelto es indefinido. Este método es seguro para simultaneidad.

```
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia o una `const` referencia al primer elemento del vector simultáneo.

##  <a name="get_allocator"></a> get_allocator

Devuelve una copia del asignador usado para construir el vector simultáneo. Este método es seguro para simultaneidad.

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valor devuelto

Una copia de asignador usado para construir el `concurrent_vector` objeto.

##  <a name="grow_by"></a> grow_by

Aumenta este vector simultáneo por `_Delta` elementos. Este método es seguro para simultaneidad.

```
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```

### <a name="parameters"></a>Parámetros

*_Delta*<br/>
El número de elementos que se va a anexar al objeto.

*_Item*<br/>
El valor para inicializar los nuevos elementos.

### <a name="return-value"></a>Valor devuelto

Un iterador al primer elemento anexado.

### <a name="remarks"></a>Comentarios

Si `_Item` no se especifica, los nuevos elementos están construido de forma predeterminada.

##  <a name="grow_to_at_least"></a> grow_to_at_least

Aumenta este vector simultáneo hasta que tenga al menos `_N` elementos. Este método es seguro para simultaneidad.

```
iterator grow_to_at_least(size_type _N);
```

### <a name="parameters"></a>Parámetros

*_N*<br/>
El nuevo tamaño mínimo para el `concurrent_vector` objeto.

### <a name="return-value"></a>Valor devuelto

Un iterador que apunta al principio de la secuencia anexada o al elemento en el índice `_N` si no se anexa ningún elemento.

##  <a name="max_size"></a> max_size

Devuelve el número máximo de elementos que puede contener el vector simultáneo. Este método es seguro para simultaneidad.

```
size_type max_size() const;
```

### <a name="return-value"></a>Valor devuelto

El número máximo de elementos de la `concurrent_vector` puede contener el objeto.

##  <a name="operator_eq"></a> operator=

Asigna el contenido de otro objeto `concurrent_vector` a este. Este método no es seguro para la simultaneidad.

```
concurrent_vector& operator= (
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector& operator= (
    const concurrent_vector<T, M>& _Vector);

concurrent_vector& operator= (
    concurrent_vector&& _Vector);
```

### <a name="parameters"></a>Parámetros

*M*<br/>
El tipo de asignador del vector de origen.

*_Vector*<br/>
Objeto `concurrent_vector` de origen.

### <a name="return-value"></a>Valor devuelto

Una referencia a este `concurrent_vector` objeto.

##  <a name="operator_at"></a> operator[]

Proporciona acceso al elemento en el índice especificado del vector simultáneo. Este método es seguro para simultaneidad para las operaciones de lectura así como al aumento del vector, siempre que se haya asegurado de que el valor `_Index` es menor que el tamaño del vector simultáneo.

```
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
El índice del elemento que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Una referencia al elemento en el índice especificado.

### <a name="remarks"></a>Comentarios

La versión de `operator []` que devuelve una que no sean de `const` referencia no se puede usar para escribir simultáneamente en el elemento desde diferentes subprocesos. Debe usarse un objeto de sincronización diferentes para sincronizar simultáneas de lectura y las operaciones de escritura al mismo elemento de datos.

No hay límites en la comprobación se realiza para asegurarse de que `_Index` es un índice válido en el vector simultáneo.

##  <a name="push_back"></a> push_back

Anexa el elemento especificado al final del vector simultáneo. Este método es seguro para simultaneidad.

```
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```

### <a name="parameters"></a>Parámetros

*_Item*<br/>
El valor se va a anexar.

### <a name="return-value"></a>Valor devuelto

Un iterador al elemento anexado.

##  <a name="rbegin"></a> rbegin

Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.

```
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al principio del vector simultáneo.

##  <a name="rend"></a> rend)

Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.

```
reverse_iterator rend();

const_reverse_iterator rend() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al final del vector simultáneo.

##  <a name="reserve"></a> reservar

Asigna espacio suficiente para crecer el vector simultáneo al tamaño `_N` sin tener que asignar más memoria más adelante. Este método no es seguro para la simultaneidad.

```
void reserve(size_type _N);
```

### <a name="parameters"></a>Parámetros

*_N*<br/>
El número de elementos para reservar espacio para.

### <a name="remarks"></a>Comentarios

`reserve` no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso invoca métodos en el vector simultáneo al llamar a este método. La capacidad del vector simultáneo después de que el método devuelve puede ser mayor que la reserva solicitada.

##  <a name="resize"></a> cambio de tamaño

Cambia el tamaño del vector simultáneo al tamaño solicitado, eliminando o agregando elementos según sea necesario. Este método no es seguro para la simultaneidad.

```
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```

### <a name="parameters"></a>Parámetros

*_N*<br/>
El nuevo tamaño de la concurrent_vector.

*val*<br/>
El valor de elementos nuevos añadido al vector si el nuevo tamaño es mayor que el tamaño original. Si se omite el valor, los nuevos objetos se asignan el valor predeterminado para su tipo.

### <a name="remarks"></a>Comentarios

Si el tamaño del contenedor es menor que el tamaño solicitado, se agregan elementos al vector hasta que alcance el tamaño solicitado. Si el tamaño del contenedor es mayor que el tamaño solicitado, se eliminan los elementos más cercanos al final del contenedor hasta que el contenedor alcanza el tamaño `_N`. Si el tamaño actual del contenedor es igual que el tamaño solicitado, no se lleva a cabo ninguna acción.

`resize` no es simultaneidad seguro. Debe asegurarse de que ningún otro subproceso invoca métodos en el vector simultáneo al llamar a este método.

##  <a name="shrink_to_fit"></a> shrink_to_fit

Compacta la representación interna del vector simultáneo para reducir la fragmentación y optimizar el uso de memoria. Este método no es seguro para la simultaneidad.

```
void shrink_to_fit();
```

### <a name="remarks"></a>Comentarios

Este método internamente volver a asignará los elementos de movimiento de memoria, lo que invalida todos los iteradores. `shrink_to_fit` no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso invoca métodos en el vector simultáneo al llamar a esta función.

##  <a name="size"></a> Tamaño

Devuelve el número de elementos del vector simultáneo. Este método es seguro para simultaneidad.

```
size_type size() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos en este `concurrent_vector` objeto.

### <a name="remarks"></a>Comentarios

Se garantiza que el tamaño devuelto incluya todos los elementos que se anexa mediante llamadas a la función `push_back`, aumente o disminuya de operaciones que se han completado antes de invocar este método. Sin embargo, también puede incluir elementos que se asignan, pero aún están en construcción mediante llamadas simultáneas a cualquiera de los métodos de crecimiento.

##  <a name="swap"></a> intercambio

Intercambia el contenido de dos vectores simultáneos. Este método no es seguro para la simultaneidad.

```
void swap(concurrent_vector& _Vector);
```

### <a name="parameters"></a>Parámetros

*_Vector*<br/>
La `concurrent_vector` objeto que se va a intercambiar el contenido.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md)
