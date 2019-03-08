---
title: IConvertTypeImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
helpviewer_keywords:
- IConvertTypeImpl class
- CanConvert method
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
ms.openlocfilehash: e1117cfb8e68cbdc5432355315213faad903ea35
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424657"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl (Clase)

Proporciona una implementación de la [IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85)) interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
class ATL_NO_VTABLE IConvertTypeImpl
   : public IConvertType, public CConvertHelper
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IConvertTypeImpl`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Miembros

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[CanConvert](#canconvert)|Proporciona información sobre la disponibilidad de las conversiones de tipos en un comando o en un conjunto de filas.|

## <a name="remarks"></a>Comentarios

Esta interfaz es obligatoria en los comandos, los conjuntos de filas y conjuntos de filas de índice. `IConvertTypeImpl` implementa la interfaz mediante la delegación para el objeto de conversión proporcionado por OLE DB.

## <a name="canconvert"></a> IConvertTypeImpl::CanConvert

Proporciona información sobre la disponibilidad de las conversiones de tipos en un comando o en un conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType,
   DBTYPE wToType,
   DBCONVERTFLAGS dwConvertFlags);
```

#### <a name="parameters"></a>Parámetros

Consulte [IConvertType::CanConvert](/previous-versions/windows/desktop/ms711224(v=vs.85)) en el *referencia del programador OLE DB*.

### <a name="remarks"></a>Comentarios

Utiliza la conversión de datos OLE DB en `MSADC.DLL`.

## <a name="see-also"></a>Vea también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)