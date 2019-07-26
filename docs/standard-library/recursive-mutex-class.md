---
title: recursive_mutex (Clase)
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_mutex
- mutex/std::recursive_mutex::recursive_mutex
- mutex/std::recursive_mutex::lock
- mutex/std::recursive_mutex::try_lock
- mutex/std::recursive_mutex::unlock
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
helpviewer_keywords:
- std::recursive_mutex [C++]
- std::recursive_mutex [C++], recursive_mutex
- std::recursive_mutex [C++], lock
- std::recursive_mutex [C++], try_lock
- std::recursive_mutex [C++], unlock
ms.openlocfilehash: 448b4d03e4d38dc45621cddab7d8f5d03b805968
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451683"
---
# <a name="recursivemutex-class"></a>recursive_mutex (Clase)

Representa un *tipo de exclusión mutua*. Al contrario que [mutex](../standard-library/mutex-class-stl.md), el comportamiento de las llamadas a métodos de bloqueo para objetos que ya están bloqueados está bien definido.

## <a name="syntax"></a>Sintaxis

```cpp
class recursive_mutex;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|Construye un objeto `recursive_mutex`.|
|[~recursive_mutex (Destructor)](#dtorrecursive_mutex_destructor)|Libera todos los recursos usados por el objeto `recursive_mutex`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[lock](#lock)|Bloquea el subproceso de llamada hasta que este obtiene la propiedad de la exclusión mutua.|
|[try_lock](#try_lock)|Intenta obtener la propiedad de la exclusión mutua sin bloquearla.|
|[unlock](#unlock)|Libera la propiedad de la exclusión mutua.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<exclusión mutua >

**Espacio de nombres:** std

## <a name="lock"></a> lock

Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Comentarios

Si el subproceso que realiza la llamada ya posee `mutex`, el método se devuelve inmediatamente, y el bloqueo anterior permanece vigente.

## <a name="recursive_mutex"></a> recursive_mutex

Crea un objeto `recursive_mutex` que no está bloqueado.

```cpp
recursive_mutex();
```

## <a name="dtorrecursive_mutex_destructor"></a> ~recursive_mutex

Libera todos los recursos usados por el objeto.

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>Comentarios

Si el objeto está bloqueado cuando se ejecuta el destructor, el comportamiento es indefinido.

## <a name="try_lock"></a> try_lock

Intenta obtener la propiedad de `mutex` sin bloquearlo.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Valor devuelto

**true** si el método obtiene correctamente la propiedad de `mutex` o si el subproceso que realiza la llamada ya posee el. `mutex**; otherwise, **false`

### <a name="remarks"></a>Comentarios

Si el subproceso que realiza la `mutex`llamada ya posee, la función devuelve inmediatamente **true**y el bloqueo anterior permanece en vigor.

## <a name="unlock"></a> unlock

Libera la propiedad de la exclusión mutua.

```cpp
void unlock();
```

### <a name="remarks"></a>Comentarios

Este método libera la propiedad de `mutex` solo después de que se llame tantas veces como se ha llamado a [lock](#lock) y [try_lock](#try_lock) correctamente en el objeto `recursive_mutex`.

Si el subproceso que realiza la llamada no posee `mutex`, el comportamiento es indefinido.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
