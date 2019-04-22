---
title: CRichEditCntrItem (clase)
ms.date: 11/04/2016
f1_keywords:
- CRichEditCntrItem
- AFXRICH/CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::SyncToRichEditObject
helpviewer_keywords:
- CRichEditCntrItem [MFC], CRichEditCntrItem
- CRichEditCntrItem [MFC], SyncToRichEditObject
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
ms.openlocfilehash: 674937df9b4ecef0d159a47a45a716d1175ad5d9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58773845"
---
# <a name="cricheditcntritem-class"></a>CRichEditCntrItem (clase)

Con [CRichEditView](../../mfc/reference/cricheditview-class.md) y [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), proporciona la funcionalidad del control rich edit en el contexto de la arquitectura de vista de documento de MFC.

## <a name="syntax"></a>Sintaxis

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CRichEditCntrItem::CRichEditCntrItem](#cricheditcntritem)|Construye un objeto `CRichEditCntrItem`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|Activa el elemento como otro tipo.|

## <a name="remarks"></a>Comentarios

Un "control rich edit" es una ventana en la que el usuario puede escribir y editar texto. El texto se puede asignar caracteres y el formato de párrafo y puede incluir objetos OLE incrustados. Los controles Rich edit proporcionan una interfaz de programación para dar formato al texto. Sin embargo, una aplicación debe implementar los componentes de interfaz de usuario necesarios para realizar operaciones de formato disponibles para el usuario.

`CRichEditView` mantiene el texto y la característica de formato de texto. `CRichEditDoc` mantiene la lista de elementos de cliente OLE que se encuentran en la vista. `CRichEditCntrItem` proporciona acceso de contenedor para el elemento de cliente OLE.

Este control común de Windows (y por lo tanto, el [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) y las clases relacionadas) está disponible solo para programas que se ejecutan en versiones de Windows 95/98 y Windows NT 3.51 y versiones posteriores.

Para obtener un ejemplo del uso de los elementos de contenedor de edición enriquecida en una aplicación MFC, vea el [WORDPAD](../../overview/visual-cpp-samples.md) aplicación de ejemplo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrich.h

##  <a name="cricheditcntritem"></a>  CRichEditCntrItem::CRichEditCntrItem

Llame a esta función para crear un `CRichEditCntrItem` y agregarlo al documento contenedor.

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>Parámetros

*preo*<br/>
Puntero a un [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) estructura que describe un elemento OLE. El nuevo `CRichEditCntrItem` se construye el objeto en torno a esta elemento OLE. Si *preo* es NULL, el elemento de cliente está vacío.

*pContainer*<br/>
Puntero en el documento contenedor que contendrá este elemento. Si *que pContainer* es NULL, debe llamar explícitamente a [COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem) para agregar este elemento de cliente a un documento.

### <a name="remarks"></a>Comentarios

Esta función no realiza ninguna inicialización de OLE.

Para obtener más información, consulte el [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) estructura en el SDK de Windows.

##  <a name="synctoricheditobject"></a>  CRichEditCntrItem::SyncToRichEditObject

Llame a esta función para sincronizar el aspecto del dispositivo, [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect), de este `CRichEditCntrltem` al especificado por *reo*.

```
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>Parámetros

*reo*<br/>
Hacer referencia a un [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) estructura que describe un elemento OLE.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem (clase)](../../mfc/reference/coleclientitem-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc (clase)](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditView (clase)](../../mfc/reference/cricheditview-class.md)
