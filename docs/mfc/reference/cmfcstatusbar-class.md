---
title: CMFCStatusBar (clase)
ms.date: 11/19/2018
f1_keywords:
- CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar::CalcFixedLayout
- AFXSTATUSBAR/CMFCStatusBar::CommandToIndex
- AFXSTATUSBAR/CMFCStatusBar::Create
- AFXSTATUSBAR/CMFCStatusBar::CreateEx
- AFXSTATUSBAR/CMFCStatusBar::DoesAllowDynInsertBefore
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneDoubleClick
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneProgressBar
- AFXSTATUSBAR/CMFCStatusBar::GetCount
- AFXSTATUSBAR/CMFCStatusBar::GetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetItemID
- AFXSTATUSBAR/CMFCStatusBar::GetItemRect
- AFXSTATUSBAR/CMFCStatusBar::GetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::GetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::GetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::GetPaneText
- AFXSTATUSBAR/CMFCStatusBar::GetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::GetTipText
- AFXSTATUSBAR/CMFCStatusBar::InvalidatePaneContent
- AFXSTATUSBAR/CMFCStatusBar::PreCreateWindow
- AFXSTATUSBAR/CMFCStatusBar::SetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::SetIndicators
- AFXSTATUSBAR/CMFCStatusBar::SetPaneAnimation
- AFXSTATUSBAR/CMFCStatusBar::SetPaneBackgroundColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneIcon
- AFXSTATUSBAR/CMFCStatusBar::SetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::SetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::SetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::SetPaneText
- AFXSTATUSBAR/CMFCStatusBar::SetPaneTextColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::SetTipText
- AFXSTATUSBAR/CMFCStatusBar::OnDrawPane
helpviewer_keywords:
- CMFCStatusBar [MFC], CalcFixedLayout
- CMFCStatusBar [MFC], CommandToIndex
- CMFCStatusBar [MFC], Create
- CMFCStatusBar [MFC], CreateEx
- CMFCStatusBar [MFC], DoesAllowDynInsertBefore
- CMFCStatusBar [MFC], EnablePaneDoubleClick
- CMFCStatusBar [MFC], EnablePaneProgressBar
- CMFCStatusBar [MFC], GetCount
- CMFCStatusBar [MFC], GetDrawExtendedArea
- CMFCStatusBar [MFC], GetExtendedArea
- CMFCStatusBar [MFC], GetItemID
- CMFCStatusBar [MFC], GetItemRect
- CMFCStatusBar [MFC], GetPaneInfo
- CMFCStatusBar [MFC], GetPaneProgress
- CMFCStatusBar [MFC], GetPaneStyle
- CMFCStatusBar [MFC], GetPaneText
- CMFCStatusBar [MFC], GetPaneWidth
- CMFCStatusBar [MFC], GetTipText
- CMFCStatusBar [MFC], InvalidatePaneContent
- CMFCStatusBar [MFC], PreCreateWindow
- CMFCStatusBar [MFC], SetDrawExtendedArea
- CMFCStatusBar [MFC], SetIndicators
- CMFCStatusBar [MFC], SetPaneAnimation
- CMFCStatusBar [MFC], SetPaneBackgroundColor
- CMFCStatusBar [MFC], SetPaneIcon
- CMFCStatusBar [MFC], SetPaneInfo
- CMFCStatusBar [MFC], SetPaneProgress
- CMFCStatusBar [MFC], SetPaneStyle
- CMFCStatusBar [MFC], SetPaneText
- CMFCStatusBar [MFC], SetPaneTextColor
- CMFCStatusBar [MFC], SetPaneWidth
- CMFCStatusBar [MFC], SetTipText
- CMFCStatusBar [MFC], OnDrawPane
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
ms.openlocfilehash: 87f75769e2f400a7721a8c9089d6c5596c31a4e3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58775964"
---
# <a name="cmfcstatusbar-class"></a>CMFCStatusBar (clase)

