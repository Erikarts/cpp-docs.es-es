---
title: CPaintDC (clase)
ms.date: 11/04/2016
f1_keywords:
- CPaintDC
- AFXWIN/CPaintDC
- AFXWIN/CPaintDC::CPaintDC
- AFXWIN/CPaintDC::m_ps
- AFXWIN/CPaintDC::m_hWnd
helpviewer_keywords:
- CPaintDC [MFC], CPaintDC
- CPaintDC [MFC], m_ps
- CPaintDC [MFC], m_hWnd
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
ms.openlocfilehash: df1db8a3e65d35f247df7d070119c66b02208815
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772064"
---
# <a name="cpaintdc-class"></a>CPaintDC (clase)

Deriva una clase de contexto de dispositivo [CDC](../../mfc/reference/cdc-class.md).

## <a name="syntax"></a>Sintaxis

```
class CPaintDC : public CDC
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CPaintDC::CPaintDC](#cpaintdc)|Construye un `CPaintDC` conectado a la especificada [CWnd](../../mfc/reference/cwnd-class.md).|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CPaintDC::m_ps](#m_ps)|Contiene el [PAINTSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagpaintstruct) se usa para pintar el área de cliente.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Name|Descripción|
|----------|-----------------|
|[CPaintDC::m_hWnd](#m_hwnd)|El HWND para que este `CPaintDC` está asociado el objeto.|

## <a name="remarks"></a>Comentarios

Realiza una [CWnd:: BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) en tiempo de construcción y [CWnd::EndPaint](../../mfc/reference/cwnd-class.md#endpaint) en tiempo de destrucción.

Un `CPaintDC` objeto sólo se puede usar al responder a un [WM_PAINT](/windows/desktop/gdi/wm-paint) mensajes, normalmente en su `OnPaint` función miembro de controlador de mensajes.

Para obtener más información sobre el uso de `CPaintDC`, consulte [contextos de dispositivo](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cpaintdc"></a>  CPaintDC::CPaintDC

Construye un `CPaintDC` prepara la ventana de la aplicación para dibujar el objeto y almacena el [PAINTSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagpaintstruct) estructura en el [m_ps](#m_ps) variable miembro.

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la `CWnd` objeto al que el `CPaintDC` pertenece el objeto.

### <a name="remarks"></a>Comentarios

Una excepción (de tipo `CResourceException`) se produce si el Windows [GetDC](/windows/desktop/api/winuser/nf-winuser-getdc) llamar se produce un error. Un contexto de dispositivo no puede estar disponible si Windows ya asignado todos sus contextos de dispositivo disponible. La aplicación compite por los cinco contextos mostrar comunes disponibles en un momento dado en Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CPaintDC::m_hWnd

El `HWND` a la que se `CPaintDC` está asociado el objeto.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Comentarios

*m_hWnd* es una variable de tipo HWND protegida.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

##  <a name="m_ps"></a>  CPaintDC::m_ps

`m_ps` es una variable de miembro público del tipo [PAINTSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagpaintstruct).

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>Comentarios

Es el `PAINTSTRUCT` que se pasa a y rellenado por [CWnd:: BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).

El `PAINTSTRUCT` contiene información que la aplicación se usa para pintar el área cliente de la ventana asociada con un `CPaintDC` objeto.

Tenga en cuenta que puede tener acceso al identificador del contexto de dispositivo a través de la `PAINTSTRUCT`. Sin embargo, puede acceder el identificador más directamente a través de la `m_hDC` variable miembro que `CPaintDC` hereda de CDC.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPaintDC::m_hWnd](#m_hwnd).

## <a name="see-also"></a>Vea también

[Ejemplo MDI de MFC](../../overview/visual-cpp-samples.md)<br/>
[CDC (clase)](../../mfc/reference/cdc-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
