---
title: CDocObjectServerItem (clase)
ms.date: 03/27/2019
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnDoVerb
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnDoVerb
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
ms.openlocfilehash: 66ff2326cd3d08b3f6c8399d7e948d6aab5074c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391158"
---
# <a name="cdocobjectserveritem-class"></a>CDocObjectServerItem (clase)

Implementa verbos de servidor OLE específicamente para servidores de DocObject.

## <a name="syntax"></a>Sintaxis

```
class CDocObjectServerItem : public COleServerItem
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Name|Descripción|
|----------|-----------------|
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|Construye un objeto `CDocObjectServerItem`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDocObjectServerItem::GetDocument](#getdocument)|Recupera un puntero al documento que contiene el elemento.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CDocObjectServerItem::OnDoVerb](#ondoverb)|Se llama para ejecutar un verbo.|
|[CDocObjectServerItem::OnHide](#onhide)|Produce una excepción si el marco de trabajo intenta ocultar un elemento de DocObject.|
|[CDocObjectServerItem::OnShow](#onshow)|Lo llama el marco para que sea el DocObject elemento en el sitio activo. Si el elemento no es un objeto DocObject, llama a [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow).|

## <a name="remarks"></a>Comentarios

`CDocObjectServerItem` define las funciones miembro que se puede invalidar: [OnHide](#onhide), [OnDoVerb](#ondoverb), y [OnShow](#onshow).

Para usar `CDocObjectServerItem`, asegurarse de que el [OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) invalidar en su `COleServerDoc`-devuelve una nueva clase derivada `CDocObjectServerItem` objeto. Si necesita cambiar ninguna funcionalidad en el elemento, puede crear una nueva instancia de su propio `CDocObjectServerItem`-clase derivada.

Para obtener más información sobre DocObjects, consulte [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) y [COleCmdUI](../../mfc/reference/colecmdui-class.md) en el *referencia de MFC*.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleServerItem](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdocob.h

##  <a name="cdocobjectserveritem"></a>  CDocObjectServerItem::CDocObjectServerItem

Construye un objeto `CDocObjectServerItem`.

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>Parámetros

*pServerDoc*<br/>
Un puntero al documento que contendrá el nuevo elemento de DocObject.

*bAutoDelete*<br/>
Indica si el objeto se puede eliminar cuando se suelta un vínculo a él. Establezca el argumento FALSE si el `CDocObjectServerItem` objeto es una parte integral de los datos del documento. Establézcalo en TRUE si el objeto es una estructura secundaria utilizada para identificar un intervalo en los datos del documento que se pueden eliminar mediante el marco de trabajo.

##  <a name="getdocument"></a>  CDocObjectServerItem::GetDocument

Recupera un puntero al documento que contiene el elemento.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al documento que contiene el elemento; Es NULL si el elemento no forma parte de un documento.

### <a name="remarks"></a>Comentarios

Esto permite el acceso al documento de servidor que pasa como argumento a la [CDocObjectServerItem](#cdocobjectserveritem) constructor.

##  <a name="ondoverb"></a>  CDocObjectServerItem::OnDoVerb

Lo llama el marco de trabajo para ejecutar el verbo especificado.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parámetros

*iVerb*<br/>
Especifica el verbo que se ejecute. Para los valores posibles, vea [DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) en el SDK de Windows.

### <a name="remarks"></a>Comentarios

La implementación predeterminada llama el [OnShow](#onshow) función de miembro si el elemento es un objeto DocObject y se especifica la OLEIVERB_INPLACEACTIVATE o OLEIVERB_SHOW. Si el elemento no es un objeto DocObject o se especifica un verbo diferente, la implementación predeterminada llama [COleServerItem::OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb).

##  <a name="onhide"></a>  CDocObjectServerItem::OnHide

Lo llama el marco para ocultar el elemento.

```
virtual void OnHide();
```

### <a name="remarks"></a>Comentarios

La implementación predeterminada produce una excepción si el elemento es un objeto DocObject. No se puede ocultar un elemento de DocObject activo porque toma la vista entera. Debe desactivar el elemento de DocObject para que desaparezca. Si el elemento no es un objeto DocObject, la implementación predeterminada llama [COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide).

##  <a name="onshow"></a>  CDocObjectServerItem::OnShow

Lo llama el marco para indicar a la aplicación de servidor para que sea el DocObject elemento en el sitio activo.

```
virtual void OnShow();
```

### <a name="remarks"></a>Comentarios

Si el elemento no es un objeto DocObject, la implementación predeterminada llama [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen). Reemplace esta función si desea realizar el procesamiento al abrir un elemento de DocObject especial.

## <a name="see-also"></a>Vea también

[COleServerItem (clase)](../../mfc/reference/coleserveritem-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServer (clase)](../../mfc/reference/cdocobjectserver-class.md)<br/>
[COleDocObjectItem (clase)](../../mfc/reference/coledocobjectitem-class.md)
