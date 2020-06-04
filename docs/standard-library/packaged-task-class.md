---
title: packaged_task (Clase)
ms.date: 11/04/2016
f1_keywords:
- future/std::packaged_task
- future/std::packaged_task::packaged_task
- future/std::packaged_task::get_future
- future/std::packaged_task::make_ready_at_thread_exit
- future/std::packaged_task::reset
- future/std::packaged_task::swap
- future/std::packaged_task::valid
- future/std::packaged_task::operator()
- future/std::packaged_task::operator bool
ms.assetid: 0a72cbe3-f22a-4bfe-8e50-dcb268c98780
helpviewer_keywords:
- std::packaged_task [C++]
- std::packaged_task [C++], packaged_task
- std::packaged_task [C++], get_future
- std::packaged_task [C++], make_ready_at_thread_exit
- std::packaged_task [C++], reset
- std::packaged_task [C++], swap
- std::packaged_task [C++], valid
ms.openlocfilehash: eb171e09451e16e89716dfdc44ed6c611e2d2280
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372122"
---
# <a name="packaged_task-class"></a>packaged_task (Clase)

Describe un *proveedor asincrónico* que es un contenedor de llamadas cuya signatura de llamada es `Ty(ArgTypes...)`. Su *estado asincrónico asociado* contiene una copia de su objeto invocable además del resultado potencial.

## <a name="syntax"></a>Sintaxis

