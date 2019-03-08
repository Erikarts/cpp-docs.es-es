---
title: CComClassFactory (clase)
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
ms.openlocfilehash: 85ef287a905abc7b3151628c0f5dc29b9050b187
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326573"
---
# <a name="ccomclassfactory-class"></a>CComClassFactory (clase)

Esta clase implementa la [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interfaz.

## <a name="syntax"></a>Sintaxis

```
class CComClassFactory
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComClassFactory::CreateInstance](#createinstance)|Crea un objeto del CLSID especificado.|
|[CComClassFactory::LockServer](#lockserver)|Bloquea el generador de clases en la memoria.|

## <a name="remarks"></a>Comentarios

`CComClassFactory` implementa el [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interfaz, que contiene métodos para crear un objeto de un CLSID determinado, así como el generador de clases en la memoria para permitir que los nuevos objetos se pueden crear más rápidamente el bloqueo. `IClassFactory` se debe implementar para todas las clases que se registran en el registro del sistema y que asigna un CLSID.

Objetos ATL adquieren normalmente un generador de clases mediante la derivación de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), que declara `CComClassFactory` como el generador de clases de forma predeterminada. Para invalidar este comportamiento predeterminado, especifique uno de los `DECLARE_CLASSFACTORY` *XXX* macros en la definición de clase. Por ejemplo, el [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex) macro usa la clase especificada para el generador de clases:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

La definición de clase anterior especifica que `CMyClassFactory` se usará como el generador de clases predeterminado del objeto. `CMyClassFactory` debe derivar de `CComClassFactory` e invalidar `CreateInstance`.

ATL proporciona tres otras macros que declaran un generador de clases:

- [Macro DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) usa [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), que controla la creación a través de una licencia.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) usa [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), que crea objetos en varios contenedores.

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) usa [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), que construye una sola [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="createinstance"></a>  CComClassFactory::CreateInstance

Crea un objeto del CLSID especificado y recupera un puntero de interfaz a este objeto.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Parámetros

*pUnkOuter*<br/>
[in] Si el objeto se crea como parte de un agregado y, a continuación, *pUnkOuter* debe ser el desconocido externo. En caso contrario, *pUnkOuter* debe ser NULL.

*riid*<br/>
[in] IID de la interfaz solicitada. Si *pUnkOuter* es distinto de NULL, *riid* debe ser `IID_IUnknown`.

*ppvObj*<br/>
[out] Un puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *ppvObj* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="lockserver"></a>  CComClassFactory::LockServer

Incrementa y disminuye el bloqueo de módulo se cuentan mediante una llamada a `_Module::Lock` y `_Module::Unlock`, respectivamente.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Parámetros

*fLock*<br/>
[in] Si es TRUE, se incrementa el recuento de bloqueos; en caso contrario, el recuento de bloqueos es reducido.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

`_Module` hace referencia a la instancia global de [CComModule](../../atl/reference/ccommodule-class.md) o una clase derivada de él.

Una llamada a `LockServer` permite que un cliente retener un generador de clases para que se pueden crear rápidamente varios objetos.

## <a name="see-also"></a>Vea también

[CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
