---
title: IColumnsInfoImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL.IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl
- IColumnsInfoImpl
- ATL.IColumnsInfoImpl
- ATL::IColumnsInfoImpl<T>
- GetColumnInfo
- ATL::IColumnsInfoImpl::GetColumnInfo
- ATL.IColumnsInfoImpl.GetColumnInfo
- ATL::IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl::GetColumnInfo
- IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl.GetColumnInfo
- IColumnsInfoImpl<T>::MapColumnIDs
- MapColumnIDs
- ATL::IColumnsInfoImpl::MapColumnIDs
- IColumnsInfoImpl.MapColumnIDs
- ATL::IColumnsInfoImpl<T>::MapColumnIDs
- IColumnsInfoImpl::MapColumnIDs
- ATL.IColumnsInfoImpl<T>.MapColumnIDs
- ATL.IColumnsInfoImpl.MapColumnIDs
helpviewer_keywords:
- IColumnsInfoImpl class
- GetColumnInfo method
- MapColumnIDs method
ms.assetid: ba74c1c5-2eda-4452-8b57-84919fa0d066
ms.openlocfilehash: 802c105e7795cdce604e72983f4fda549abcd5fb
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418274"
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl (Clase)

Proporciona una implementación de la [IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85)) interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
class ATL_NO_VTABLE IColumnsInfoImpl :
   public IColumnsInfo, 
   public CDBIDOps
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IColumnsInfoImpl`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|Devuelve los metadatos de columna necesarios para la mayoría de los consumidores.|
|[MapColumnIDs](#mapcolumnids)|Devuelve una matriz de ordinales de las columnas en un conjunto de filas que se identifican mediante los identificadores de columna especificado.|

## <a name="remarks"></a>Comentarios

Una interfaz obligatoria en los conjuntos de filas y los comandos. Para modificar el comportamiento de su proveedor `IColumnsInfo` implementación, deberá modificar la asignación de columna del proveedor.

## <a name="getcolumninfo"></a> IColumnsInfoImpl::GetColumnInfo

Devuelve los metadatos de columna necesarios para la mayoría de los consumidores.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (GetColumnInfo)(DBORDINAL* pcColumns,
   DBCOLUMNINFO** prgInfo,
   OLECHAR** ppStringsBuffer);
```

#### <a name="parameters"></a>Parámetros

Consulte [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) en el *referencia del programador OLE DB*.

## <a name="mapcolumnids"></a> IColumnsInfoImpl::MapColumnIDs

Devuelve una matriz de ordinales de las columnas en un conjunto de filas que se identifican mediante los identificadores de columna especificado.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (MapColumnIDs)(DBORDINAL cColumnIDs,
   const DBID rgColumnIDs[],
   DBORDINAL rgColumns[]);
```

#### <a name="parameters"></a>Parámetros

Consulte [IColumnsInfo::MapColumnIDs](/previous-versions/windows/desktop/ms714200(v=vs.85)) en el *referencia del programador OLE DB*.

## <a name="see-also"></a>Vea también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)