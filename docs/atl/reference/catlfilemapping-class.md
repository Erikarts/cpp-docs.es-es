---
title: CAtlFileMapping (clase)
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: d0a47a6cf0cc86409ceb9ef40d6fc6d738c86aa9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247179"
---
# <a name="catlfilemapping-class"></a>CAtlFileMapping (clase)

Esta clase representa un archivo asignado a memoria, adición de un operador de conversión a los métodos de [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos utilizados para el operador de conversión.

## <a name="members"></a>Miembros

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlFileMapping::operator T *](#operator_t_star)|Permite la conversión implícita de `CAtlFileMapping` objetos `T*`.|

## <a name="remarks"></a>Comentarios

Esta clase agrega un operador de conversión única para permitir la conversión implícita de `CAtlFileMapping` objetos `T*`. Otros miembros proporcionados por la clase base, [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlfile.h

##  <a name="operator_t_star"></a>  CAtlFileMapping::operator T *

Permite la conversión implícita de `CAtlFileMapping` objetos `T*`.

```
operator T*() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un `T*` puntero al principio del archivo asignado a la memoria.

### <a name="remarks"></a>Comentarios

Las llamadas [CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) y vuelve a interpretar el puntero devuelto como un `T*` donde *T* es el tipo utilizado como parámetro de plantilla de esta clase.

## <a name="see-also"></a>Vea también

[CAtlFileMappingBase (clase)](../../atl/reference/catlfilemappingbase-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
