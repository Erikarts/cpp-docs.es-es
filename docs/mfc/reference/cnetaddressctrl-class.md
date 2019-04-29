---
title: Clase CNetDirecciónCtrl
ms.date: 11/19/2018
f1_keywords:
- CNetAddressCtrl
- AFXCMN/CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::Create
- AFXCMN/CNetAddressCtrl::CreateEx
- AFXCMN/CNetAddressCtrl::DisplayErrorTip
- AFXCMN/CNetAddressCtrl::GetAddress
- AFXCMN/CNetAddressCtrl::GetAllowType
- AFXCMN/CNetAddressCtrl::SetAllowType
helpviewer_keywords:
- CNetAddressCtrl [MFC], CNetAddressCtrl
- CNetAddressCtrl [MFC], Create
- CNetAddressCtrl [MFC], CreateEx
- CNetAddressCtrl [MFC], DisplayErrorTip
- CNetAddressCtrl [MFC], GetAddress
- CNetAddressCtrl [MFC], GetAllowType
- CNetAddressCtrl [MFC], SetAllowType
ms.assetid: cb4c6aca-3f49-4b52-b76c-65f57096155b
ms.openlocfilehash: ec4d7aa6f2a1061e632b81a27a0233cf5fdd1c63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62373819"
---
# <a name="cnetaddressctrl-class"></a>Clase CNetDirecciónCtrl

La clase `CNetAddressCtrl` representa el control de dirección de red, que puede utilizar para especificar y validar el formato de direcciones IPv4, IPv6 y DNS con nombre.

## <a name="syntax"></a>Sintaxis

