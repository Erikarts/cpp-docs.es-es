---
title: max_fixed_size (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_fixed_size
- allocators/stdext::max_fixed_size::allocated
- allocators/stdext::max_fixed_size::deallocated
- allocators/stdext::max_fixed_size::full
- allocators/stdext::max_fixed_size::released
- allocators/stdext::max_fixed_size::saved
helpviewer_keywords:
- stdext::max_fixed_size
- stdext::max_fixed_size [C++], allocated
- stdext::max_fixed_size [C++], deallocated
- stdext::max_fixed_size [C++], full
- stdext::max_fixed_size [C++], released
- stdext::max_fixed_size [C++], saved
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
ms.openlocfilehash: 08510ecc3b7469e8f88a61dcb0df28541e170892
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412961"
---
# <a name="maxfixedsize-class"></a>max_fixed_size (Clase)

Describe un objeto de [clase máxima](../standard-library/allocators-header.md) que limita un objeto [freelist](../standard-library/freelist-class.md) a una longitud máxima fija.

## <a name="syntax"></a>Sintaxis

```cpp
template <std::size_t Max>
class max_fixed_size
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Max*|Clase máxima que determina el número máximo de elementos que se van a almacenar en `freelist`.|

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[max_fixed_size](#max_fixed_size)|Construye un objeto de tipo `max_fixed_size`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[allocated](#allocated)|Aumenta el número de bloques de memoria asignada.|
|[deallocated](#deallocated)|Reduce el número de bloques de memoria asignada.|
|[full](#full)|Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.|
|[released](#released)|Reduce el número de bloques de memoria de la lista libre.|
|[saved](#saved)|Aumenta el número de bloques de memoria de la lista libre.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="allocated"></a>  max_fixed_size::allocated

Aumenta el número de bloques de memoria asignada.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*_Nx*|Valor de incremento.|

### <a name="remarks"></a>Comentarios

La función miembro no hace nada. Esta función miembro se llama después de cada llamada correcta por `cache_freelist::allocate` al operador **nuevo**. El argumento *_Nx* es el número de bloques de memoria del fragmento asignado por el operador **nuevo**.

## <a name="deallocated"></a>  max_fixed_size::deallocated

Reduce el número de bloques de memoria asignada.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*_Nx*|Valor de incremento.|

### <a name="remarks"></a>Comentarios

La función miembro no hace nada. Se llama a esta función miembro después de cada llamada por `cache_freelist::deallocate` al operador **eliminar**. El argumento *_Nx* es el número de bloques de memoria del fragmento desasignado por el operador **eliminar**.

## <a name="full"></a>  max_fixed_size::full

Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.

```cpp
bool full();
```

### <a name="return-value"></a>Valor devuelto

**True** si `Max <= _Nblocks`; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Se llama a esta función miembro mediante `cache_freelist::deallocate`. Si la llamada devuelve **true**, `deallocate` coloca el bloque de memoria en la lista libre; si devuelve false, `deallocate` llama al operador **eliminar** desasignar el bloque.

## <a name="max_fixed_size"></a>  max_fixed_size::max_fixed_size

Construye un objeto de tipo `max_fixed_size`.

```cpp
max_fixed_size();
```

### <a name="remarks"></a>Comentarios

Este constructor inicializa el valor almacenado `_Nblocks` en cero.

## <a name="released"></a>  max_fixed_size::released

Reduce el número de bloques de memoria de la lista libre.

```cpp
void released();
```

### <a name="remarks"></a>Comentarios

Disminuye el valor almacenado `_Nblocks`. La función miembro `released` de la [clase máxima](../standard-library/allocators-header.md) actual se llama mediante `cache_freelist::allocate` cada vez que quita un bloque de memoria de la lista libre.

## <a name="saved"></a>  max_fixed_size::saved

Aumenta el número de bloques de memoria de la lista libre.

```cpp
void saved();
```

### <a name="remarks"></a>Comentarios

Esta función miembro aumenta el valor almacenado `_Nblocks`. Esta función miembro se llama mediante `cache_freelist::deallocate` cada vez que coloca un bloque de memoria en la lista libre.

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)<br/>
