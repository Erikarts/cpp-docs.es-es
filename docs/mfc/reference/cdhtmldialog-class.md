---
title: CDHtmlDialog (clase)
ms.date: 03/27/2019
f1_keywords:
- CDHtmlDialog
- AFXDHTML/CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CanAccessExternal
- AFXDHTML/CDHtmlDialog::CreateControlSite
- AFXDHTML/CDHtmlDialog::DDX_DHtml_AxControl
- AFXDHTML/CDHtmlDialog::DDX_DHtml_CheckBox
- AFXDHTML/CDHtmlDialog::DDX_DHtml_ElementText
- AFXDHTML/CDHtmlDialog::DDX_DHtml_Radio
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectIndex
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectString
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectValue
- AFXDHTML/CDHtmlDialog::DestroyModeless
- AFXDHTML/CDHtmlDialog::EnableModeless
- AFXDHTML/CDHtmlDialog::FilterDataObject
- AFXDHTML/CDHtmlDialog::GetControlDispatch
- AFXDHTML/CDHtmlDialog::GetControlProperty
- AFXDHTML/CDHtmlDialog::GetCurrentUrl
- AFXDHTML/CDHtmlDialog::GetDHtmlDocument
- AFXDHTML/CDHtmlDialog::GetDropTarget
- AFXDHTML/CDHtmlDialog::GetElement
- AFXDHTML/CDHtmlDialog::GetElementHtml
- AFXDHTML/CDHtmlDialog::GetElementInterface
- AFXDHTML/CDHtmlDialog::GetElementProperty
- AFXDHTML/CDHtmlDialog::GetElementText
- AFXDHTML/CDHtmlDialog::GetEvent
- AFXDHTML/CDHtmlDialog::GetExternal
- AFXDHTML/CDHtmlDialog::GetHostInfo
- AFXDHTML/CDHtmlDialog::GetOptionKeyPath
- AFXDHTML/CDHtmlDialog::HideUI
- AFXDHTML/CDHtmlDialog::IsExternalDispatchSafe
- AFXDHTML/CDHtmlDialog::LoadFromResource
- AFXDHTML/CDHtmlDialog::Navigate
- AFXDHTML/CDHtmlDialog::OnBeforeNavigate
- AFXDHTML/CDHtmlDialog::OnDocumentComplete
- AFXDHTML/CDHtmlDialog::OnDocWindowActivate
- AFXDHTML/CDHtmlDialog::OnFrameWindowActivate
- AFXDHTML/CDHtmlDialog::OnInitDialog
- AFXDHTML/CDHtmlDialog::OnNavigateComplete
- AFXDHTML/CDHtmlDialog::ResizeBorder
- AFXDHTML/CDHtmlDialog::SetControlProperty
- AFXDHTML/CDHtmlDialog::SetElementHtml
- AFXDHTML/CDHtmlDialog::SetElementProperty
- AFXDHTML/CDHtmlDialog::SetElementText
- AFXDHTML/CDHtmlDialog::SetExternalDispatch
- AFXDHTML/CDHtmlDialog::SetHostFlags
- AFXDHTML/CDHtmlDialog::ShowContextMenu
- AFXDHTML/CDHtmlDialog::ShowUI
- AFXDHTML/CDHtmlDialog::TranslateAccelerator
- AFXDHTML/CDHtmlDialog::TranslateUrl
- AFXDHTML/CDHtmlDialog::UpdateUI
- AFXDHTML/CDHtmlDialog::m_bUseHtmlTitle
- AFXDHTML/CDHtmlDialog::m_nHtmlResID
- AFXDHTML/CDHtmlDialog::m_pBrowserApp
- AFXDHTML/CDHtmlDialog::m_spHtmlDoc
- AFXDHTML/CDHtmlDialog::m_strCurrentUrl
- AFXDHTML/CDHtmlDialog::m_szHtmlResID
helpviewer_keywords:
- CDHtmlDialog [MFC], CDHtmlDialog
- CDHtmlDialog [MFC], CanAccessExternal
- CDHtmlDialog [MFC], CreateControlSite
- CDHtmlDialog [MFC], DDX_DHtml_AxControl
- CDHtmlDialog [MFC], DDX_DHtml_CheckBox
- CDHtmlDialog [MFC], DDX_DHtml_ElementText
- CDHtmlDialog [MFC], DDX_DHtml_Radio
- CDHtmlDialog [MFC], DDX_DHtml_SelectIndex
- CDHtmlDialog [MFC], DDX_DHtml_SelectString
- CDHtmlDialog [MFC], DDX_DHtml_SelectValue
- CDHtmlDialog [MFC], DestroyModeless
- CDHtmlDialog [MFC], EnableModeless
- CDHtmlDialog [MFC], FilterDataObject
- CDHtmlDialog [MFC], GetControlDispatch
- CDHtmlDialog [MFC], GetControlProperty
- CDHtmlDialog [MFC], GetCurrentUrl
- CDHtmlDialog [MFC], GetDHtmlDocument
- CDHtmlDialog [MFC], GetDropTarget
- CDHtmlDialog [MFC], GetElement
- CDHtmlDialog [MFC], GetElementHtml
- CDHtmlDialog [MFC], GetElementInterface
- CDHtmlDialog [MFC], GetElementProperty
- CDHtmlDialog [MFC], GetElementText
- CDHtmlDialog [MFC], GetEvent
- CDHtmlDialog [MFC], GetExternal
- CDHtmlDialog [MFC], GetHostInfo
- CDHtmlDialog [MFC], GetOptionKeyPath
- CDHtmlDialog [MFC], HideUI
- CDHtmlDialog [MFC], IsExternalDispatchSafe
- CDHtmlDialog [MFC], LoadFromResource
- CDHtmlDialog [MFC], Navigate
- CDHtmlDialog [MFC], OnBeforeNavigate
- CDHtmlDialog [MFC], OnDocumentComplete
- CDHtmlDialog [MFC], OnDocWindowActivate
- CDHtmlDialog [MFC], OnFrameWindowActivate
- CDHtmlDialog [MFC], OnInitDialog
- CDHtmlDialog [MFC], OnNavigateComplete
- CDHtmlDialog [MFC], ResizeBorder
- CDHtmlDialog [MFC], SetControlProperty
- CDHtmlDialog [MFC], SetElementHtml
- CDHtmlDialog [MFC], SetElementProperty
- CDHtmlDialog [MFC], SetElementText
- CDHtmlDialog [MFC], SetExternalDispatch
- CDHtmlDialog [MFC], SetHostFlags
- CDHtmlDialog [MFC], ShowContextMenu
- CDHtmlDialog [MFC], ShowUI
- CDHtmlDialog [MFC], TranslateAccelerator
- CDHtmlDialog [MFC], TranslateUrl
- CDHtmlDialog [MFC], UpdateUI
- CDHtmlDialog [MFC], m_bUseHtmlTitle
- CDHtmlDialog [MFC], m_nHtmlResID
- CDHtmlDialog [MFC], m_pBrowserApp
- CDHtmlDialog [MFC], m_spHtmlDoc
- CDHtmlDialog [MFC], m_strCurrentUrl
- CDHtmlDialog [MFC], m_szHtmlResID
ms.assetid: 3f941c85-87e1-4f0f-9cc5-ffee8498b312
ms.openlocfilehash: ec424e433dc84bf4188e349eb6450888aeeeb463
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506900"
---
# <a name="cdhtmldialog-class"></a>CDHtmlDialog (clase)

