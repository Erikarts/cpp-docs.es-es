---
title: allocator_variable_size (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_variable_size
- allocators/stdext::allocators::allocator_variable_size
- stdext::allocators::allocator_variable_size
helpviewer_keywords:
- stdext::allocator_variable_size
- stdext::allocators [C++], allocator_variable_size
ms.assetid: c3aa4105-ae45-4385-bbbe-9f23060478cb
ms.openlocfilehash: bf243089ee8f4e26930e183b007a108e38f444e3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458153"
---
# <a name="allocatorvariablesize-class"></a>allocator_variable_size (Clase)

Describe un objeto que administra la asignación de almacenamiento y la liberación de objetos de tipo *Type* mediante una memoria caché de tipo [cache_freelist](../standard-library/cache-freelist-class.md) con una longitud administrada por [max_variable_size](../standard-library/max-variable-size-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type>
class allocator_variable_size;
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*Type*|Tipo de elementos que asigna el asignador.|

## <a name="remarks"></a>Comentarios

La macro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) pasa esta clase como parámetro *Name* en la siguiente instrucción:`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_variable_size), SYNC_DEFAULT, allocator_variable_size);`

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)