```cpp
template <class>
class packaged_task;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[packaged_task](#packaged_task)|Construye un objeto `packaged_task`.|
|[packaged_task::-packaged_task Destructor](#dtorpackaged_task_destructor)|Destruye un objeto `packaged_task` .|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[get_future](#get_future)|Devuelve un objeto [future](../standard-library/future-class.md) que tiene el mismo estado asincrónico asociado.|
|[make_ready_at_thread_exit](#make_ready_at_thread_exit)|Llama al objeto que se puede llamar que está almacenado en el estado asincrónico asociado y almacena el valor devuelto de forma atómica.|
|[Restablecer](#reset)|Reemplaza el estado asincrónico asociado.|
|[swap](#swap)|Intercambia el estado asincrónico asociado con el de un objeto especificado.|
|[Válido](#valid)|Especifica si el objeto tiene un estado asincrónico asociado.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[packaged_task::operador ?](#op_eq)|Transfiere un estado asincrónico asociado de un objeto especificado.|
|[packaged_task::operador()](#op_call)|Llama al objeto que se puede llamar que está almacenado en el estado asincrónico asociado, almacena el valor devuelto de forma atómica y establece el estado en *Listo*.|
|[packaged_task::operator bool](#op_bool)|Especifica si el objeto tiene un estado asincrónico asociado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<futuro>

**Espacio de nombres:** std

## <a name="packaged_taskget_future"></a><a name="get_future"></a>packaged_task::get_future

Devuelve un objeto de tipo `future<Ty>` que tiene el mismo *estado asincrónico asociado*.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Observaciones

Si el objeto `packaged_task` no tiene un estado asincrónico asociado, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un código de error de `no_state`.

Si ya se ha llamado a este método para un objeto `packaged_task` que tiene el mismo estado asincrónico asociado, el método produce un `future_error` que tiene un código de error de `future_already_retrieved`.

## <a name="packaged_taskmake_ready_at_thread_exit"></a><a name="make_ready_at_thread_exit"></a>packaged_task::make_ready_at_thread_exit

Llama al objeto que se puede llamar que está almacenado en el *estado asincrónico asociado* y almacena el valor devuelto de forma atómica.

```cpp
void make_ready_at_thread_exit(ArgTypes... args);
```

### <a name="remarks"></a>Observaciones

Si el objeto `packaged_task` no tiene un estado asincrónico asociado, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un código de error de `no_state`.

Si ya se ha llamado a este método o a [make_ready_at_thread_exit](#make_ready_at_thread_exit) para un objeto `packaged_task` que tiene el mismo estado asincrónico asociado, el método produce un `future_error` que tiene un código de error de `promise_already_satisfied`.

De otro modo, este operador llama a `INVOKE(fn, args..., Ty)`, donde *fn* es el objeto que se puede llamar que está almacenado en el estado asincrónico asociado. Cualquier valor devuelto se almacena de forma atómica como el resultado devuelto del estado asincrónico asociado.

A diferencia de [packaged_task::operator()](#op_call), el estado asincrónico asociado no se establece en `ready` hasta que no se hayan destruido todos los objetos locales de subprocesos del subproceso de llamada. Normalmente, los subprocesos que están bloqueados en el estado asincrónico asociado no se desbloquean hasta que no se sale del subproceso de llamada.

## <a name="packaged_taskoperator"></a><a name="op_eq"></a>packaged_task::operador ?

Transfiere el *estado asincrónico asociado* desde un objeto especificado.

```cpp
packaged_task& operator=(packaged_task&& Right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Objeto `packaged_task` .

### <a name="return-value"></a>Valor devuelto

`*this`

### <a name="remarks"></a>Observaciones

Después de la operación, *Right* ya no tiene un estado asincrónico asociado.

## <a name="packaged_taskoperator"></a><a name="op_call"></a>packaged_task::operador()

Llama al objeto invocable que se almacena en el *estado asincrónico asociado,* almacena atómicamente el valor devuelto y establece el estado en *ready*.

```cpp
void operator()(ArgTypes... args);
```

### <a name="remarks"></a>Observaciones

Si el objeto `packaged_task` no tiene un estado asincrónico asociado, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un código de error de `no_state`.

Si ya se ha llamado a este método o a [make_ready_at_thread_exit](#make_ready_at_thread_exit) para un objeto `packaged_task` que tiene el mismo estado asincrónico asociado, el método produce un `future_error` que tiene un código de error de `promise_already_satisfied`.

De otro modo, este operador llama a `INVOKE(fn, args..., Ty)`, donde *fn* es el objeto que se puede llamar que está almacenado en el estado asincrónico asociado. Cualquier valor devuelto se almacena de forma atómica como el resultado devuelto del estado asincrónico asociado, y el estado se establece en Listo. Como resultado, se desbloquean todos los subprocesos bloqueados en el estado asincrónico asociado.

## <a name="packaged_taskoperator-bool"></a><a name="op_bool"></a>packaged_task::operador bool

Especifica si el objeto tiene `associated asynchronous state`.

```cpp
operator bool() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

**true** si el objeto tiene un estado asincrónico asociado; de lo contrario, **false**.

## <a name="packaged_taskpackaged_task-constructor"></a><a name="packaged_task"></a>Constructor packaged_task::packaged_task

Construye un objeto `packaged_task`.

```cpp
packaged_task() noexcept;
packaged_task(packaged_task&& Right) noexcept;
template <class Fn>
   explicit packaged_task(Fn&& fn);

template <class Fn, class Alloc>
   explicit packaged_task(
      allocator_arg_t, const Alloc& alloc, Fn&& fn);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Objeto `packaged_task` .

*Alloc*\
Asignador de memoria. Para obtener más información, consulte [ \<>los asignadores ](../standard-library/allocators-header.md).

*Fn*\
Objeto de función.

### <a name="remarks"></a>Observaciones

El primer constructor `packaged_task` construye un objeto que no tiene ningún *estado asincrónico asociado.*

El segundo constructor `packaged_task` construye un objeto y transfiere el estado asincrónico asociado desde *Right*. Después de la operación, *Right* ya no tiene un estado asincrónico asociado.

El tercer constructor `packaged_task` construye un objeto que tiene una copia de *fn* almacenada en su estado asincrónico asociado.

El cuarto constructor `packaged_task` construye un objeto que tiene una copia de *fn* almacenada en su estado asincrónico asociado y se usa `alloc` para la asignación de memoria.

## <a name="packaged_taskpackaged_task-destructor"></a><a name="dtorpackaged_task_destructor"></a>packaged_task::-packaged_task Destructor

Destruye un objeto `packaged_task` .

```cpp
~packaged_task();
```

### <a name="remarks"></a>Observaciones

Si el *estado asincrónico asociado* no está *listo*, el destructor almacena una excepción [future_error](../standard-library/future-error-class.md) que tiene un código de error de `broken_promise` como el resultado en el estado asincrónico asociado, y cualquier subproceso que esté bloqueado en el estado asincrónico asociado se desbloquea.

## <a name="packaged_taskreset"></a><a name="reset"></a>packaged_task::reset

Usa un nuevo *estado asincrónico asociado* para reemplazar el estado asincrónico asociado existente.

```cpp
void reset();
```

### <a name="remarks"></a>Observaciones

De hecho, este método ejecuta `*this = packaged_task(move(fn))`, donde *fn* es el objeto de función que está almacenado en el estado asincrónico asociado de este objeto. Por lo tanto, el estado del objeto se borra, y puede llamarse a [get_future](#get_future), [operator()](#op_call) y [make_ready_at_thread_exit](#make_ready_at_thread_exit) como si estuviera en un objeto recién creado.

## <a name="packaged_taskswap"></a><a name="swap"></a>packaged_task::swap

Intercambia el estado asincrónico asociado con el de un objeto especificado.

```cpp
void swap(packaged_task& Right) noexcept;
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Objeto `packaged_task` .

## <a name="packaged_taskvalid"></a><a name="valid"></a>packaged_task::válido

Especifica si el objeto tiene `associated asynchronous state`.

```cpp
bool valid() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si el objeto tiene un estado asincrónico asociado; de lo contrario, **false**.

## <a name="see-also"></a>Consulte también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<>futuro](../standard-library/future.md)
