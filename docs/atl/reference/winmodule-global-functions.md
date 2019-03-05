---
title: Funciones globales de WinModule
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 0e7450ea2a42c0b35dc5a6d1b77dfb0f2acb9520
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265096"
---
# <a name="winmodule-global-functions"></a>Funciones globales de WinModule

Estas funciones proporcionan compatibilidad para `_AtlCreateWndData` estructurar las operaciones.

> [!IMPORTANT]
> Las funciones enumeradas en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

|||
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|Esta función se utiliza para inicializar y agregar una estructura `_AtlCreateWndData`.|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|Llame a esta función para extraer una estructura `_AtlCreateWndData` existente.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="atlwinmoduleaddcreatewnddata"></a>  AtlWinModuleAddCreateWndData

Esta función se utiliza para inicializar y agregar una estructura `_AtlCreateWndData`.

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>Parámetros

*pWinModule*<br/>
Puntero a un módulo [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) estructura.

*pData*<br/>
Puntero a la [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) estructura se inicialicen y agregado al módulo actual.

*pObject*<br/>
Puntero a un objeto **esto** puntero.

### <a name="remarks"></a>Comentarios

Inicializa un `_AtlCreateWndData` estructura, que se usa para almacenar el **esto** puntero utilizado para hacer referencia a instancias de clase y lo agrega a la lista de un módulo hace referencia `_ATL_WIN_MODULE70` estructura. Lo llama [CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata).

##  <a name="atlwinmoduleextractcreatewnddata"></a>  AtlWinModuleExtractCreateWndData

Llame a esta función para extraer una estructura `_AtlCreateWndData` existente.

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>Parámetros

*pWinModule*<br/>
Puntero a un módulo [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) estructura.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) estructura.

### <a name="remarks"></a>Comentarios

Esta función extraerá existente `_AtlCreateWndData` estructura de la lista que se hace referencia a un módulo `_ATL_WIN_MODULE70` estructura.

## <a name="see-also"></a>Vea también

[Funciones](../../atl/reference/atl-functions.md)
