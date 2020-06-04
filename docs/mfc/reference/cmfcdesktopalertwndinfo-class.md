---
title: CMFCDesktopAlertWndInfo Clase
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_hIcon
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_nURLCmdID
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strText
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strURL
helpviewer_keywords:
- CMFCDesktopAlertWndInfo [MFC], m_hIcon
- CMFCDesktopAlertWndInfo [MFC], m_nURLCmdID
- CMFCDesktopAlertWndInfo [MFC], m_strText
- CMFCDesktopAlertWndInfo [MFC], m_strURL
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
ms.openlocfilehash: f51c1b75e0c096a34b190e36e097aaca4109b5f8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367583"
---
# <a name="cmfcdesktopalertwndinfo-class"></a>CMFCDesktopAlertWndInfo Clase

La `CMFCDesktopAlertWndInfo` clase se utiliza con la [clase CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md). Especifica los controles que se muestran si emerge la ventana de alerta de escritorio.

## <a name="syntax"></a>Sintaxis

```
class CMFCDesktopAlertWndInfo
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo::operator ?](#operator_eq)||

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)|Identificador del icono que se muestra.|
|[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)|El identificador de comando asociado a un vínculo en la ventana de alerta de escritorio.|
|[CMFCDesktopAlertWndInfo::m_strText](#m_strtext)|El texto que se muestra en la ventana de alerta del escritorio.|
|[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)|El vínculo que se muestra en la ventana de alerta del escritorio.|

## <a name="remarks"></a>Observaciones

La `CMFCDesktopAlertWndInfo` clase se pasa al método [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) para especificar los elementos que se muestran en el cuadro de diálogo predeterminado de la ventana de alerta de escritorio. El cuadro de diálogo predeterminado puede contener tres elementos:

- Un icono, que se establece mediante una llamada a [CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon).

- Una etiqueta o mensaje de texto, que se establece mediante una llamada a [CMFCDesktopAlertWndInfo::m_strText](#m_strtext).

- Un vínculo, que se establece mediante una llamada a [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl). Para establecer el comando que se ejecuta cuando se hace clic en el vínculo, llame a [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid).

Si el cuadro de diálogo predeterminado no es suficiente, puede crear un cuadro de diálogo personalizado y pasarlo al método [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) en lugar de utilizar esta clase. Para obtener más información, vea [CMFCDesktopAlertDialog (Clase)](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCDesktopAlertWndInfo` cómo utilizar varios miembros de la clase. En el ejemplo se muestra cómo establecer el identificador en el icono que se muestra, el texto que se muestra en la ventana de alerta de escritorio, el vínculo que se muestra en la ventana de alerta de escritorio y el identificador de comando asociado a un vínculo en la ventana de alerta de escritorio. Este ejemplo forma parte del [ejemplo Demostración](../../overview/visual-cpp-samples.md)de alertas de escritorio.

[!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxDesktopAlertDialog.h

## <a name="cmfcdesktopalertwndinfooperator"></a><a name="operator_eq"></a>CMFCDesktopAlertWndInfo::operator ?

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```

### <a name="parameters"></a>Parámetros

[en] *src*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcdesktopalertwndinfom_hicon"></a><a name="m_hicon"></a>CMFCDesktopAlertWndInfo::m_hIcon

Identificador del icono que se muestra.

```
HICON m_hIcon;
```

### <a name="remarks"></a>Observaciones

## <a name="cmfcdesktopalertwndinfom_nurlcmdid"></a><a name="m_nurlcmdid"></a>CMFCDesktopAlertWndInfo::m_nURLCmdID

El identificador de comando asociado a un vínculo en la ventana de alerta de escritorio.

```
UINT m_nURLCmdID;
```

### <a name="remarks"></a>Observaciones

El identificador de comando se envía al propietario de la ventana emergente cuando el usuario hace clic en el vínculo especificado por [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl).

## <a name="cmfcdesktopalertwndinfom_strtext"></a><a name="m_strtext"></a>CMFCDesktopAlertWndInfo::m_strText

El texto que se muestra en la ventana de alerta del escritorio.

```
CString m_strText;
```

### <a name="remarks"></a>Observaciones

## <a name="cmfcdesktopalertwndinfom_strurl"></a><a name="m_strurl"></a>CMFCDesktopAlertWndInfo::m_strURL

El vínculo que se muestra en la ventana de alerta del escritorio.

```
CString m_strURL;
```

### <a name="remarks"></a>Observaciones

Cuando el usuario hace clic en el vínculo, el comando que tiene el [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid) identificador de comando se enviará al propietario de la ventana emergente.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFCDesktopAlertWnd::Crear](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)<br/>
[CMFCDesktopAlertDialog (clase)](../../mfc/reference/cmfcdesktopalertdialog-class.md)
