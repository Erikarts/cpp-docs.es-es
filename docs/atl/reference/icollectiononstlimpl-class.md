---
title: ICollectionOnSTLImpl (clase)
ms.date: 11/04/2016
f1_keywords:
- ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl::get__NewEnum
- ATLCOM/ATL::ICollectionOnSTLImpl::getcount
- ATLCOM/ATL::ICollectionOnSTLImpl::get_Item
- ATLCOM/ATL::ICollectionOnSTLImpl::m_coll
helpviewer_keywords:
- ICollectionOnSTLImpl class
ms.assetid: 683c88b0-0d97-4779-a762-e493334ba7f9
ms.openlocfilehash: fc1e4988237cb839cca9421b56dbcdd04067059d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266463"
---
# <a name="icollectiononstlimpl-class"></a>ICollectionOnSTLImpl (clase)

Esta clase proporciona métodos utilizados por una clase de colección.

## <a name="syntax"></a>Sintaxis

```
template <class T, class CollType, class ItemType, class CopyItem, class EnumType>
class ICollectionOnSTLImpl : public T
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Una interfaz COM de la colección.

*CollType*<br/>
Una clase de contenedor de la biblioteca estándar de C++.

*ItemType*<br/>
El tipo de elemento que expone la interfaz del contenedor.

*CopyItem*<br/>
Un [Copiar directiva clase](../../atl/atl-copy-policy-classes.md).

*EnumType*<br/>
Un [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)-clase de enumerador compatible.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[ICollectionOnSTLImpl::get__NewEnum](#newenum)|Devuelve un objeto enumerador para la colección.|
|[ICollectionOnSTLImpl::getcount](#get_count)|Devuelve el número de elementos de la colección.|
|[ICollectionOnSTLImpl::get_Item](#get_item)|Devuelve el elemento solicitado de la colección.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[ICollectionOnSTLImpl::m_coll](#m_coll)|La colección.|

## <a name="remarks"></a>Comentarios

Esta clase proporciona la implementación de tres métodos de una interfaz de colección: [getcount](#get_count), [get_Item](#get_item), y [get__NewEnum](#newenum).

Para usar esta clase:

- Definir una interfaz de colección que desea implementar (o pedir prestado).

- Derive la clase de una especialización de `ICollectionOnSTLImpl` basadas en la interfaz de la colección.

- Utilice la clase derivada para implementar los métodos de la interfaz de colección no controlada por `ICollectionOnSTLImpl`.

> [!NOTE]
>  Si la interfaz de colección es una interfaz dual, derive la clase de [IDispatchImpl](../../atl/reference/idispatchimpl-class.md), pasando el `ICollectionOnSTLImpl` especialización como el primer parámetro de plantilla si desea que ATL para proporcionar la implementación de la `IDispatch` métodos.

- Agregar elementos a la [m_coll](#m_coll) miembro para rellenar la colección.

Para obtener más información y ejemplos, vea [colecciones y enumeradores ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`T`

`ICollectionOnSTLImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="get_count"></a>  ICollectionOnSTLImpl::getcount

Este método devuelve el número de elementos de la colección.

```
STDMETHOD(getcount)(long* pcount);
```

### <a name="parameters"></a>Parámetros

*pcount*<br/>
[out] El número de elementos de la colección.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="get_item"></a>  ICollectionOnSTLImpl::get_Item

Este método devuelve el elemento especificado de la colección.

```
STDMETHOD(get_Item)(long Index, ItemType* pvar);
```

### <a name="parameters"></a>Parámetros

*Index*<br/>
[in] El índice basado en 1 de un elemento de la colección.

*pvar*<br/>
[out] El elemento correspondiente a *índice*.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

El elemento se obtiene mediante la copia de los datos en la posición especificada en [m_coll](#m_coll) utilizando el método de copia de la [copiar clase directiva](../../atl/atl-copy-policy-classes.md) pasado como argumento de plantilla en el `ICollectionOnSTLImpl` especialización.

##  <a name="newenum"></a>  ICollectionOnSTLImpl::get__NewEnum

Devuelve un objeto enumerador para la colección.

```
STDMETHOD(get__NewEnum)(IUnknown** ppUnk);
```

### <a name="parameters"></a>Parámetros

*ppUnk*<br/>
[out] El **IUnknown** puntero de un objeto de enumerador recién creado.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

El enumerador recién creado mantiene un iterador en la colección original, `m_coll`, (por lo que se realiza ninguna copia) y mantiene una referencia COM en el objeto de colección para asegurarse de que la colección permanece activa mientras hay enumeradores pendientes.

##  <a name="m_coll"></a>  ICollectionOnSTLImpl::m_coll

Este miembro contiene los elementos representados por la colección.

```
CollType m_coll;
```

## <a name="see-also"></a>Vea también

[Ejemplo ATLCollections](../../visual-cpp-samples.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