El `CMFCStatusBar` clase implementa una barra de estado similar a la `CStatusBar` clase. Sin embargo, la clase `CMFCStatusBar` tiene características que no ofrece la clase `CStatusBar` , tales como la capacidad para mostrar imágenes, animaciones y barras de progreso y la capacidad de responder a los doble clics del mouse.

Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
class CMFCStatusBar : public CPane
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCStatusBar::CalcFixedLayout](#calcfixedlayout)|(Invalida [cbasepane:: Calcfixedlayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCStatusBar::CommandToIndex](#commandtoindex)||
|[CMFCStatusBar::Create](#create)|Crea una barra de control y lo adjunta a la [CPane](../../mfc/reference/cpane-class.md) objeto. (Invalida [CPANE:: Create](../../mfc/reference/cpane-class.md#create).)|
|[CMFCStatusBar::CreateEx](#createex)|Crea una barra de control y lo adjunta a la [CPane](../../mfc/reference/cpane-class.md) objeto. (Invalida [CPANE:: CreateEx](../../mfc/reference/cpane-class.md#createex).)|
|[CMFCStatusBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Determina si se puede insertar otro panel dinámicamente entre este panel y el marco primario. (Invalida [cbasepane:: Doesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCStatusBar::EnablePaneDoubleClick](#enablepanedoubleclick)|Habilita o deshabilita el control de mouse hace doble clic en la barra de estado.|
|[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)|Muestra una barra de progreso en el panel especificado.|
|[CMFCStatusBar::GetCount](#getcount)|Devuelve el número de paneles en la barra de estado.|
|[CMFCStatusBar::GetDrawExtendedArea](#getdrawextendedarea)||
|[CMFCStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCStatusBar::GetItemID](#getitemid)||
|[CMFCStatusBar::GetItemRect](#getitemrect)||
|[CMFCStatusBar::GetPaneInfo](#getpaneinfo)||
|[CMFCStatusBar::GetPaneProgress](#getpaneprogress)||
|[CMFCStatusBar::GetPaneStyle](#getpanestyle)|Devuelve el estilo del panel. (Invalida [CBasePane::GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle).)|
|[CMFCStatusBar::GetPaneText](#getpanetext)||
|[CMFCStatusBar::GetPaneWidth](#getpanewidth)|Devuelve el ancho, en píxeles, del panel de la barra de estado especificado.|
|[CMFCStatusBar::GetTipText](#gettiptext)|Devuelve el texto de sugerencia para el panel de la barra de estado especificado.|
|[CMFCStatusBar::InvalidatePaneContent](#invalidatepanecontent)|Invalida el panel especificado y lo vuelve a dibujar su contenido.|
|[CMFCStatusBar::PreCreateWindow](#precreatewindow)|Lo llama el marco antes de la creación de la ventana de Windows asociada a este `CWnd` objeto. (Invalida [CWnd::PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).)|
|[CMFCStatusBar::SetDrawExtendedArea](#setdrawextendedarea)||
|[CMFCStatusBar::SetIndicators](#setindicators)||
|[CMFCStatusBar::SetPaneAnimation](#setpaneanimation)|Asigna una animación en el panel especificado.|
|[CMFCStatusBar::SetPaneBackgroundColor](#setpanebackgroundcolor)|Establece el color de fondo del panel de la barra de estado especificado.|
|[CMFCStatusBar::SetPaneIcon](#setpaneicon)|Establece el icono de indicador para el panel de la barra de estado especificado.|
|[CMFCStatusBar::SetPaneInfo](#setpaneinfo)||
|[CMFCStatusBar::SetPaneProgress](#setpaneprogress)|Establece el progreso actual de la barra de progreso para el panel de la barra de estado especificado.|
|[CMFCStatusBar::SetPaneStyle](#setpanestyle)|Establece el estilo del panel. (Invalida [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).)|
|[CMFCStatusBar::SetPaneText](#setpanetext)||
|[CMFCStatusBar::SetPaneTextColor](#setpanetextcolor)|Establece el color del texto del panel de la barra de estado especificado.|
|[CMFCStatusBar::SetPaneWidth](#setpanewidth)|Establece el ancho en píxeles del panel de la barra de estado especificado.|
|[CMFCStatusBar::SetTipText](#settiptext)|Establece el texto de sugerencia para el panel de la barra de estado especificado.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CMFCStatusBar::OnDrawPane](#ondrawpane)|Lo llama el marco de trabajo cuando vuelve a dibujar el panel de la barra de estado.|

## <a name="remarks"></a>Comentarios

El siguiente diagrama muestra una ilustración de la barra de estado de [ejemplo de demostración de la barra de estado](../../overview/visual-cpp-samples.md) aplicación.

![Ejemplo de CMFCStatusBar](../../mfc/reference/media/cmfcstatusbar.png "ejemplo de CMFCStatusBar")

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra las variables locales que la aplicación usa para llamar a métodos distintos en la `CMFCStatusBar` clase. Estas variables se declaran en StatusBarDemoView.h. El marco principal se declara en MainFrm.h, se declara el documento en StatusBarDemoDoc.h y la vista se declara en StatusBarDemoView.h. Este fragmento de código forma parte de la [ejemplo de demostración de la barra de estado](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo obtener una referencia a `CMFCStatusBar` objeto introduciendo el `GetStatusBar` método MainFrm.h y, a continuación, llamar a este método desde el `GetStatusBar` método StatusBarDemoView.h. Este fragmento de código forma parte de la [ejemplo de demostración de la barra de estado](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo llamar a métodos distintos en la `CMFCStatusBar` clase StatusBarDemoView.cpp. Las constantes se declaran en MainFrm.h. El ejemplo muestra cómo establecer el icono, establecer el texto de información sobre herramientas del panel de barra de estado, mostrar una barra de progreso en el panel especificado, asignar una animación en el panel especificado, Establece el texto y el ancho del panel de barra de estado y establezca el indicador de progreso actual de la progr barra de acceso para el panel de barra de estado. Este fragmento de código forma parte de la [ejemplo de demostración de la barra de estado](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxstatusbar.h

##  <a name="calcfixedlayout"></a>  CMFCStatusBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parámetros

[in] *bStretch*<br/>
[in] *bHorz*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="commandtoindex"></a>  CMFCStatusBar::CommandToIndex

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parámetros

[in] *nIDFind*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="create"></a>  CMFCStatusBar::Create

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parámetros

[in] *pParentWnd*<br/>
[in] *dwStyle*<br/>
[in] *nID*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="createex"></a>  CMFCStatusBar::CreateEx

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parámetros

[in] *pParentWnd*<br/>
[in] *dwCtrlStyle*<br/>
[in] *dwStyle*<br/>
[in] *nID*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="doesallowdyninsertbefore"></a>  CMFCStatusBar::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="enablepanedoubleclick"></a>  CMFCStatusBar::EnablePaneDoubleClick

Habilita o deshabilita el control de mouse hace doble clic en la barra de estado.

```
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
[in] Si es TRUE, habilite el procesamiento del doble clic del mouse. En caso contrario, deshabilite el procesamiento del doble clic del mouse.

### <a name="remarks"></a>Comentarios

Si está habilitada la barra de estado para procesar los dobles clics, Windows envía la notificación de WM_COMMAND junto con un identificador de recurso para el propietario de la cada vez que el usuario hace doble clic en el panel de barra de estado de la barra de estado.

##  <a name="enablepaneprogressbar"></a>  CMFCStatusBar::EnablePaneProgressBar

Mostrar una barra de progreso en el panel especificado.

```
void EnablePaneProgressBar(
    int nIndex,
    long nTotal=100,
    BOOL bDisplayText=FALSE,
    COLORREF clrBar=-1,
    COLORREF clrBarDest=-1,
    COLORREF clrProgressText=-1);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[in] Especifica el índice del panel cuyo barra de progreso para habilitar.

*nTotal*<br/>
[in] Especifica el valor máximo de la barra de progreso.

*bDisplayText*<br/>
[in] Especifica si la barra de progreso debe mostrar el valor de progreso actual.

*clrBar*<br/>
[in] Especifica el color de fondo de la barra de progreso.

*clrBarDest*<br/>
[in] Especifica el color secundario del fondo de la barra de progreso. Usar valor distinto de *clrBar* para rellenar por un dado lugar a un degradado de color.

*clrProgressText*<br/>
[in] Especifica el color del texto de la barra de progreso.

### <a name="remarks"></a>Comentarios

Si desea deshabilitar la llamada de la barra de progreso `EnablePaneProgressBar` con *nEl* establecido en -1. De forma predeterminada *nEl* está establecido en 100. Por lo tanto, no es necesario ningún cálculos adicionales para mostrar el progreso como porcentaje.

Debe pasar valores diferentes *clrBar* y *clrBarDest* para que el color de fondo de la barra de progreso muestre un dado lugar a un degradado de color. .

Para establecer el progreso actual, llame a la [CMFCStatusBar::SetPaneProgress](#setpaneprogress) método.

##  <a name="getcount"></a>  CMFCStatusBar::GetCount

Recupera el número de paneles en la barra de estado.

```
int GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de paneles en la barra de estado.

##  <a name="getdrawextendedarea"></a>  CMFCStatusBar::GetDrawExtendedArea

```
BOOL GetDrawExtendedArea() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getextendedarea"></a>  CMFCStatusBar::GetExtendedArea

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Parámetros

[in] *rect*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getitemid"></a>  CMFCStatusBar::GetItemID

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

[in] *nIndex*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getitemrect"></a>  CMFCStatusBar::GetItemRect

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

[in] *nIndex*<br/>
[in] *lpRect*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="getpaneinfo"></a>  CMFCStatusBar::GetPaneInfo

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parámetros

[in] *nIndex*<br/>
[in] *nID*<br/>
[in] *nStyle*<br/>
[in] *cxWidth*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="getpaneprogress"></a>  CMFCStatusBar::GetPaneProgress

```
long GetPaneProgress(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

[in] *nIndex*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getpanestyle"></a>  CMFCStatusBar::GetPaneStyle

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

[in] *nIndex*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getpanetext"></a>  CMFCStatusBar::GetPaneText

```
void GetPaneText(
    int nIndex,
    CString& s) const;

CString GetPaneText(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

[in] *nIndex*<br/>
[in] *s*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getpanewidth"></a>  CMFCStatusBar::GetPaneWidth

Recupera el ancho del panel de una barra de estado.

```
int GetPaneWidth(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[in] Especifica el índice del panel de barra de estado.

### <a name="return-value"></a>Valor devuelto

El ancho del panel de barra de estado que *nIndex* especifica; de lo contrario, es cero si no existe un panel de barra de estado.

##  <a name="gettiptext"></a>  CMFCStatusBar::GetTipText

Recuperar el texto de información sobre herramientas del panel de la barra de estado.

```
CString GetTipText(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[in] Especifica el índice del panel para que se va a recuperar el texto de sugerencia.

### <a name="return-value"></a>Valor devuelto

El texto de información sobre herramientas del panel de barra de estado que *nIndex* especifica. En caso contrario, la cadena vacía si no existe un panel de barra de estado para el elemento especificado *nIndex* o si el texto de información sobre herramientas está vacío.

##  <a name="invalidatepanecontent"></a>  CMFCStatusBar::InvalidatePaneContent

Invalidar el panel de barra de estado y volver a dibujar su contenido.

```
void InvalidatePaneContent(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[in] Especifica el índice del panel cuyo contenido es invalidado y vuelve a dibujar.

### <a name="remarks"></a>Comentarios

Cuando se invalida la barra de estado, se marca para volver a dibujar. Windows vuelve a dibujar cuando el `UpdateWindow` método envía un mensaje WM_PAINT a la `OnPaint` método.

##  <a name="ondrawpane"></a>  CMFCStatusBar::OnDrawPane

Volver a dibujar el panel de la barra de estado.

```
virtual void OnDrawPane(
    CDC* pDC,
    CMFCStatusBarPaneInfo* pPane);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Un puntero a un contexto de dispositivo para dibujar.

*pPane*<br/>
[in] Un puntero a un `CMFCStatusBarPaneInfo` estructura que contiene la información acerca del panel para volver a dibujar.

### <a name="remarks"></a>Comentarios

De forma predeterminada, `OnDrawPane` vuelve a dibujar el panel utilizando el contexto de dispositivo *pDC* según el estilo y el contenido del panel.

Invalide este método en un `CMFCStatusBar`-clase derivada para personalizar la apariencia de un panel.

##  <a name="precreatewindow"></a>  CMFCStatusBar::PreCreateWindow

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Parámetros

[in] *cs*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="setdrawextendedarea"></a>  CMFCStatusBar::SetDrawExtendedArea

```
void SetDrawExtendedArea(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parámetros

[in] *bSet*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="setindicators"></a>  CMFCStatusBar::SetIndicators

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parámetros

[in] *lpIDArray*<br/>
[in] *nIDCount*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="setpaneanimation"></a>  CMFCStatusBar::SetPaneAnimation

Asigna una animación en el panel especificado.

```
void SetPaneAnimation(
    int nIndex,
    HIMAGELIST hImageList,
    UINT nFrameRate=500,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[in] Especifica el índice del panel al que desea que se le asignan una animación.

*hImageList*<br/>
[in] Especifica un identificador de la lista de imágenes que contiene los fotogramas de animación.

*nFrameRate*<br/>
[in] Especifica la velocidad de fotogramas, en milisegundos, para la animación.

*bUpdate*<br/>
[in] Si es TRUE, actualice el contenido del panel inmediatamente. En caso contrario, se actualiza el contenido del panel al que se invalide.

### <a name="remarks"></a>Comentarios

Si desea deshabilitar la animación actual, llame a `SetPaneAnimation` con `hImageList` establecido en NULL.

##  <a name="setpanebackgroundcolor"></a>  CMFCStatusBar::SetPaneBackgroundColor

Establece el color de fondo del panel de barra de estado.

```
void SetPaneBackgroundColor(
    int nIndex,
    COLORREF clrBackground=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[in] Especifica el índice del panel para que se va a establecer un nuevo color de fondo.

*clrBackground*<br/>
[in] Especifica el nuevo color de fondo.

*bUpdate*<br/>
[in] Si es TRUE, actualice el contenido del panel inmediatamente. En caso contrario, no actualice el contenido del panel hasta que el panel se invalida por cualquier otro método.

##  <a name="setpaneicon"></a>  CMFCStatusBar::SetPaneIcon

Establecer el icono del panel de barra de estado.

```
void SetPaneIcon(
    int nIndex,
    HICON hIcon,
    BOOL bUpdate=TRUE);

void SetPaneIcon(
    int nIndex,
    HBITMAP hBmp,
    COLORREF clrTransparent=RGB(255, 0, 255),
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[in] Especifica el índice del panel para que se va a establecer la imagen.

*hIcon*<br/>
[in] Especifica un identificador para el icono que se establecerá como la imagen del panel.

*bUpdate*<br/>
[in] Especifica si se debe actualizar inmediatamente el contenido del panel.

*hBmp*<br/>
[in] Especifica un identificador para el mapa de bits que se establecerá como la imagen del panel.

*clrTransparent*<br/>
[in] Especifica el color transparente del mapa de bits que el *hBmp* indica.

### <a name="remarks"></a>Comentarios

Puede pasar HICON o HBITMAP junto con el color transparente para establecer la imagen del panel. Si no desea mostrar la imagen más largo, pase el valor NULL como identificador de la imagen.

Si no hay ninguna animación en ejecución que [CMFCStatusBar::SetPaneAnimation](#setpaneanimation) tiene establecido, se detendrá la animación.

##  <a name="setpaneinfo"></a>  CMFCStatusBar::SetPaneInfo

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parámetros

[in] *nIndex*<br/>
[in] *nID*<br/>
[in] *nStyle*<br/>
[in] *cxWidth*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="setpaneprogress"></a>  CMFCStatusBar::SetPaneProgress

Establezca el indicador de progreso actual de la barra de progreso para el panel especificado.

```
void SetPaneProgress(
    int nIndex,
    long nCurr,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[in] Especifica el índice del panel para que se va a actualizar el indicador de progreso.

*nCurr*<br/>
[in] Especifica el valor actual del indicador de progreso.

*bUpdate*<br/>
[in] Especifica si se debe actualizar inmediatamente el panel.

### <a name="remarks"></a>Comentarios

Llame a este método cuando desee actualizar el indicador de progreso de la barra de progreso en el panel especificado.

Para usar esta función para el panel determinado, debe llamar a [CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar) primero.

##  <a name="setpanestyle"></a>  CMFCStatusBar::SetPaneStyle

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parámetros

[in] *nIndex*<br/>
[in] *nStyle*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="setpanetext"></a>  CMFCStatusBar::SetPaneText

```
virtual BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parámetros

[in] *nIndex*<br/>
[in] *lpszNewText*<br/>
[in] *bActualizar*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="setpanetextcolor"></a>  CMFCStatusBar::SetPaneTextColor

Establece el color del texto del panel especificado.

```
void SetPaneTextColor(
    int nIndex,
    COLORREF clrText=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[in] Especifica el índice del panel al que desea asignar un nuevo color de texto.

*clrText*<br/>
[in] Especifica el color del texto.

*bUpdate*<br/>
[in] Si es TRUE, actualice el contenido del panel inmediatamente. En caso contrario, no actualice el contenido del panel hasta que el panel se invalida por cualquier otro método.

##  <a name="setpanewidth"></a>  CMFCStatusBar::SetPaneWidth

Establezca el ancho del panel de barra de estado.

```
void SetPaneWidth(
    int nIndex,
    int cx);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[in] Índice del panel de barra de estado para el que se va a establecer un ancho de nuevo.

*cx*<br/>
[in] Nuevo ancho del panel de barra de estado, en píxeles.

##  <a name="settiptext"></a>  CMFCStatusBar::SetTipText

Establecer el texto de información sobre herramientas de un panel de barra de estado.

```
void SetTipText(
    int nIndex,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[in] El índice del panel al que desea asignar el texto de información sobre herramientas.

*pszTipText*<br/>
[in] El nuevo texto de información sobre herramientas.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CPane (clase)](../../mfc/reference/cpane-class.md)<br/>
[CStatusBar (clase)](../../mfc/reference/cstatusbar-class.md)
