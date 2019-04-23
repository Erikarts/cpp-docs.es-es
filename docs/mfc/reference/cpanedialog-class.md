---
title: CPaneDialog (clase)
ms.date: 11/04/2016
f1_keywords:
- CPaneDialog
- AFXPANEDIALOG/CPaneDialog
- AFXPANEDIALOG/CPaneDialog::Create
- AFXPANEDIALOG/CPaneDialog::HandleInitDialog
- AFXPANEDIALOG/CPaneDialog::SetOccDialogInfo
helpviewer_keywords:
- CPaneDialog [MFC], Create
- CPaneDialog [MFC], HandleInitDialog
- CPaneDialog [MFC], SetOccDialogInfo
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
ms.openlocfilehash: c78b8f2cd19e87fa559c3f9bbd24d07543d887c5
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58769750"
---
# <a name="cpanedialog-class"></a>CPaneDialog (clase)

La `CPaneDialog` clase es compatible con un cuadro de diálogo no modal, acoplable.

## <a name="syntax"></a>Sintaxis

```
class CPaneDialog : public CDockablePane
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|`CPaneDialog::CPaneDialog`|Constructor predeterminado.|
|`CPaneDialog::~CPaneDialog`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CPaneDialog::Create](#create)|Crea un cuadro de diálogo acoplable y lo adjunta a un `CPaneDialog` objeto.|
|`CPaneDialog::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CPaneDialog::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|Controla el [WM_INITDIALOG](/windows/desktop/dlgbox/wm-initdialog) mensaje. (Redefine `CBasePane::HandleInitDialog`.)|
|`CPaneDialog::OnEraseBkgnd`|Controla el [WM_ERASEBKGND](/windows/desktop/winmsg/wm-erasebkgnd) mensaje. (Redefine [CWnd::OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd).)|
|`CPaneDialog::OnLButtonDblClk`|Controla el [WM_LBUTTONDBLCLK](/windows/desktop/inputdev/wm-lbuttondblclk) mensaje. (Redefine [CWnd::OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk).)|
|`CPaneDialog::OnLButtonDown`|Controla el [WM_LBUTTONDOWN](/windows/desktop/inputdev/wm-lbuttondown) mensaje. (Redefine [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown).)|
|`CPaneDialog::OnUpdateCmdUI`|Lo llama el marco de trabajo para actualizar la ventana del cuadro de diálogo. (Invalida [CDockablePane:: OnUpdateCmdUI](cdockablepane-class.md).)|
|`CPaneDialog::OnWindowPosChanging`|Controla el [WM_WINDOWPOSCHANGING](/windows/desktop/winmsg/wm-windowposchanging) mensaje. (Redefine [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging).)|
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|Especifica la plantilla para un cuadro de diálogo que es un contenedor de controles OLE.|

## <a name="remarks"></a>Comentarios

Construir un `CPaneDialog` objeto en dos pasos. Primero, construya el objeto en el código. En segundo lugar, llame a [CPaneDialog::Create](#create). Debe especificar un identificador de nombre o la plantilla de la plantilla de recurso válido y pasar un puntero a la ventana primaria. En caso contrario, se produce un error en el proceso de creación. El cuadro de diálogo debe especificar el estilo WS_CHILD y WS_VISIBLE. Se recomienda que especifique también los estilos WS_CLIPCHILDREN y WS_CLIPSIBLINGS. Para obtener más información, consulte [estilos de ventana](styles-used-by-mfc.md#window-styles).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CPaneDialog](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpanedialog.h

##  <a name="create"></a>  CPaneDialog::Create

Crea un cuadro de diálogo de acoplamiento y lo adjunta a un `CPaneDialog` objeto.

```
BOOL Create(
    LPCTSTR lpszWindowName,
    CWnd* pParentWnd,
    BOOL bHasGripper,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID,
    DWORD dwTabbedStyle= AFX_CBRS_REGULAR_TABS,
    DWORD dwControlBarStyle=AFX_DEFAULT_DOCKING_PANE_STYLE);

BOOL Create(
    LPCTSTR lpszWindowName,
    CWnd* pParentWnd,
    BOOL bHasGripper,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);

BOOL Create(
    CWnd* pParentWnd,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID);

BOOL Create(
    CWnd* pParentWnd,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*lpszWindowName*<br/>
[in] El nombre del cuadro de diálogo de acoplamiento.

*pParentWnd*<br/>
[in] Apunta a la ventana primaria.

*bHasGripper*<br/>
[in] TRUE para crear el cuadro de diálogo de acoplamiento con el título (agarrador); en caso contrario, FALSE.

*lpszTemplateName*<br/>
[in] El nombre de la plantilla de cuadro de diálogo de recursos.

*nStyle*<br/>
[in] El estilo de Windows.

*nID*<br/>
[in] El identificador de control.

*nIDTemplate*<br/>
[in] El identificador de recurso de la plantilla de cuadro de diálogo.

*dwTabbedStyle*<br/>
[in] El estilo de la ventana con pestañas que se produce cuando el usuario arrastra otro panel de control en el título de este panel de control. El valor predeterminado es AFX_CBRS_REGULAR_TABS. Para obtener más información, vea la sección Comentarios de la [cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex) método.

*dwControlBarStyle*<br/>
[in] Atributos de estilo adicionales. El valor predeterminado es AFX_DEFAULT_DOCKING_PANE_STYLE. Para obtener más información, vea la sección Comentarios de la [cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex) método.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar el `Create` método en el `CPaneDialog` clase. Este ejemplo forma parte de la [ejemplo establece el tamaño del panel](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

##  <a name="handleinitdialog"></a>  CPaneDialog::HandleInitDialog

Controla el [WM_INITDIALOG](/windows/desktop/dlgbox/wm-initdialog) mensaje.

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*wParam*<br/>
[in] Identificador del control que va a recibir el foco de teclado predeterminado.

*lParam*<br/>
[in] Especifica los datos de inicialización adicionales.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE. Además, es TRUE establece el foco de teclado para el control especificado por el *wParam* parámetro; FALSE impide establecer el foco de teclado predeterminado.

### <a name="remarks"></a>Comentarios

El marco de trabajo usa este método para inicializar los controles y la apariencia de un cuadro de diálogo. El marco llama a este método antes de mostrar el cuadro de diálogo.

##  <a name="setoccdialoginfo"></a>  CPaneDialog::SetOccDialogInfo

Especifica la plantilla para un cuadro de diálogo que es un contenedor de controles OLE.

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parámetros

*pOccDialogInfo*<br/>
[in] Puntero a una plantilla de cuadro de diálogo que se usa para crear el objeto de cuadro de diálogo. El valor de este parámetro se pasa posteriormente a la [COccManager::CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols) método.

### <a name="return-value"></a>Valor devuelto

Siempre es TRUE.

### <a name="remarks"></a>Comentarios

Este método admite la [COccManager](../../mfc/reference/coccmanager-class.md) (clase), que administra controles ActiveX y sitios de control OLE. La estructura _AFX_OCC_DIALOG_INFO se define en el archivo de encabezado afxocc.h.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane (clase)](../../mfc/reference/cdockablepane-class.md)<br/>
[Estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles)
