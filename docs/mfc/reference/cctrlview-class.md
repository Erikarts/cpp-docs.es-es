---
title: Clase CCtrlView
ms.date: 11/04/2016
f1_keywords:
- CCtrlView
- AFXWIN/CCtrlView
- AFXWIN/CCtrlView::CCtrlView
- AFXWIN/CCtrlView::OnDraw
- AFXWIN/CCtrlView::PreCreateWindow
- AFXWIN/CCtrlView::m_dwDefaultStyle
- AFXWIN/CCtrlView::m_strClass
helpviewer_keywords:
- CCtrlView [MFC], CCtrlView
- CCtrlView [MFC], OnDraw
- CCtrlView [MFC], PreCreateWindow
- CCtrlView [MFC], m_dwDefaultStyle
- CCtrlView [MFC], m_strClass
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
ms.openlocfilehash: 334f139b81afeb06d57cbd128abe9e413b1fd0e7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507146"
---
# <a name="cctrlview-class"></a>Clase CCtrlView

Adapta la arquitectura de vista-documento a los controles comunes admitidos por las versiones 3.51 y posteriores de Windows 98 y Windows NT.

## <a name="syntax"></a>Sintaxis

```
class CCtrlView : public CView
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CCtrlView::CCtrlView](#cctrlview)|Construye un objeto `CCtrlView`.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CCtrlView::OnDraw](#ondraw)|Lo llama el marco de trabajo para dibujar mediante el contexto de dispositivo especificado.|
|[CCtrlView::PreCreateWindow](#precreatewindow)|Se llama antes de crear la ventana de Windows asociada a este objeto `CCtrlView`.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|Contiene el estilo predeterminado de la clase de vista.|
|[CCtrlView::m_strClass](#m_strclass)|Contiene el nombre de clase de Windows para la clase de vista.|

## <a name="remarks"></a>Comentarios

La clase `CCtrlView` y sus derivados, [CEditView](../../mfc/reference/ceditview-class.md), [CListView](../../mfc/reference/clistview-class.md), [CTreeView](../../mfc/reference/ctreeview-class.md)y [CRichEditView](../../mfc/reference/cricheditview-class.md), adaptan la arquitectura de la vista del documento a los nuevos controles comunes admitidos por las versiones de Windows 95/98 y Windows NT 3,51 y versiones posteriores. Para obtener más información sobre la arquitectura de vista-documento, vea [arquitectura documento/vista](../../mfc/document-view-architecture.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CCtrlView`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cctrlview"></a>  CCtrlView::CCtrlView

Construye un objeto `CCtrlView`.

```
CCtrlView(
    LPCTSTR lpszClass,
    DWORD dwStyle);
```

### <a name="parameters"></a>Parámetros

*lpszClass*<br/>
Nombre de clase de Windows de la clase de vista.

*dwStyle*<br/>
Estilo de la clase de vista.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama al constructor cuando se crea una nueva ventana de marco o se divide una ventana. Invalide [CView:: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) para inicializar la vista después de adjuntar el documento. Llame a [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) o [CWnd:: CreateEx](../../mfc/reference/cwnd-class.md#createex) para crear el objeto de Windows.

##  <a name="m_strclass"></a>  CCtrlView::m_strClass

Contiene el nombre de clase de Windows para la clase de vista.

```
CString m_strClass;
```

##  <a name="m_dwdefaultstyle"></a>  CCtrlView::m_dwDefaultStyle

Contiene el estilo predeterminado de la clase de vista.

```
DWORD m_dwDefaultStyle;
```

### <a name="remarks"></a>Comentarios

Este estilo se aplica cuando se crea una ventana.

##  <a name="ondraw"></a>  CCtrlView::OnDraw

Lo llama el marco de trabajo para dibujar el contenido `CCtrlView` del objeto utilizando el contexto de dispositivo especificado.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Un puntero al contexto de dispositivo en el que se produce el dibujo.

### <a name="remarks"></a>Comentarios

`OnDraw`normalmente se llama para mostrar la pantalla y pasar un contexto de dispositivo de pantalla especificado por *pDC*.

##  <a name="precreatewindow"></a>  CCtrlView::PreCreateWindow

Se llama antes de crear la ventana de Windows asociada a este objeto `CWnd`.

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Parámetros

*cs*<br/>
Una estructura [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw) .

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la creación de la ventana debe continuar; 0 para indicar un error de creación.

### <a name="remarks"></a>Comentarios

Nunca llame directamente a esta función.

La implementación predeterminada de esta función comprueba un nombre de clase de ventana NULL y sustituye un valor predeterminado adecuado. Invalide esta función miembro para `CREATESTRUCT` modificar la estructura antes de que se cree la ventana.

Cada clase derivada de `CCtrlView` agrega su propia funcionalidad a su invalidación `PreCreateWindow`de. Por diseño, estas derivaciones de `PreCreateWindow` no están documentadas. Para determinar los estilos adecuados para cada clase y las interdependencias entre los estilos, puede examinar el código fuente de MFC para la clase base de la aplicación. Si elige invalidar `PreCreateWindow`, puede determinar si los estilos utilizados en la clase base de la aplicación proporcionan la funcionalidad que necesita mediante el uso de la información recopilada del código fuente de MFC.

Para obtener más información sobre cómo cambiar los estilos de ventana, vea el [cambio de los estilos de una ventana creada por MFC](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Vea también

[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CTreeView (clase)](../../mfc/reference/ctreeview-class.md)<br/>
[CListView (clase)](../../mfc/reference/clistview-class.md)<br/>
[CRichEditView (clase)](../../mfc/reference/cricheditview-class.md)
