---
title: allocator_traits (clase)
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator_traits
- memory/std::allocator_traits::propagate_on_container_move_assignment
- memory/std::allocator_traits::const_pointer
- memory/std::allocator_traits::propagate_on_container_swap
- memory/std::allocator_traits::propagate_on_container_copy_assignment
- memory/std::allocator_traits::difference_type
- memory/std::allocator_traits::allocator_type
- memory/std::allocator_traits::value_type
- memory/std::allocator_traits::pointer
- memory/std::allocator_traits::size_type
- memory/std::allocator_traits::const_void_pointer
- memory/std::allocator_traits::void_pointer
- memory/std::allocator_traits::allocate
- memory/std::allocator_traits::construct
- memory/std::allocator_traits::deallocate
- memory/std::allocator_traits::destroy
- memory/std::allocator_traits::max_size
- memory/std::allocator_traits::select_on_container_copy_construction
ms.assetid: 612974b8-b5d4-4668-82fb-824bff6821d6
helpviewer_keywords:
- std::allocator_traits [C++]
- std::allocator_traits [C++], propagate_on_container_move_assignment
- std::allocator_traits [C++], const_pointer
- std::allocator_traits [C++], propagate_on_container_swap
- std::allocator_traits [C++], propagate_on_container_copy_assignment
- std::allocator_traits [C++], difference_type
- std::allocator_traits [C++], allocator_type
- std::allocator_traits [C++], value_type
- std::allocator_traits [C++], pointer
- std::allocator_traits [C++], size_type
- std::allocator_traits [C++], const_void_pointer
- std::allocator_traits [C++], void_pointer
- std::allocator_traits [C++], allocate
- std::allocator_traits [C++], construct
- std::allocator_traits [C++], deallocate
- std::allocator_traits [C++], destroy
- std::allocator_traits [C++], max_size
- std::allocator_traits [C++], select_on_container_copy_construction
ms.openlocfilehash: 795fd17c2c5b3c7fa92e62088b8f2fd126094df9
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245887"
---
# <a name="allocatortraits-class"></a>allocator_traits (clase)