Se utiliza para crear cuadros de diálogo que utilizan HTML en lugar de recursos de cuadro de diálogo para implementar la interfaz de usuario.

## <a name="syntax"></a>Sintaxis

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDHtmlDialog::CDHtmlDialog](#cdhtmldialog)|Construye un objeto CDHtmlDialog.|
|[CDHtmlDialog::~CDHtmlDialog](#_dtorcdhtmldialog)|Destruye un objeto CDHtmlDialog.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDHtmlDialog::CanAccessExternal](#canaccessexternal)|Reemplazable al que se llama como una comprobación de acceso para ver si los objetos de scripting de la página cargada pueden tener acceso al envío externo del sitio de control. Comprueba que el envío sea seguro para el scripting o que la zona actual permita objetos que no son seguros para el scripting.|
|[CDHtmlDialog::CreateControlSite](#createcontrolsite)|Reemplazable usado para crear una instancia del sitio de control para hospedar el control WebBrowser en el cuadro de diálogo.|
|[CDHtmlDialog::DDX_DHtml_AxControl](#ddx_dhtml_axcontrol)|Intercambia datos entre una variable miembro y el valor de propiedad de un control ActiveX en una página HTML.|
|[CDHtmlDialog::DDX_DHtml_CheckBox](#ddx_dhtml_checkbox)|Intercambia datos entre una variable miembro y una casilla en una página HTML.|
|[CDHtmlDialog::DDX_DHtml_ElementText](#ddx_dhtml_elementtext)|Intercambia datos entre una variable miembro y cualquier propiedad de elemento HTML en una página HTML.|
|[CDHtmlDialog::DDX_DHtml_Radio](#ddx_dhtml_radio)|Intercambia datos entre una variable miembro y un botón de radio de una página HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectIndex](#ddx_dhtml_selectindex)|Obtiene o establece el índice de un cuadro de lista en una página HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectString](#ddx_dhtml_selectstring)|Obtiene o establece el texto para mostrar de una entrada de cuadro de lista (basado en el índice actual) en una página HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectValue](#ddx_dhtml_selectvalue)|Obtiene o establece el valor de una entrada de cuadro de lista (basada en el índice actual) en una página HTML.|
|[CDHtmlDialog::DestroyModeless](#destroymodeless)|Destruye un cuadro de diálogo no modal.|
|[CDHtmlDialog::EnableModeless](#enablemodeless)|Habilita los cuadros de diálogo no modales.|
|[CDHtmlDialog::FilterDataObject](#filterdataobject)|Permite que el cuadro de diálogo filtre los objetos de datos del portapapeles creados por el explorador hospedado.|
|[CDHtmlDialog::GetControlDispatch](#getcontroldispatch)|Recupera la `IDispatch` interfaz en un control ActiveX incrustado en el documento HTML.|
|[CDHtmlDialog::GetControlProperty](#getcontrolproperty)|Recupera la propiedad solicitada del control ActiveX especificado.|
|[CDHtmlDialog::GetCurrentUrl](#getcurrenturl)|Recupera el localizador uniforme de recursos (URL) asociado al documento actual.|
|[CDHtmlDialog::GetDHtmlDocument](#getdhtmldocument)|Recupera la interfaz IHTMLDocument2 en el documento HTML cargado actualmente.|
|[CDHtmlDialog::GetDropTarget](#getdroptarget)|Lo llama el control WebBrowser incluido cuando se usa como destino de colocación para permitir que el cuadro de diálogo proporcione un [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)alternativo.|
|[CDHtmlDialog::GetElement](#getelement)|Obtiene una interfaz en un elemento HTML.|
|[CDHtmlDialog::GetElementHtml](#getelementhtml)|Recupera la `innerHTML` propiedad de un elemento HTML.|
|[CDHtmlDialog::GetElementInterface](#getelementinterface)|Recupera el puntero de interfaz solicitado de un elemento HTML.|
|[CDHtmlDialog::GetElementProperty](#getelementproperty)|Recupera el valor de la propiedad de un elemento HTML.|
|[CDHtmlDialog::GetElementText](#getelementtext)|Recupera la `innerText` propiedad de un elemento HTML.|
|[CDHtmlDialog::GetEvent](#getevent)|Obtiene el `IHTMLEventObj` puntero al objeto de evento actual.|
|[CDHtmlDialog::GetExternal](#getexternal)|Obtiene la interfaz del `IDispatch` host.|
|[CDHtmlDialog::GetHostInfo](#gethostinfo)|Recupera las capacidades de la interfaz de usuario del host.|
|[CDHtmlDialog::GetOptionKeyPath](#getoptionkeypath)|Recupera la clave del registro en la que se almacenan las preferencias del usuario.|
|[CDHtmlDialog::HideUI](#hideui)|Oculta la interfaz de usuario del host.|
|[CDHtmlDialog::IsExternalDispatchSafe](#isexternaldispatchsafe)|Indica si la interfaz del `IDispatch` host es segura para el scripting.|
|[CDHtmlDialog::LoadFromResource](#loadfromresource)|Carga el recurso especificado en el control WebBrowser.|
|[CDHtmlDialog::Navigate](#navigate)|Navega a la dirección URL especificada.|
|[CDHtmlDialog::OnBeforeNavigate](#onbeforenavigate)|Lo llama el marco de trabajo antes de que se desencadene un evento de navegación.|
|[CDHtmlDialog::OnDocumentComplete](#ondocumentcomplete)|Lo llama el marco de trabajo para notificar a una aplicación cuando un documento ha alcanzado el estado READYSTATE_COMPLETE.|
|[CDHtmlDialog::OnDocWindowActivate](#ondocwindowactivate)|Lo llama el marco de trabajo cuando la ventana de documento está activada o desactivada.|
|[CDHtmlDialog::OnFrameWindowActivate](#onframewindowactivate)|Lo llama el marco de trabajo cuando la ventana de marco está activada o desactivada.|
|[CDHtmlDialog::OnInitDialog](#oninitdialog)|Se llama en respuesta al mensaje WM_INITDIALOG.|
|[CDHtmlDialog::OnNavigateComplete](#onnavigatecomplete)|Lo llama el marco de trabajo una vez completado un evento de navegación.|
|[CDHtmlDialog::ResizeBorder](#resizeborder)|Alerta al objeto que necesita para cambiar el tamaño del espacio del borde.|
|[CDHtmlDialog::SetControlProperty](#setcontrolproperty)|Establece la propiedad de un control ActiveX en un nuevo valor.|
|[CDHtmlDialog::SetElementHtml](#setelementhtml)|Establece la `innerHTML` propiedad de un elemento HTML.|
|[CDHtmlDialog::SetElementProperty](#setelementproperty)|Establece una propiedad de un elemento HTML.|
|[CDHtmlDialog::SetElementText](#setelementtext)|Establece la `innerText` propiedad de un elemento HTML.|
|[CDHtmlDialog::SetExternalDispatch](#setexternaldispatch)|Establece la interfaz del `IDispatch` host.|
|[CDHtmlDialog::SetHostFlags](#sethostflags)|Establece las marcas de la interfaz de usuario del host.|
|[CDHtmlDialog::ShowContextMenu](#showcontextmenu)|Se le llama cuando un menú contextual está a punto de mostrarse.|
|[CDHtmlDialog::ShowUI](#showui)|Muestra la interfaz de usuario del host.|
|[CDHtmlDialog::TranslateAccelerator](#translateaccelerator)|Se llama para procesar los mensajes de tecla de aceleración del menú.|
|[CDHtmlDialog::TranslateUrl](#translateurl)|Se llama para modificar la dirección URL que se va a cargar.|
|[CDHtmlDialog::UpdateUI](#updateui)|Se llama para notificar al host que el estado del comando ha cambiado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDHtmlDialog::m_bUseHtmlTitle](#m_busehtmltitle)|Indica si se va a usar el título del documento HTML como título del cuadro de diálogo.|
|[CDHtmlDialog::m_nHtmlResID](#m_nhtmlresid)|IDENTIFICADOR de recurso del recurso HTML que se va a mostrar.|
|[CDHtmlDialog::m_pBrowserApp](#m_pbrowserapp)|Puntero a una aplicación de explorador Web.|
|[CDHtmlDialog::m_spHtmlDoc](#m_sphtmldoc)|Un puntero a un documento HTML.|
|[CDHtmlDialog::m_strCurrentUrl](#m_strcurrenturl)|La dirección URL actual.|
|[CDHtmlDialog::m_szHtmlResID](#m_szhtmlresid)|Versión de cadena del identificador de recurso HTML.|

## <a name="remarks"></a>Comentarios

`CDHtmlDialog`puede cargar el código HTML que se va a mostrar desde un recurso HTML o una dirección URL.

`CDHtmlDialog`también puede realizar el intercambio de datos con controles HTML y controlar eventos de controles HTML, como clics en botones.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

`CDHtmlDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdhtml. h

##  <a name="ddx_dhtml_helper_macros"></a>Macros auxiliares de DDX_DHtml

Las macros auxiliares de DDX_DHtml permiten el acceso sencillo a las propiedades de los controles que se usan habitualmente en una página HTML.

### <a name="data-exchange-macros"></a>Macros de intercambio de datos

|||
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|Establece o recupera la propiedad Value del control seleccionado.|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|Establece o recupera el texto entre las etiquetas inicial y final del elemento actual.|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|Establece o recupera el código HTML entre las etiquetas inicial y final del elemento actual.|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|Establece o recupera la dirección URL de destino o el punto de anclaje.|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|Establece o recupera la ventana o el marco de destino.|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|Establece o recupera el nombre de una imagen o de un clip de vídeo en el documento.|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|Establece o recupera la dirección URL del marco asociado.|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|Establece o recupera la dirección URL del marco asociado.|

##  <a name="canaccessexternal"></a>  CDHtmlDialog::CanAccessExternal

Reemplazable al que se llama como una comprobación de acceso para ver si los objetos de scripting de la página cargada pueden tener acceso al envío externo del sitio de control. Comprueba que el envío sea seguro para el scripting o que la zona actual permita objetos que no son seguros para el scripting.

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="cdhtmldialog"></a>  CDHtmlDialog::CDHtmlDialog

Crea un cuadro de diálogo HTML dinámico basado en recursos.

```
CDHtmlDialog();

CDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID,
    CWnd *pParentWnd = NULL);

CDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd *pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszTemplateName*<br/>
Cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.

*szHtmlResID*<br/>
Cadena terminada en null que es el nombre de un recurso HTML.

*pParentWnd*<br/>
Puntero al objeto de ventana primario o propietario (de tipo [CWnd](../../mfc/reference/cwnd-class.md)) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

*nIDTemplate*<br/>
Contiene el número de identificación de un recurso de plantilla de cuadro de diálogo.

*nHtmlResID*<br/>
Contiene el número de identificador de un recurso HTML.

### <a name="remarks"></a>Comentarios

La segunda forma del constructor proporciona acceso al recurso de cuadro de diálogo a través del nombre de la plantilla. La tercera forma del constructor proporciona acceso al recurso de cuadro de diálogo a través del identificador de la plantilla de recursos. Normalmente, el identificador comienza con el prefijo **IDD_** .

##  <a name="_dtorcdhtmldialog"></a>  CDHtmlDialog::~CDHtmlDialog

Destruye un objeto CDHtmlDialog.

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>Comentarios

La función miembro [CWnd::D estroywindow](../../mfc/reference/cwnd-class.md#destroywindow) se debe usar para destruir los cuadros de diálogo no modales creados por [CDialog:: Create](../../mfc/reference/cdialog-class.md#create).

##  <a name="createcontrolsite"></a>  CDHtmlDialog::CreateControlSite

Reemplazable usado para crear una instancia del sitio de control para hospedar el control WebBrowser en el cuadro de diálogo.

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>Parámetros

*pContainer*<br/>
Un puntero al objeto [COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)

*ppSite*<br/>
Un puntero a un puntero a un [COleControlSite](../../mfc/reference/colecontrolsite-class.md).

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Puede invalidar esta función miembro para que devuelva una instancia de su propia clase de sitio de control.

##  <a name="ddx_dhtml_axcontrol"></a>  CDHtmlDialog::DDX_DHtml_AxControl

Intercambia datos entre una variable miembro y el valor de propiedad de un control ActiveX en una página HTML.

```
void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    VARIANT& var);

void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    LPCTSTR szPropName,
    VARIANT& var);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) .

*szId*<br/>
Valor del parámetro de identificador de la etiqueta de objeto en el origen HTML del control ActiveX.

*dispId*<br/>
El identificador de envío de la propiedad con la que desea intercambiar los datos.

*szPropName*<br/>
Nombre de la propiedad.

*var*<br/>
El miembro de datos, de tipo VARIANT, [COleVariant](../../mfc/reference/colevariant-class.md)o [CComVariant](../../atl/reference/ccomvariant-class.md), que contiene el valor intercambiado con la propiedad de control ActiveX.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

##  <a name="ddx_dhtml_checkbox"></a>  CDHtmlDialog::DDX_DHtml_CheckBox

Intercambia datos entre una variable miembro y una casilla en una página HTML.

```
void DDX_DHtml_CheckBox(
    CDataExchange* pDX,
    LPCTSTR szId,
    int& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) .

*szId*<br/>
Valor especificado para el parámetro de identificador del control HTML.

*value*<br/>
Valor que se va a intercambiar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

##  <a name="ddx_dhtml_elementtext"></a>  CDHtmlDialog::DDX_DHtml_ElementText

Intercambia datos entre una variable miembro y cualquier propiedad de elemento HTML en una página HTML.

```
void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    CString& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    short& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    int& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    long& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    DWORD& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    float& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    double& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) .

*szId*<br/>
Valor especificado para el parámetro de identificador del control HTML.

*dispId*<br/>
El identificador de envío del elemento HTML con el que desea intercambiar datos.

*value*<br/>
Valor que se va a intercambiar.

##  <a name="ddx_dhtml_radio"></a>  CDHtmlDialog::DDX_DHtml_Radio

Intercambia datos entre una variable miembro y un botón de radio de una página HTML.

```
void DDX_DHtml_Radio(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) .

*szId*<br/>
Valor especificado para el parámetro de identificador del control HTML.

*value*<br/>
Valor que se va a intercambiar.

##  <a name="ddx_dhtml_selectindex"></a>  CDHtmlDialog::DDX_DHtml_SelectIndex

Obtiene o establece el índice de un cuadro de lista en una página HTML.

```
void DDX_DHtml_SelectIndex(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) .

*szId*<br/>
Valor especificado para el parámetro del `id` control HTML.

*value*<br/>
Valor que se va a intercambiar.

##  <a name="ddx_dhtml_selectstring"></a>  CDHtmlDialog::DDX_DHtml_SelectString

Obtiene o establece el texto para mostrar de una entrada de cuadro de lista (basado en el índice actual) en una página HTML.

```
void DDX_DHtml_SelectString(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) .

*szId*<br/>
Valor especificado para el parámetro de identificador del control HTML.

*value*<br/>
Valor que se va a intercambiar.

##  <a name="ddx_dhtml_selectvalue"></a>  CDHtmlDialog::DDX_DHtml_SelectValue

Obtiene o establece el valor de una entrada de cuadro de lista (basada en el índice actual) en una página HTML.

```
void DDX_DHtml_SelectValue(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) .

*szId*<br/>
Valor especificado para el parámetro de identificador del control HTML.

*value*<br/>
Valor que se va a intercambiar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

##  <a name="destroymodeless"></a>  CDHtmlDialog::DestroyModeless

Desasocia un cuadro de diálogo no modal del `CDHtmlDialog` objeto y destruye el objeto.

```
void DestroyModeless();
```

##  <a name="enablemodeless"></a>  CDHtmlDialog::EnableModeless

Habilita los cuadros de diálogo no modales.

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>Parámetros

*fEnable*<br/>
Vea *fEnable* en [IDocHostUIHandler:: EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler:: EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)), tal y como se describe en el Windows SDK.

##  <a name="filterdataobject"></a>  CDHtmlDialog::FilterDataObject

Permite que el cuadro de diálogo filtre los objetos de datos del portapapeles creados por el explorador hospedado.

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>Parámetros

*pDO*<br/>
Consulte *pDO* in [IDocHostUIHandler:: FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)) en el Windows SDK.

*ppDORet*<br/>
Vea *ppDORet* en `IDocHostUIHandler::FilterDataObject` en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve S_FALSE.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler:: FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)), tal y como se describe en el Windows SDK.

##  <a name="getcontroldispatch"></a>  CDHtmlDialog::GetControlDispatch

Recupera la `IDispatch` interfaz en un control ActiveX incrustado en el documento HTML devuelto por [GetDHtmlDocument](#getdhtmldocument).

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>Parámetros

*szId*<br/>
IDENTIFICADOR HTML de un control ActiveX.

*ppdisp*<br/>
La `IDispatch` interfaz del control, si se encuentra en la Página Web.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="getcontrolproperty"></a>  CDHtmlDialog::GetControlProperty

Recupera la propiedad solicitada del control ActiveX especificado.

```
VARIANT GetControlProperty(
    LPCTSTR szId,
    LPCTSTR szPropName);

VARIANT GetControlProperty(
    LPCTSTR szId,
    DISPID dispId);

VARIANT GetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId);
```

### <a name="parameters"></a>Parámetros

*szId*<br/>
IDENTIFICADOR HTML de un control ActiveX.

*szPropName*<br/>
Nombre de una propiedad de la configuración regional predeterminada del usuario actual.

*pdispControl*<br/>
`IDispatch` Puntero de un control ActiveX.

*dispId*<br/>
El identificador de envío de una propiedad.

### <a name="return-value"></a>Valor devuelto

Variante que contiene la propiedad solicitada o una variante vacía si no se pudo encontrar el control o la propiedad.

### <a name="remarks"></a>Comentarios

Las sobrecargas se muestran desde la menos eficaz en la parte superior a la más eficaz en la parte inferior.

##  <a name="getcurrenturl"></a>  CDHtmlDialog::GetCurrentUrl

Recupera el localizador uniforme de recursos (URL) asociado al documento actual.

```
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>Parámetros

*szUrl*<br/>
Objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la dirección URL que se va a recuperar.

##  <a name="getdhtmldocument"></a>  CDHtmlDialog::GetDHtmlDocument

Recupera la interfaz [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) en el documento HTML cargado actualmente.

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>Parámetros

pphtmlDoc puntero a un puntero a un documento HTML.  *\* \**

### <a name="return-value"></a>Valor devuelto

HRESULT estándar. Devuelve S_OK si se realiza correctamente.

##  <a name="getdroptarget"></a>  CDHtmlDialog::GetDropTarget

Lo llama el control WebBrowser incluido cuando se usa como destino de colocación para permitir que el cuadro de diálogo proporcione un [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)alternativo.

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>Parámetros

*pDropTarget*<br/>
Vea *pDropTarget* en [IDocHostUIHandler:: GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)) en el Windows SDK.

*ppDropTarget*<br/>
Vea *ppDropTarget* en `IDocHostUIHandler::GetDropTarget` en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler:: GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)), tal y como se describe en el Windows SDK.

##  <a name="getelement"></a>  CDHtmlDialog::GetElement

Devuelve una interfaz en el elemento HTML especificado por *szElementId*.

```
HRESULT GetElement(
    LPCTSTR szElementId,
    IDispatch** ppdisp,
    BOOL* pbCollection = NULL);

HRESULT GetElement(
    LPCTSTR szElementId,
    IHTMLElement** pphtmlElement);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
IDENTIFICADOR de un elemento HTML.

*ppdisp*<br/>
`IDispatch` Puntero al elemento o colección de elementos solicitados.

*pbCollection*<br/>
Un valor BOOLEANO que indica si el objeto representado por *ppdisp* es un elemento único o una colección de elementos.

*pphtmlElement*<br/>
`IHTMLElement` Puntero al elemento solicitado.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Use la primera sobrecarga si necesita controlar las condiciones en las que puede haber más de un elemento con el identificador especificado. Puede usar el último parámetro para averiguar si el puntero de interfaz devuelto es a una colección o un elemento único. Si el puntero de interfaz se encuentra en una colección, puede consultar `IHTMLElementCollection` y usar su `item` propiedad para hacer referencia a los elementos por posición ordinal.

La segunda sobrecarga producirá un error si hay más de un elemento con el mismo identificador en la página.

##  <a name="getelementhtml"></a>  CDHtmlDialog::GetElementHtml

Recupera la `innerHTML` propiedad del elemento HTML identificado por *szElementId*.

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
IDENTIFICADOR de un elemento HTML.

### <a name="return-value"></a>Valor devuelto

La `innerHTML` propiedad del elemento HTML identificado por *szElementId* o null si no se encuentra el elemento.

##  <a name="getelementinterface"></a>  CDHtmlDialog::GetElementInterface

Recupera el puntero de interfaz solicitado del elemento HTML identificado por *szElementId*.

```
template <class Q> HRESULT GetElementInterface(
    LPCTSTR szElementId,
    Q** ppvObj);

HRESULT GetElementInterface(
    LPCTSTR szElementId,
    REFIID refiid,
    void** ppvObj);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
IDENTIFICADOR de un elemento HTML.

*ppvObj*<br/>
Dirección de un puntero que se rellenará con el puntero de interfaz solicitado si se encuentra el elemento y la consulta se realiza correctamente.

*refiid*<br/>
IDENTIFICADOR de interfaz (IID) de la interfaz solicitada.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

##  <a name="getelementproperty"></a>  CDHtmlDialog::GetElementProperty

Recupera el valor de la propiedad identificada por *DISPID* del elemento HTML identificado por *szElementId*.

```
VARIANT GetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
IDENTIFICADOR de un elemento HTML.

*dispId*<br/>
El identificador de envío de una propiedad.

### <a name="return-value"></a>Valor devuelto

El valor de la propiedad o una variante vacía si no se encontró la propiedad o el elemento.

##  <a name="getelementtext"></a>  CDHtmlDialog::GetElementText

Recupera la `innerText` propiedad del elemento HTML identificado por *szElementId*.

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
IDENTIFICADOR de un elemento HTML.

### <a name="return-value"></a>Valor devuelto

La `innerText` propiedad del elemento HTML identificado por *szElementId* o null si no se encontró la propiedad o el elemento.

##  <a name="getevent"></a>  CDHtmlDialog::GetEvent

Devuelve el `IHTMLEventObj` puntero al objeto de evento actual.

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>Parámetros

*ppEventObj*<br/>
Dirección de un puntero que se rellenará con `IHTMLEventObj` el puntero de interfaz.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Solo se debe llamar a esta función desde dentro de un controlador de eventos DHTML.

##  <a name="getexternal"></a>  CDHtmlDialog::GetExternal

Obtiene la interfaz del `IDispatch` host.

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>Parámetros

*ppDispatch*<br/>
Vea *ppDispatch* en [IDocHostUIHandler:: GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se realiza correctamente o E_NOTIMPL en caso de error.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler:: GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)), tal y como se describe en el Windows SDK.

##  <a name="gethostinfo"></a>  CDHtmlDialog::GetHostInfo

Recupera las capacidades de la interfaz de usuario del host.

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>Parámetros

*pInfo*<br/>
Vea *Pinfo* en [IDocHostUIHandler:: GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler:: GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)), tal y como se describe en el Windows SDK.

##  <a name="getoptionkeypath"></a>  CDHtmlDialog::GetOptionKeyPath

Recupera la clave del registro en la que se almacenan las preferencias del usuario.

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>Parámetros

*pchKey*<br/>
Vea *pchKey* en [IDocHostUIHandler:: GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)) en el Windows SDK.

*dw*<br/>
Vea *DW* en `IDocHostUIHandler::GetOptionKeyPath` en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler:: GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)), tal y como se describe en el Windows SDK.

##  <a name="hideui"></a>  CDHtmlDialog::HideUI

Oculta la interfaz de usuario del host.

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler:: HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\)), tal y como se describe en el Windows SDK.

##  <a name="isexternaldispatchsafe"></a>  CDHtmlDialog::IsExternalDispatchSafe

Indica si la interfaz del `IDispatch` host es segura para el scripting.

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>Valor devuelto

Devuelve FALSE.

##  <a name="loadfromresource"></a>  CDHtmlDialog::LoadFromResource

Carga el recurso especificado en el control WebBrowser en el cuadro de diálogo DHTML.

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>Parámetros

*lpszResource*<br/>
Puntero a una cadena que contiene el nombre del recurso que se va a cargar.

*nRes*<br/>
IDENTIFICADOR del recurso que se va a cargar.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

##  <a name="m_busehtmltitle"></a>  CDHtmlDialog::m_bUseHtmlTitle

Indica si se va a usar el título del documento HTML como título del cuadro de diálogo.

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>Comentarios

Si **m**_ **bUseHtmlTitle** es true, el título del cuadro de diálogo se establece igual al título del documento HTML; de lo contrario, se usa el título del recurso de diálogo.

##  <a name="m_nhtmlresid"></a>  CDHtmlDialog::m_nHtmlResID

IDENTIFICADOR de recurso del recurso HTML que se va a mostrar.

```
UINT m_nHtmlResID;
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

##  <a name="m_pbrowserapp"></a>  CDHtmlDialog::m_pBrowserApp

Puntero a una aplicación de explorador Web.

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

##  <a name="m_sphtmldoc"></a>  CDHtmlDialog::m_spHtmlDoc

Un puntero a un documento HTML.

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

##  <a name="m_strcurrenturl"></a>  CDHtmlDialog::m_strCurrentUrl

La dirección URL actual.

```
CString m_strCurrentUrl;
```

##  <a name="m_szhtmlresid"></a>  CDHtmlDialog::m_szHtmlResID

Versión de cadena del identificador de recurso HTML.

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

##  <a name="navigate"></a>  CDHtmlDialog::Navigate

Navega al recurso identificado por la dirección URL especificada por *lpszURL*.

```
void Navigate(
    LPCTSTR lpszURL,
    DWORD dwFlags = 0,
    LPCTSTR lpszTargetFrameName = NULL,
    LPCTSTR lpszHeaders = NULL,
    LPVOID lpvPostData = NULL,
    DWORD dwPostDataLen = 0);
```

### <a name="parameters"></a>Parámetros

*lpszURL*<br/>
Un puntero a una cadena que contiene la dirección URL que se va a usar como destino.

*dwFlags*<br/>
Marcas de una variable que especifica si se debe agregar el recurso a la lista de historial, si se va a leer o escribir en la memoria caché, y si se va a mostrar el recurso en una nueva ventana. La variable puede ser una combinación de los valores definidos por la enumeración [BrowserNavConstants](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\)) .

*lpszTargetFrameName*<br/>
Puntero a una cadena que contiene el nombre del marco en el que se va a mostrar el recurso.

*lpszHeaders*<br/>
Un puntero a un valor que especifica los encabezados HTTP que se van a enviar al servidor. Estos encabezados se agregan a los encabezados predeterminados de Internet Explorer. Los encabezados pueden especificar tal información como la acción requerida del servidor, el tipo de datos que se pasan al servidor o un código de estado. Este parámetro se omite si la dirección URL no es una dirección URL HTTP.

*lpvPostData*<br/>
Puntero a los datos que se van a enviar con la transacción HTTP POST. Por ejemplo, la transacción POST se utiliza para enviar los datos recopilados por un formulario HTML. Si este parámetro no especifica ningún dato post, `Navigate` emite una transacción HTTP GET. Este parámetro se omite si la dirección URL no es una dirección URL HTTP.

*dwPostDataLen*<br/>
Datos que se van a enviar con la transacción HTTP POST. Por ejemplo, la transacción POST se utiliza para enviar los datos recopilados por un formulario HTML. Si este parámetro no especifica ningún dato post, `Navigate` emite una transacción HTTP GET. Este parámetro se omite si la dirección URL no es una dirección URL HTTP.

##  <a name="onbeforenavigate"></a>  CDHtmlDialog::OnBeforeNavigate

Lo llama el marco de trabajo para que se desencadene un evento antes de que se produzca una navegación.

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
Puntero a un objeto `IDispatch`.

*szUrl*<br/>
Puntero a una cadena que contiene la dirección URL a la que se va a navegar.

##  <a name="ondocumentcomplete"></a>  CDHtmlDialog::OnDocumentComplete

Lo llama el marco de trabajo para notificar a una aplicación cuando un documento ha logrado el estado READYSTATE_COMPLETE.

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
Puntero a un objeto `IDispatch`.

*szUrl*<br/>
Puntero a una cadena que contiene la dirección URL a la que se navegó.

##  <a name="ondocwindowactivate"></a>  CDHtmlDialog::OnDocWindowActivate

Lo llama el marco de trabajo cuando la ventana de documento está activada o desactivada.

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parámetros

*fActivate*<br/>
Vea *fActivate* en [IDocHostUIHandler:: OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler:: OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)), tal y como se describe en el Windows SDK.

##  <a name="onframewindowactivate"></a>  CDHtmlDialog::OnFrameWindowActivate

Lo llama el marco de trabajo cuando la ventana de marco está activada o desactivada.

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parámetros

*fActivate*<br/>
Vea *fActivate* en [IDocHostUIHandler:: OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler:: OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)), tal y como se describe en el Windows SDK.

##  <a name="oninitdialog"></a>  CDHtmlDialog::OnInitDialog

Se llama en respuesta al mensaje WM_INITDIALOG.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve TRUE.

### <a name="remarks"></a>Comentarios

Este mensaje se envía al cuadro de diálogo durante las `Create` `CreateIndirect`llamadas a, `DoModal` o, que se producen inmediatamente antes de que se muestre el cuadro de diálogo.

Invalide esta función miembro si necesita realizar un procesamiento especial cuando se inicializa el cuadro de diálogo. En la versión invalidada, llame primero a la `OnInitDialog` clase base pero omita el valor devuelto. Normalmente, devolverá TRUE desde la función miembro invalidada.

Windows llama a `OnInitDialog` la función mediante el procedimiento de cuadro de diálogo global estándar común a todos los cuadros de diálogo de biblioteca MFC, en lugar de a través del mapa de mensajes, por lo que no se necesita una entrada de mapa de mensajes para esta función miembro.

##  <a name="onnavigatecomplete"></a>  CDHtmlDialog::OnNavigateComplete

Lo llama el marco de trabajo después de que se complete la navegación a la dirección URL especificada.

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
Puntero a un objeto `IDispatch`.

*szUrl*<br/>
Puntero a una cadena que contiene la dirección URL a la que se navegó.

##  <a name="resizeborder"></a>  CDHtmlDialog::ResizeBorder

Alerta al objeto que necesita para cambiar el tamaño del espacio del borde.

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>Parámetros

*prcBorder*<br/>
Vea *prcBorder* en [IDocHostUIHandler:: ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\)) en el Windows SDK.

*pUIWindow*<br/>
Vea *pUIWindow* en `IDocHostUIHandler::ResizeBorder` en el Windows SDK.

*fFrameWindow*<br/>
Vea *fFrameWindow* en `IDocHostUIHandler::ResizeBorder` en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

##  <a name="setcontrolproperty"></a>  CDHtmlDialog::SetControlProperty

Establece la propiedad de un control ActiveX en un nuevo valor.

```
void SetControlProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    LPCTSTR szElementId,
    LPCTSTR szPropName,
    VARIANT* pVar);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
IDENTIFICADOR HTML de un control ActiveX.

*dispId*<br/>
IDENTIFICADOR de envío de la propiedad que se va a establecer.

*pVar*<br/>
Puntero a un tipo VARIANT que contiene el nuevo valor de propiedad.

*pdispControl*<br/>
Puntero a la interfaz de `IDispatch` un control ActiveX.

*szPropName*<br/>
Cadena que contiene el nombre de la propiedad que se va a establecer.

##  <a name="setelementhtml"></a>  CDHtmlDialog::SetElementHtml

Establece la `innerHTML` propiedad de un elemento HTML.

```
void SetElementHtml(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementHtml(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
IDENTIFICADOR de un elemento HTML.

*bstrText*<br/>
Nuevo valor de la propiedad `innerHTML`.

*punkElem*<br/>
`IUnknown` Puntero de un elemento HTML.

##  <a name="setelementproperty"></a>  CDHtmlDialog::SetElementProperty

Establece una propiedad de un elemento HTML.

```
void SetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
IDENTIFICADOR de un elemento HTML.

*dispId*<br/>
IDENTIFICADOR de envío de la propiedad que se va a establecer.

*pVar*<br/>
Nuevo valor de la propiedad.

##  <a name="setelementtext"></a>  CDHtmlDialog::SetElementText

Establece la `innerText` propiedad de un elemento HTML.

```
void SetElementText(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementText(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
IDENTIFICADOR de un elemento HTML.

*bstrText*<br/>
Nuevo valor de la propiedad `innerText`.

*punkElem*<br/>
`IUnknown` Puntero de un elemento HTML.

##  <a name="setexternaldispatch"></a>  CDHtmlDialog::SetExternalDispatch

Establece la interfaz del `IDispatch` host.

```
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>Parámetros

*pdispExternal*<br/>
La nueva `IDispatch` interfaz.

##  <a name="sethostflags"></a>  CDHtmlDialog::SetHostFlags

Establece las marcas de la interfaz de usuario del host.

```
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Para ver los valores posibles, vea [DOCHOSTUIFLAG](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\)) en el Windows SDK.

##  <a name="showcontextmenu"></a>  CDHtmlDialog::ShowContextMenu

Se le llama cuando un menú contextual está a punto de mostrarse.

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>Parámetros

*dwID*<br/>
Vea *dwID* en [IDocHostUIHandler:: ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)) en el Windows SDK.

*ppt*<br/>
Vea *PPT* in `IDocHostUIHandler::ShowContextMenu` en el Windows SDK.

*pcmdtReserved*<br/>
Vea *pcmdtReserved* en `IDocHostUIHandler::ShowContextMenu` en el Windows SDK.

*pdispReserved*<br/>
Vea *pdispReserved* en `IDocHostUIHandler::ShowContextMenu` en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve S_FALSE.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler:: ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)), tal y como se describe en el Windows SDK.

##  <a name="showui"></a>  CDHtmlDialog::ShowUI

Muestra la interfaz de usuario del host.

```
STDMETHOD(ShowUI)(
    DWORD dwID,
    IOleInPlaceActiveObject* pActiveObject,
    IOleCommandTarget* pCommandTarget,
    IOleInPlaceFrame* pFrame,
    IOleInPlaceUIWindow* pDoc);
```

### <a name="parameters"></a>Parámetros

*dwID*<br/>
Vea *dwID* en [IDocHostUIHandler:: ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)) en el Windows SDK.

*pActiveObject*<br/>
Vea *d pActiveObject* in `IDocHostUIHandler::ShowUI` en el Windows SDK.

*pCommandTarget*<br/>
Vea *pCommandTarget* en `IDocHostUIHandler::ShowUI` en el Windows SDK.

*pFrame*<br/>
Vea *pFrame* en `IDocHostUIHandler::ShowUI` en el Windows SDK.

*pDoc*<br/>
Vea *pDoc* en `IDocHostUIHandler::ShowUI` en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve S_FALSE.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler:: ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)), tal como se describe en el Windows SDK.

##  <a name="translateaccelerator"></a>  CDHtmlDialog::TranslateAccelerator

Se llama para procesar los mensajes de tecla de aceleración del menú.

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>Parámetros

*lpMsg*<br/>
Vea *lpMsg* en [IDocHostUIHandler:: TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)) en el Windows SDK.

*pguidCmdGroup*<br/>
Vea *pguidCmdGroup* en `IDocHostUIHandler::TranslateAccelerator` en el Windows SDK.

*nCmdID*<br/>
Vea *nCmdID* en `IDocHostUIHandler::TranslateAccelerator` en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve S_FALSE.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler:: TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)), tal como se describe en el Windows SDK.

##  <a name="translateurl"></a>  CDHtmlDialog::TranslateUrl

Se llama para modificar la dirección URL que se va a cargar.

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>Parámetros

*dwTranslate*<br/>
Vea *dwTranslate* en [IDocHostUIHandler:: TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)) en el Windows SDK.

*pchURLIn*<br/>
Vea *pchURLIn* en `IDocHostUIHandler::TranslateUrl` en el Windows SDK.

*ppchURLOut*<br/>
Vea *ppchURLOut* en `IDocHostUIHandler::TranslateUrl` en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve S_FALSE.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler:: TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)), tal y como se describe en el Windows SDK.

##  <a name="updateui"></a>  CDHtmlDialog::UpdateUI

Se llama para notificar al host que el estado del comando ha cambiado.

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler:: updateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\)), tal como se describe en el Windows SDK.

## <a name="see-also"></a>Vea también

[Ejemplo DHtmlExplore de MFC](../../overview/visual-cpp-samples.md)<br/>
[DDX_DHtml (macros del asistente)](#ddx_dhtml_helper_macros)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
