---
title: '&lt;allocators&gt; (macros)'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::ALLOCATOR_DECL
- allocators/std::CACHE_CHUNKLIST
- allocators/std::CACHE_FREELIST
- allocators/std::CACHE_SUBALLOC
- allocators/std::SYNC_DEFAULT
ms.assetid: 9cb5ee07-1ff9-4594-ae32-3c8c6efb511a
helpviewer_keywords:
- std::ALLOCATOR_DECL [C++]
- std::CACHE_CHUNKLIST [C++]
- std::CACHE_FREELIST [C++]
- std::CACHE_SUBALLOC [C++]
- std::SYNC_DEFAULT [C++]
ms.openlocfilehash: 5355661e370daf8826541c036f7301e5c25788d7
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424084"
---
# <a name="ltallocatorsgt-macros"></a>&lt;allocators&gt; (macros)

||||
|-|-|-|
|[ALLOCATOR_DECL](#allocator_decl)|[CACHE_CHUNKLIST](#cache_chunklist)|[CACHE_FREELIST](#cache_freelist)|
|[CACHE_SUBALLOC](#cache_suballoc)|[SYNC_DEFAULT](#sync_default)|

## <a name="allocator_decl"></a>  ALLOCATOR_DECL

Produce una plantilla de clase de asignador.

```cpp
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```

### <a name="remarks"></a>Observaciones

La macro produce una definición de plantilla `template <class Type> class name {.....}` y una especialización `template <> class name<void> {.....}` que, juntos, definen una plantilla de clase de asignador que usa el filtro de sincronización `sync` y una memoria caché de tipo `cache`.

En el caso de los compiladores que pueden compilar reenlaces, la definición de plantilla resultante tiene el siguiente aspecto:

```cpp
struct rebind
   {    /* convert a name<Type> to a name<Other> */
   typedef name<Other> other;
   };
```

En el caso de los compiladores que no pueden compilar reenlaces, la definición de plantilla resultante tiene el siguiente aspecto:

```cpp
template <class Type<class name
    : public stdext::allocators::allocator_base<Type,
    sync<stdext::allocators::rts_alloc<cache>>>
{
public:
    name() {}
    template <class Other>
    name(const name<Other>&) {}
    template <class Other>
    name& operator= (const name<Other>&)
    {
        return *this;
    }
};
```

## <a name="cache_chunklist"></a>  CACHE_CHUNKLIST

Produce `stdext::allocators::cache_chunklist<sizeof(Type)>`.

```cpp
#define CACHE_CHUNKLIST <cache_class>
```

### <a name="remarks"></a>Observaciones

## <a name="cache_freelist"></a>  CACHE_FREELIST

Produce `stdext::allocators::cache_freelist<sizeof(Type), max>`.

```cpp
#define CACHE_FREELIST(max) <cache_class>
```

### <a name="remarks"></a>Observaciones

## <a name="cache_suballoc"></a>  CACHE_SUBALLOC

Produce `stdext::allocators::cache_suballoc<sizeof(Type)>`.

```cpp
#define CACHE_SUBALLOC <cache_class>
```

### <a name="remarks"></a>Observaciones

## <a name="sync_default"></a>  SYNC_DEFAULT

Da como resultado un filtro de sincronización.

```cpp
#define SYNC_DEFAULT <sync_template>
```

### <a name="remarks"></a>Observaciones

Si un compilador admite la compilación de aplicaciones de un único subproceso y de varios, en el caso de las aplicaciones de un único subproceso la macro produce `stdext::allocators::sync_none`; en todos los demás casos, produce `stdext::allocators::sync_shared`.

## <a name="see-also"></a>Consulte también

[\<allocators>](../standard-library/allocators-header.md)