La clase de plantilla describe a un objeto que complementa a un *tipo de asignador*. Un tipo de asignador es cualquier tipo que describe a un objeto de asignador que se usa para administrar el almacenamiento asignado. Concretamente, para cualquier tipo de asignador `Alloc`, puede usar `allocator_traits<Alloc>` para determinar toda la información que necesita un contenedor habilitado como asignador. Para más información, vea [allocator (Clase)](../standard-library/allocator-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <class Alloc>
    class allocator_traits;
```

## <a name="members"></a>Miembros

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|`allocator_type`|Este tipo es un sinónimo del parámetro de plantilla `Alloc`.|
|`const_pointer`|Este tipo es `Alloc::const_pointer`, en caso de tener el formato correcto; en caso contrario, es `pointer_traits<pointer>::rebind<const value_type>`.|
|`const_void_pointer`|Este tipo es `Alloc::const_void_pointer`, en caso de tener el formato correcto; en caso contrario, es `pointer_traits<pointer>::rebind<const void>`.|
|`difference_type`|Este tipo es `Alloc::difference_type`, en caso de tener el formato correcto; en caso contrario, es `pointer_traits<pointer>::difference_type`.|
|`pointer`|Este tipo es `Alloc::pointer`, en caso de tener el formato correcto; en caso contrario, es `value_type *`.|
|`propagate_on_container_copy_assignment`|Este tipo es `Alloc::propagate_on_container_copy_assignment`, en caso de tener el formato correcto; en caso contrario, es `false_type`.|
|`propagate_on_container_move_assignment`|Este tipo es `Alloc::propagate_on_container_move_assignment`, en caso de tener el formato correcto; en caso contrario, es `false_type`. Si el tipo es verdadero, un contenedor habilitado como asignador copia su asignador almacenado en una asignación de movimiento.|
|`propagate_on_container_swap`|Este tipo es `Alloc::propagate_on_container_swap`, en caso de tener el formato correcto; en caso contrario, es `false_type`. Si el tipo es verdadero, un contenedor habilitado como asignador intercambia su asignador almacenado en un cambio.|
|`size_type`|Este tipo es `Alloc::size_type`, en caso de tener el formato correcto; en caso contrario, es `make_unsigned<difference_type>::type`.|
|`value_type`|Este tipo es un sinónimo de `Alloc::value_type`.|
|`void_pointer`|Este tipo es `Alloc::void_pointer`, en caso de tener el formato correcto; en caso contrario, es `pointer_traits<pointer>::rebind<void>`.|

### <a name="static-methods"></a>Métodos estáticos

Los siguientes métodos estáticos llaman al método correspondiente en un parámetro de asignador determinado.

|||
|-|-|
|[allocate](#allocate)|Método estático que asigna memoria mediante el parámetro de asignador determinado.|
|[construct](#construct)|Método estático que usa un asignador especificado para crear un objeto.|
|[deallocate](#deallocate)|Método estático que usa un asignador especificado para desasignar un número determinado de objetos.|
|[destroy](#destroy)|Método estático que usa un asignador especificado para llamar al destructor de un objeto sin desasignar su memoria.|
|[max_size](#max_size)|Método estático que usa un asignador especificado para determinar el número máximo de objetos que se pueden asignar.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Método estático que se llama a `select_on_container_copy_construction` en el asignador especificado.|

### <a name="allocate"></a> asignar

Método estático que asigna memoria mediante el parámetro de asignador determinado.

```cpp
static pointer allocate(Alloc& al, size_type count);

static pointer allocate(Alloc& al, size_type count,
    typename allocator_traits<void>::const_pointer* hint);
```

#### <a name="parameters"></a>Parámetros

*Al*\
Un objeto de asignador.

*recuento*\
Número de elementos que se van a asignar.

*Sugerencia*\
`const_pointer` que puede ayudar al objeto de asignador a satisfacer la solicitud de almacenamiento al buscar la dirección de un objeto asignado antes de la solicitud. Un puntero nulo se trata como si no hubiera sugerencia.

#### <a name="return-value"></a>Valor devuelto

Cada método devuelve un puntero al objeto asignado.

El primer método estático devuelve `al.allocate(count)`.

Si la expresión tiene el formato correcto, el segundo método devuelve `al.allocate(count, hint)`; de lo contrario, devuelve `al.allocate(count)`.

### <a name="construct"></a> Construcción

Método estático que usa un asignador especificado para crear un objeto.

```cpp
template <class Uty, class Types>
static void construct(Alloc& al, Uty* ptr, Types&&... args);
```

#### <a name="parameters"></a>Parámetros

*Al*\
Un objeto de asignador.

*PTR*\
Puntero a la ubicación donde se va a crear el objeto.

*args*\
Lista de argumentos que se pasa al constructor de objeto.

#### <a name="remarks"></a>Comentarios

Si la expresión tiene el formato correcto, la función miembro estática llama a `al.construct(ptr, args...)`; de lo contrario, se evalúa como `::new (static_cast<void *>(ptr)) Uty(std::forward<Types>(args)...)`.

### <a name="deallocate"></a> desasignar

Método estático que usa un asignador especificado para desasignar un número determinado de objetos.

```cpp
static void deallocate(Alloc al,
    pointer ptr,
    size_type count);
```

#### <a name="parameters"></a>Parámetros

*Al*\
Un objeto de asignador.

*PTR*\
Puntero a la ubicación inicial de los objetos que se van a desasignar.

*recuento*\
Número de objetos que se van a desasignar.

#### <a name="remarks"></a>Comentarios

Este método llama a `al.deallocate(ptr, count)`.

Este método no produce nada.

### <a name="destroy"></a> destruir

Método estático que usa un asignador especificado para llamar al destructor de un objeto sin desasignar su memoria.

```cpp
template <class Uty>
    static void destroy(Alloc& al, Uty* ptr);
```

#### <a name="parameters"></a>Parámetros

*Al*\
Un objeto de asignador.

*PTR*\
Puntero a la ubicación del objeto.

#### <a name="remarks"></a>Comentarios

Si esa expresión tiene el formato correcto, este método llama a `al.destroy(ptr)`; de lo contrario, se evalúa como `ptr->~Uty()`.

### <a name="max_size"></a> max_size

Método estático que usa un asignador especificado para determinar el número máximo de objetos que se pueden asignar.

```cpp
static size_type max_size(const Alloc& al);
```

#### <a name="parameters"></a>Parámetros

*Al*\
Un objeto de asignador.

#### <a name="remarks"></a>Comentarios

Si esa expresión tiene el formato correcto, este método devuelve `al.max_size()`; de lo contrario, devuelve `numeric_limits<size_type>::max()`.

### <a name="select_on_container_copy_construction"></a> select_on_container_copy_construction

Método estático que se llama a `select_on_container_copy_construction` en el asignador especificado.

```cpp
static Alloc select_on_container_copy_construction(const Alloc& al);
```

#### <a name="parameters"></a>Parámetros

*Al*\
Un objeto de asignador.

#### <a name="return-value"></a>Valor devuelto

Este método devuelve `al.select_on_container_copy_construction()`si tipo tiene el formato correcto; en caso contrario, devuelve *al*.

#### <a name="remarks"></a>Comentarios

Este método se usa para especificar un asignador cuando se ha aplicado el constructor de copias al contenedor asociado.
