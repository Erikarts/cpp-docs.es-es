---
title: Funciones globales de serialización
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
ms.openlocfilehash: cac6e316ad6b5d3f49c171c940d9129060744aee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274699"
---
# <a name="marshaling-global-functions"></a>Funciones globales de serialización

Estas funciones proporcionan compatibilidad para el cálculo de referencias y conversión de datos de cálculo de referencias a punteros de interfaz.

> [!IMPORTANT]
>  Las funciones enumeradas en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

|||
|-|-|
|[AtlFreeMarshalStream](#atlfreemarshalstream)|Libera los datos de serialización y el `IStream` puntero.|
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|Crea un nuevo objeto de secuencia y calcula las referencias el puntero de interfaz especificado.|
|[AtlUnmarshalPtr](#atlunmarshalptr)|Serialización de datos de la secuencia se convierte en un puntero de interfaz.|

## <a name="requirements"></a>Requisitos:

**Encabezado:** atlbase.h

##  <a name="atlfreemarshalstream"></a>  AtlFreeMarshalStream

Libera los datos de serializar del flujo; a continuación, libera el puntero del flujo.

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
[in] Un puntero a la `IStream` interfaz en la secuencia utilizada para calcular las referencias.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [AtlMarshalPtrInProc](#atlmarshalptrinproc).

##  <a name="atlmarshalptrinproc"></a>  AtlMarshalPtrInProc

Crea un nuevo objeto de flujo, escribe el CLSID del proxy en el flujo y calcula las referencias del puntero de interfaz especificado escribiendo los datos necesarios para inicializar el proxy en el flujo.

```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
[in] Un puntero a la interfaz que se van a calcular.

*iid*<br/>
[in] El GUID de la interfaz que se va a serializar.

*ppStream*<br/>
[out] Un puntero a la `IStream` interfaz en el nuevo objeto de secuencia utilizado para calcular las referencias.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Se establece la marca MSHLFLAGS_TABLESTRONG por lo que el puntero se puede serializar en varias secuencias. El puntero también se puede deserializar varias veces.

Si se produce un error de cálculo de referencias, se libera el puntero del flujo.

`AtlMarshalPtrInProc` solo puede usarse en un puntero a un objeto en proceso.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]

##  <a name="atlunmarshalptr"></a>  AtlUnmarshalPtr

Convierte los datos de cálculo de referencias del flujo en un puntero de interfaz que puede usarse en el cliente.

```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
[in] Un puntero a la secuencia que se resuelven referencias.

*iid*<br/>
[in] El GUID de la interfaz que se resuelven referencias.

*ppUnk*<br/>
[out] Un puntero a la interfaz sin cálculo de referencias.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [AtlMarshalPtrInProc](#atlmarshalptrinproc).

## <a name="see-also"></a>Vea también

[Funciones](../../atl/reference/atl-functions.md)
