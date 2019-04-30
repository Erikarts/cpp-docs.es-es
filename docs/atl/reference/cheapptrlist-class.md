---
title: CHeapPtrList (clase)
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
helpviewer_keywords:
- CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
ms.openlocfilehash: 84b4241dcad8d54321aea37c7055c6669ff3ca87
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245652"
---
# <a name="cheapptrlist-class"></a>CHeapPtrList (clase)

Esta clase proporciona métodos útiles al construir una lista de punteros del montón.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<typename E, class Allocator = ATL::CCRTAllocator>
class CHeapPtrList
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```

#### <a name="parameters"></a>Parámetros

*E*<br/>
El tipo de objeto que se almacenará en la clase de colección.

*Allocator*<br/>
La clase de asignación de memoria que utilice. El valor predeterminado es [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|El constructor.|

## <a name="remarks"></a>Comentarios

Esta clase proporciona un constructor y se deriva de los métodos de [CAtlList](../../atl/reference/catllist-class.md) y [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md) para facilitar la creación de un objeto de clase de colección almacenar punteros del montón.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CAtlList](../../atl/reference/catllist-class.md)

`CHeapPtrList`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

##  <a name="cheapptrlist"></a>  CHeapPtrList::CHeapPtrList

El constructor.

```
CHeapPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
El tamaño de bloque.

### <a name="remarks"></a>Comentarios

El tamaño de bloque es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Mayor tamaño de bloque reduce las llamadas a rutinas de asignación de memoria, pero usa más recursos.

## <a name="see-also"></a>Vea también

[CAtlList (clase)](../../atl/reference/catllist-class.md)<br/>
[CHeapPtr (clase)](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtrElementTraits (clase)](../../atl/reference/cheapptrelementtraits-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