```
class CNetAddressCtrl : public CEdit
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CNetAddressCtrl::CNetAddressCtrl](#cnetaddressctrl)|Construye un objeto `CNetAddressCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CNetAddressCtrl::Create](#create)|Crea un control de dirección de red con los estilos especificados y lo asocia a la actual `CNetAddressCtrl` objeto.|
|[CNetAddressCtrl::CreateEx](#createex)|Crea un control de dirección de red con los estilos extendidos especificados y lo asocia a la actual `CNetAddressCtrl` objeto.|
|[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)|Muestra un globo de sugerencias de error cuando el usuario escribe una dirección de red no admitido en el control de dirección de red actual.|
|[CNetAddressCtrl::GetAddress](#getaddress)|Recupera una representación analizada y validada la dirección de red asociada al control de dirección de red actual.|
|[CNetAddressCtrl::GetAllowType](#getallowtype)|Recupera el tipo de dirección de red que puede admitir el control de dirección de red actual.|
|[CNetAddressCtrl::SetAllowType](#setallowtype)|Establece el tipo de dirección de red que puede admitir el control de dirección de red actual.|

## <a name="remarks"></a>Comentarios

El control de dirección de red, se comprueba que el formato de la dirección que el usuario escribe sea correcto. El control no conectarse realmente a la dirección de red. El [CNetAddressCtrl::SetAllowType](#setallowtype) método especifica uno o varios tipos de dirección que el [CNetAddressCtrl::GetAddress](#getaddress) puede analizar y comprobar el método. Una dirección puede tener el formato de IPv4, IPv6 o dirección con nombre para un servidor, red, host o el destino de mensaje de difusión. Si el formato de la dirección es correcto, puede usar el [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) método para mostrar un cuadro de mensaje de recuadro informativo que señala al cuadro de texto del control de dirección de red gráficamente y muestra predefinido mensaje de error.

El `CNetAddressCtrl` clase se deriva el [CEdit](../../mfc/reference/cedit-class.md) clase. Por lo tanto, el control de dirección de red proporciona acceso a todos los mensajes de control de edición de Windows.

La figura siguiente muestra un cuadro de diálogo que contiene un control de dirección de red. El texto cuadro (1) para el control de dirección de red contiene una dirección de red no válido. Se muestra el mensaje de recuadro informativo (2) si la dirección de red no es válida.

![Cuadro de diálogo con un control de dirección de red y un recuadro informativo. ](../../mfc/reference/media/cnetaddctrl.png "Cuadro de diálogo con un control de dirección de red y un recuadro informativo.")

## <a name="example"></a>Ejemplo

El ejemplo de código siguiente es una parte de un cuadro de diálogo que valida una dirección de red. Los controladores de eventos para los tres botones de radio especifican que la dirección de red puede ser uno de los tres tipos de dirección. El usuario escribe una dirección en el cuadro de texto del control de red, a continuación, presiona un botón para validar la dirección. Si la dirección es válida, se muestra un mensaje de confirmación; en caso contrario, se muestra el mensaje de error predefinidos de recuadro informativo.

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]

## <a name="example"></a>Ejemplo

El siguiente ejemplo de código desde el archivo de encabezado del cuadro de diálogo define el [NC_ADDRESS](/windows/desktop/api/shellapi/ns-shellapi-tagnc_address) y [NET_ADDRESS_INFO](https://msdn.microsoft.com/library/windows/desktop/bb773346) variables que requieren el [CNetAddressCtrl::GetAddress](#getaddress)método.

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CNetAddressCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

Esta clase se admite en Windows Vista y versiones posteriores.

Requisitos adicionales para esta clase se describen en [crear requisitos de Windows Vista controles comunes](../../mfc/build-requirements-for-windows-vista-common-controls.md).

##  <a name="cnetaddressctrl"></a>  CNetAddressCtrl::CNetAddressCtrl

Construye un objeto `CNetAddressCtrl`.

```
CNetAddressCtrl();
```

### <a name="remarks"></a>Comentarios

Use la [CNetAddressCtrl::Create](#create) o [CNetAddressCtrl::CreateEx](#createex) método para crear un control de la red y adjuntarlo a la `CNetAddressCtrl` objeto.

##  <a name="create"></a>  CNetAddressCtrl::Create

Crea un control de dirección de red con los estilos especificados y lo asocia a la actual `CNetAddressCtrl` objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*dwStyle*|[in] Una combinación bit a bit de estilos que se va a aplicarse al control. Para obtener más información, consulte [Editar estilos](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*rect*|[in] Una referencia a un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura que contiene la posición y el tamaño del control.|
|*pParentWnd*|[in] Un puntero no nulo a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es la ventana primaria del control.|
|*nID*|[in] El identificador del control.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

##  <a name="createex"></a>  CNetAddressCtrl::CreateEx

Crea un control de dirección de red con los estilos extendidos especificados y lo asocia a la actual `CNetAddressCtrl` objeto.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*dwExStyle*|[in] Una combinación bit a bit (OR) de los estilos extendidos para aplicarse al control. Para obtener más información, consulte el *dwExStyle* parámetro de la [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) función.|
|*dwStyle*|[in] Una combinación bit a bit (OR) de estilos que se va a aplicarse al control. Para obtener más información, consulte [Editar estilos](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*rect*|[in] Una referencia a un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura que contiene la posición y el tamaño del control.|
|*pParentWnd*|[in] Un puntero no nulo a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es la ventana primaria del control.|
|*nID*|[in] El identificador del control.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

##  <a name="displayerrortip"></a>  CNetAddressCtrl::DisplayErrorTip

Muestra un mensaje de error en el globo de sugerencias asociado al control de dirección de red actual.

```
HRESULT DisplayErrorTip();
```

### <a name="return-value"></a>Valor devuelto

El valor `S_OK` si este método es correcto; en caso contrario, un código de error.

### <a name="remarks"></a>Comentarios

Use la [CNetAddressCtrl::SetAllowType](#setallowtype) método para especificar los tipos de direcciones que puede admitir el control de dirección de red actual. Use la [CNetAddressCtrl::GetAddress](#getaddress) método para validar y analizar la dirección de red que el usuario escribe. Use la [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) método para mostrar un recuadro informativo de mensaje de error si el [CNetAddressCtrl::GetAddress](#getaddress) método es incorrecto.

Este mensaje se invoca el [NetAddr_DisplayErrorTip](/windows/desktop/api/shellapi/nf-shellapi-netaddr_displayerrortip) macro, que se describe en el SDK de Windows. Envía esa macro el `NCM_DISPLAYERRORTIP` mensaje.

##  <a name="getaddress"></a>  CNetAddressCtrl::GetAddress

Recupera una representación analizada y validada la dirección de red que está asociada con el control de dirección de red actual.

```
HRESULT GetAddress(PNC_ADDRESS pAddress) const;
```

### <a name="parameters"></a>Parámetros

*pAddress*<br/>
[in, out] Puntero a un [NC_ADDRESS](/windows/desktop/api/shellapi/ns-shellapi-tagnc_address) estructura.  Establecer el *pAddrInfo* miembro de esta estructura a la dirección de un [NET_ADDRESS_INFO](https://msdn.microsoft.com/library/windows/desktop/bb773346) estructura antes de llamar a GetAddress (método).

### <a name="return-value"></a>Valor devuelto

El valor S_OK si este método se realiza correctamente; en caso contrario, un código de error COM. Para obtener más información acerca de los códigos de error posibles, vea la sección de valor devuelto de la [NetAddr_GetAddress](/windows/desktop/api/shellapi/nf-shellapi-netaddr_getaddress) macro.

### <a name="remarks"></a>Comentarios

Si este método se realiza correctamente, el [NET_ADDRESS_INFO](https://msdn.microsoft.com/library/windows/desktop/bb773346) estructura contiene información adicional acerca de la dirección de red.

Use la [CNetAddressCtrl::SetAllowType](#setallowtype) método para especificar los tipos de direcciones que puede admitir el control de dirección de red actual. Use la [CNetAddressCtrl::GetAddress](#getaddress) método para validar y analizar la dirección de red que el usuario escribe. Use la [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) método para mostrar un recuadro informativo de mensaje de error si el [CNetAddressCtrl::GetAddress](#getaddress) método es incorrecto.

Este método invoca el [NetAddr_GetAddress](/windows/desktop/api/shellapi/nf-shellapi-netaddr_getaddress) macro, que se describe en el SDK de Windows. Esa macro envía el mensaje NCM_GETADDRESS.

##  <a name="getallowtype"></a>  CNetAddressCtrl::GetAllowType

Recupera el tipo de dirección de red que puede admitir el control de dirección de red actual.

```
DWORD GetAllowType() const;
```

### <a name="return-value"></a>Valor devuelto

Una combinación bit a bit (OR) de marcas que especifica los tipos de direcciones que puede admitir el control de dirección de red. Para obtener más información, consulte [NET_STRING](https://msdn.microsoft.com/library/windows/desktop/bb762586).

### <a name="remarks"></a>Comentarios

Este mensaje se invoca el [NetAddr_GetAllowType](/windows/desktop/api/shellapi/nf-shellapi-netaddr_getallowtype) macro, que se describe en el SDK de Windows. Esa macro envía el mensaje NCM_GETALLOWTYPE.

##  <a name="setallowtype"></a>  CNetAddressCtrl::SetAllowType

Establece el tipo de dirección de red que puede admitir el control de dirección de red actual.

```
HRESULT SetAllowType(DWORD dwAddrMask);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*dwAddrMask*|[in] Una combinación bit a bit (OR) de marcas que especifica los tipos de direcciones que puede admitir el control de dirección de red. Para obtener más información, consulte [NET_STRING](https://msdn.microsoft.com/library/windows/desktop/bb762586).|

### <a name="return-value"></a>Valor devuelto

S_OK si este método se realiza correctamente; en caso contrario, un código de error COM.

### <a name="remarks"></a>Comentarios

Use la [CNetAddressCtrl::SetAllowType](#setallowtype) método para especificar los tipos de direcciones que puede admitir el control de dirección de red actual. Use la [CNetAddressCtrl::GetAddress](#getaddress) método para validar y analizar la dirección de red que el usuario escribe. Use la [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) método para mostrar un recuadro informativo de mensaje de error si el [CNetAddressCtrl::GetAddress](#getaddress) método es incorrecto.

Este mensaje se invoca el [NetAddr_SetAllowType](/windows/desktop/api/shellapi/nf-shellapi-netaddr_setallowtype) macro, que se describe en el SDK de Windows. Esa macro envía el mensaje NCM_SETALLOWTYPE.

## <a name="see-also"></a>Vea también

[CNetAddressCtrl (clase)](../../mfc/reference/cnetaddressctrl-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CEdit (clase)](../../mfc/reference/cedit-class.md)
