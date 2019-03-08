---
title: CMFCPropertyGridFontProperty (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetLogFont
helpviewer_keywords:
- CMFCPropertyGridFontProperty [MFC], CMFCPropertyGridFontProperty
- CMFCPropertyGridFontProperty [MFC], GetColor
- CMFCPropertyGridFontProperty [MFC], GetLogFont
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
ms.openlocfilehash: 2ab4f43b2b12dff88148097e2961f235669aaa62
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295674"
---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty (clase)

La `CMFCPropertyGridFileProperty` clase es compatible con un elemento de control de lista de propiedades que se abre un cuadro de diálogo de selección de fuente.

## <a name="syntax"></a>Sintaxis

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|Construye un objeto `CMFCPropertyGridFontProperty`.|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|Da formato a la representación de texto de un valor de propiedad. (Invalida [cmfcpropertygridproperty:: Formatproperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|Recupera el color de fuente que el usuario selecciona en el cuadro de diálogo fuente.|
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|Recupera la fuente que el usuario selecciona en el cuadro de diálogo fuente.|
|`CMFCPropertyGridFontProperty::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|
|`CMFCPropertyGridFontProperty::OnClickButton`|Lo llama el marco cuando el usuario hace clic en un botón que se encuentra en una propiedad. (Invalida [cmfcpropertygridproperty:: Onclickbutton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

## <a name="remarks"></a>Comentarios

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpropertygridctrl.h

##  <a name="cmfcpropertygridfontproperty"></a>  CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty

Construye un objeto `CMFCPropertyGridFontProperty`.

```
CMFCPropertyGridFontProperty(
    const CString& strName,
    LOGFONT& lf,
    DWORD dwFontDialogFlags = CF_EFFECTS | CF_SCREENFONTS,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0,
    COLORREF color = (COLORREF)-1);
```

### <a name="parameters"></a>Parámetros

*strName*<br/>
[in] El nombre de la propiedad.

*lf*<br/>
[in] Una estructura de fuente lógica que especifica los atributos de la fuente.

*dwFontDialogFlags*<br/>
[in] Estilos que se aplican al cuadro de diálogo fuente que se muestra al hacer clic en el botón de lista desplegable del valor de propiedad. El valor predeterminado es la combinación bit a bit (OR) de CF_EFFECTS y CF_SCREENFONTS. Para obtener más información, consulte el *marcas* parámetro de la [CHOOSEFONT estructura](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta).

*lpszDescr*<br/>
[in] Descripción de la propiedad font. El valor predeterminado es NULL.

*dwData*<br/>
[in] Datos específicos de la aplicación, como un entero o un puntero a otros datos que está asociados a la propiedad. El valor predeterminado es 0.

*color*<br/>
[in] El color de la fuente. El valor predeterminado es el color predeterminado.

### <a name="remarks"></a>Comentarios

Un `CMFCPropertyGridFontProperty` objeto representa una propiedad de fuente en un control de fuente de cuadrícula de propiedades.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCPropertyGridFontProperty` clase. Este ejemplo forma parte de la [ejemplo de controles nuevos](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

##  <a name="getcolor"></a>  CMFCPropertyGridFontProperty::GetColor

Recupera el color de fuente que el usuario selecciona en el cuadro de diálogo fuente.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de color RGB que representa el color de fuente seleccionada.

### <a name="remarks"></a>Comentarios

##  <a name="getlogfont"></a>  CMFCPropertyGridFontProperty::GetLogFont

Recupera la fuente que el usuario selecciona en el cuadro de diálogo fuente.

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) estructura que describe la fuente seleccionada.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl (clase)](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty (clase)](../../mfc/reference/cmfcpropertygridproperty-class.md)
