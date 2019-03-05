---
title: Clase CMFCDynamicLayout
ms.date: 11/04/2016
f1_keywords:
- CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout::AddItem
- AFXLAYOUT/CMFCDynamicLayout::Adjust
- AFXLAYOUT/CMFCDynamicLayout::Create
- AFXLAYOUT/CMFCDynamicLayout::GetHostWnd
- AFXLAYOUT/CMFCDynamicLayout::GetMinSize
- AFXLAYOUT/CMFCDynamicLayout::GetWindowRect
- AFXLAYOUT/CMFCDynamicLayout::HasItem
- AFXLAYOUT/CMFCDynamicLayout::IsEmpty
- AFXLAYOUT/CMFCDynamicLayout::LoadResource
- AFXLAYOUT/CMFCDynamicLayout::SetMinSize
ms.assetid: c2df2976-f049-47fc-9cf0-abe3e01948bc
ms.openlocfilehash: 40dedbe2737a79b7531b8acd47870ce7cb788604
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288407"
---
# <a name="cmfcdynamiclayout-class"></a>Clase CMFCDynamicLayout

Especifica cómo se mueven y cambian de tamaño los controles de una ventana cuando el usuario cambia el tamaño de la ventana.

## <a name="syntax"></a>Sintaxis

```
class CMFCDynamicLayout : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|`CMFCDynamicLayout::CMFCDynamicLayout`|Construye un objeto `CMFCDynamicLayout`.|
|`CMFCDynamicLayout::~CMFCDynamicLayout`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCDynamicLayout::AddItem](#additem)|Agrega una ventana secundaria (un control, normalmente) a la lista de ventanas controladas por el administrador de diseño dinámico.|
|[CMFCDynamicLayout::Adjust](#adjust)|Agrega una ventana secundaria (un control, normalmente) a la lista de ventanas controladas por el administrador de diseño dinámico.|
|[CMFCDynamicLayout::Create](#create)|Almacena y valida la ventana host.|
|[CMFCDynamicLayout::GetHostWnd](#gethostwnd)|Devuelve un puntero a una ventana host.|
|[CMFCDynamicLayout::GetMinSize](#getminsize)|Devuelve el tamaño de la ventana por debajo del cual no se ajusta el diseño.|
|[CMFCDynamicLayout::GetWindowRect](#getwindowrect)|Recupera el rectángulo de área de cliente actual de la ventana.|
|[CMFCDynamicLayout::HasItem](#hasitem)|Comprueba si se agregó un control secundario al diseño dinámico.|
|[CMFCDynamicLayout::IsEmpty](#isempty)|Comprueba si un diseño dinámico no tiene ventanas secundarias agregadas.|
|[CMFCDynamicLayout::LoadResource](#loadresource)|Lee el diseño dinámico del recurso AFX_DIALOG_LAYOUT y después aplica el diseño a la ventana del host.|
|estática [CMFCDynamicLayout::MoveHorizontal](#movehorizontal)|Obtiene un [MoveSettings](#movesettings_structure) valor que define cuánto un control secundario se desplaza horizontalmente cuando el usuario cambia el tamaño de su ventana de hospedaje.|
|estática [CMFCDynamicLayout::MoveHorizontalAndVertical](#movehorizontalandvertical)|Obtiene un [MoveSettings](#movesettings_structure) valor que define cuánto un control secundario se desplaza horizontalmente cuando el usuario cambia el tamaño de su ventana de hospedaje.|
|estática [CMFCDynamicLayout::MoveNone](#movenone)|Obtiene un [MoveSettings](#movesettings_structure) valor que no representa ningún movimiento, vertical u horizontal de un control secundario.|
|estática [CMFCDynamicLayout::MoveVertical](#movevertical)|Obtiene un [MoveSettings](#movesettings_structure) valor que define cuánto un control secundario se desplaza verticalmente cuando el usuario cambia el tamaño de su ventana de hospedaje.|
|[CMFCDynamicLayout::SetMinSize](#setminsize)|Establece el tamaño de la ventana por debajo del cual no se ajusta el diseño.|
|estática [CMFCDynamicLayout::SizeHorizontal](#sizehorizontal)|Obtiene un [SizeSettings](#sizesettings_structure) valor que define cuánto un control secundario se redimensiona horizontalmente cuando el usuario cambia el tamaño de su ventana de hospedaje.|
|estática [CMFCDynamicLayout::SizeHorizontalAndVertical](#sizehorizontalandvertical)|Obtiene un [SizeSettings](#sizesettings_structure) valor que define cuánto un control secundario se redimensiona horizontalmente cuando el usuario cambia el tamaño de su ventana de hospedaje.|
|estática [CMFCDynamicLayout::SizeNone](#sizenone)|Obtiene un [SizeSettings](#sizesettings_structure) valor que no representa ningún cambio de tamaño para un control secundario.|
|estática [CMFCDynamicLayout::SizeVertical](#sizevertical)|Obtiene un [SizeSettings](#sizesettings_structure) valor que define cuánto un control secundario se redimensiona verticalmente cuando el usuario cambia el tamaño de su ventana de hospedaje.|

## <a name="nested-types"></a>Tipos anidados

|nombre|Descripción|
|----------|-----------------|
|[Cmfcdynamiclayout:: estructura](#movesettings_structure)|Encapsula los datos de movimiento de los controles de un diseño dinámico.|
|[Estructura de cmfcdynamiclayout:: Sizesettings](#sizesettings_structure)|Encapsula los datos de cambio de tamaño de los controles de un diseño dinámico.|

## <a name="remarks"></a>Comentarios

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxlayout.h

##  <a name="additem"></a>  CMFCDynamicLayout::AddItem

Agrega una ventana secundaria (un control, normalmente) a la lista de ventanas controladas por el administrador de diseño dinámico.

```
BOOL AddItem(
    HWND hwnd,
    MoveSettings moveSettings SizeSettings sizeSettings);

BOOL AddItem(
    int nID,
    MoveSettings moveSettings SizeSettings sizeSettings);
```

### <a name="parameters"></a>Parámetros

*hwnd*<br/>
Controlador de la ventana que se va a agregar.

*nID*<br/>
Identificador del control secundario que se va a agregar.

*moveSettings*<br/>
Estructura que describe cómo se debe mover el control a medida que cambia el tamaño de la ventana.

*sizeSettings*<br/>
Estructura que describe cómo debe cambiar el tamaño del control a medida que cambia el tamaño de la ventana.

### <a name="return-value"></a>Valor devuelto

Es TRUE si se agregó correctamente el elemento; de lo contrario, es FALSE.

### <a name="remarks"></a>Comentarios

La posición y el tamaño de un control secundario cambian dinámicamente cuando una ventana de hospedaje cambia de tamaño.

##  <a name="adjust"></a>  Cmfcdynamiclayout:: Adjust

Agrega una ventana secundaria (un control, normalmente) a la lista de ventanas controladas por el administrador de diseño dinámico.

```
void Adjust();
```

### <a name="remarks"></a>Comentarios

La posición y el tamaño de un control secundario cambian dinámicamente cuando una ventana de hospedaje cambia de tamaño.

##  <a name="create"></a>  CMFCDynamicLayout::Create

Almacena y valida la ventana host.

```
BOOL Create(CWnd* pHostWnd);
```

### <a name="parameters"></a>Parámetros

*pHostWnd*<br/>
Un puntero a la ventana host.

### <a name="return-value"></a>Valor devuelto

Es TRUE si la creación se realizó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="gethostwnd"></a>  CMFCDynamicLayout::GetHostWnd

Devuelve un puntero a una ventana host.

```
CWnd* GetHostWnd();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la ventana host.

### <a name="remarks"></a>Comentarios

De forma predeterminada, la posición de todos los controles secundarios se recalcula con respecto a esta ventana.

##  <a name="getminsize"></a>  CMFCDynamicLayout::GetMinSize

Devuelve el tamaño de la ventana por debajo del cual no se ajusta el diseño.

```
CSize GetMinSize();
```

### <a name="return-value"></a>Valor devuelto

Tamaño de la ventana por debajo del cual no se ajusta el diseño.

### <a name="remarks"></a>Comentarios

La posición y el tamaño de un control secundario cambian dinámicamente cuando se cambia el tamaño de una ventana de hospedaje, pero hay un tamaño mínimo por debajo del cual no se ajusta el diseño. El usuario puede reducir el tamaño de la ventana, pero habrá partes de la ventana ocultas a la vista.

##  <a name="getwindowrect"></a>  CMFCDynamicLayout::GetWindowRect

Recupera el rectángulo de área de cliente actual de la ventana.

```
void GetHostWndRect(CRect& rect,);
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
Después de la devolución de la función, este parámetro contiene el rectángulo delimitador del área de presentación. Se trata de un parámetro de salida; el valor de entrada se sobrescribe.

### <a name="remarks"></a>Comentarios

##  <a name="hasitem"></a>  CMFCDynamicLayout::HasItem

Comprueba si se agregó un control secundario al diseño dinámico.

```
BOOL HasItem(HWND hwnd);
```

### <a name="parameters"></a>Parámetros

*hwnd*<br/>
El identificador de ventana para el control.

### <a name="return-value"></a>Valor devuelto

TRUE si el diseño ya tiene este elemento; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="isempty"></a>  CMFCDynamicLayout::IsEmpty

Comprueba si un diseño dinámico no tiene ventanas secundarias agregadas.

```
BOOL IsEmpty();
```

### <a name="return-value"></a>Valor devuelto

TRUE si el diseño no tiene elementos; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="loadresource"></a>  CMFCDynamicLayout::LoadResource

Lee el diseño dinámico del recurso AFX_DIALOG_LAYOUT y después aplica el diseño a la ventana del host.

```
static BOOL LoadResource(CWnd* pHostWnd,
    LPVOID lpResource,
    DWORD dwSize);
```

### <a name="parameters"></a>Parámetros

*pHostWnd*<br/>
Un puntero a la ventana host.

*lpResource*<br/>
Un puntero al búfer que contiene el recurso AFX_DIALOG_LAYOUT.

*dwSize*<br/>
El tamaño del búfer en bytes.

### <a name="return-value"></a>Valor devuelto

TRUE si el recurso se carga y se aplica a la ventana del host; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="movehorizontal"></a>  CMFCDynamicLayout::MoveHorizontal

Obtiene un [MoveSettings](#movesettings_structure) valor que define cuánto un control secundario se desplaza horizontalmente cuando el usuario cambia el tamaño de su ventana de hospedaje.

```
static MoveSettings MoveHorizontal(int nRatio);
```

### <a name="parameters"></a>Parámetros

*nRatio*<br/>
Define como un porcentaje hasta qué punto se desplaza horizontalmente un control secundario cuando el usuario cambia el tamaño de la ventana de hospedaje.

### <a name="return-value"></a>Valor devuelto

Un [MoveSettings](#movesettings_structure) relación de movimiento de valor que encapsula la información solicitada.

### <a name="remarks"></a>Comentarios

##  <a name="movehorizontalandvertical"></a>  CMFCDynamicLayout::MoveHorizontalAndVertical

Obtiene un [MoveSettings](#movesettings_structure) valor que define cuánto un control secundario se desplaza horizontalmente cuando el usuario cambia el tamaño de su ventana de hospedaje.

```
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Parámetros

*nXRatio*<br/>
Define como un porcentaje hasta qué punto se desplaza horizontalmente un control secundario cuando el usuario cambia el tamaño de la ventana de hospedaje.

*nYRatio*<br/>
Define, como un porcentaje, hasta qué punto se desplaza verticalmente un control secundario cuando el usuario cambia el tamaño de la ventana de host.

### <a name="return-value"></a>Valor devuelto

Un [MoveSettings](#movesettings_structure) relación de movimiento de valor que encapsula la información solicitada.

### <a name="remarks"></a>Comentarios

##  <a name="movenone"></a>  CMFCDynamicLayout::MoveNone

Obtiene un [MoveSettings](#movesettings_structure) valor que no representa ningún movimiento, vertical u horizontal de un control secundario.

```
static MoveSettings MoveNone();
```

### <a name="return-value"></a>Valor devuelto

Un [MoveSettings](#movesettings_structure) valor que corrige el control en su lugar, por lo que no se mueve como el usuario cambia el tamaño de la ventana host.

### <a name="remarks"></a>Comentarios

##  <a name="movesettings_structure"></a>  Cmfcdynamiclayout:: estructura

Encapsula los datos de movimiento de los controles de un diseño dinámico.

```
struct CMFCDynamicLayout::MoveSettings;
```

### <a name="remarks"></a>Comentarios

Se trata de una clase anidada dentro de `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutmovesettingsishorizontal"></a>CMFCDynamicLayout::MoveSettings::IsHorizontal

Compruebe si los datos de movimiento especifican un movimiento horizontal distinto de cero.

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>Valor devuelto

Es TRUE si el objeto `MoveSettings` especifica un movimiento de tamaño horizontal distinto de cero.

## <a name="cmfcdynamiclayoutmovesettingsisnone"></a>CMFCDynamicLayout::MoveSettings::IsNone

Comprueba si los datos de movimiento no especifican ningún movimiento.

```
BOOL IsNone() const
```

## <a name="return-value"></a>Valor devuelto

Es TRUE si el objeto `MoveSettings` no especifica ningún movimiento.

## <a name="cmfcdynamiclayoutmovesettingsisvertical"></a>CMFCDynamicLayout::MoveSettings::IsVertical

  Comprueba si los datos de movimiento especifican un movimiento vertical distinto de cero.

```
BOOL IsVertical() const
```

## <a name="return-value"></a>Valor devuelto

Es TRUE si el objeto `MoveSettings` especifica un movimiento vertical distinto de cero.

##  <a name="movevertical"></a>  CMFCDynamicLayout::MoveVertical

Obtiene un [MoveSettings](#movesettings_structure) valor que define cuánto un control secundario se desplaza verticalmente cuando el usuario cambia el tamaño de su ventana de hospedaje.

```
static MoveSettings MoveVertical(int nRatio);
```

### <a name="parameters"></a>Parámetros

*nRatio*<br/>
Define, como un porcentaje, hasta qué punto se desplaza verticalmente un control secundario cuando el usuario cambia el tamaño de la ventana de host.

### <a name="return-value"></a>Valor devuelto

Un [MoveSettings](#movesettings_structure) relación de movimiento de valor que encapsula la información solicitada.

### <a name="remarks"></a>Comentarios

##  <a name="setminsize"></a>  CMFCDynamicLayout::SetMinSize

Establece el tamaño de la ventana por debajo del cual no se ajusta el diseño.

```
void SetMinSize(const CSize& size);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
El tamaño deseado por debajo del cual no se ajusta el diseño.

### <a name="remarks"></a>Comentarios

La posición y el tamaño de un control secundario cambian dinámicamente cuando se cambia el tamaño de una ventana de hospedaje, pero hay un tamaño mínimo por debajo del cual no se ajusta el diseño. El usuario puede reducir el tamaño de la ventana, pero habrá partes de la ventana ocultas a la vista.

##  <a name="sizehorizontal"></a>  CMFCDynamicLayout::SizeHorizontal

Obtiene un [SizeSettings](#sizesettings_structure) valor que define cuánto un control secundario se redimensiona horizontalmente cuando el usuario cambia el tamaño de su ventana de hospedaje.

```
static SizeSettings SizeHorizontal(int nRatio);
```

### <a name="parameters"></a>Parámetros

*nRatio*<br/>
Define como un porcentaje hasta qué punto se cambia el tamaño horizontal de un control secundario cuando el usuario cambia el tamaño de la ventana de hospedaje.

### <a name="return-value"></a>Valor devuelto

Un [SizeSettings](#sizesettings_structure) valor que encapsula la proporción de tamaño solicitado.

### <a name="remarks"></a>Comentarios

##  <a name="sizehorizontalandvertical"></a>  CMFCDynamicLayout::SizeHorizontalAndVertical

Obtiene un [SizeSettings](#sizesettings_structure) valor que define cuánto un control secundario se redimensiona horizontalmente cuando el usuario cambia el tamaño de su ventana de hospedaje.

```
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Parámetros

*nXRatio*<br/>
Define como un porcentaje hasta qué punto se cambia el tamaño horizontal de un control secundario cuando el usuario cambia el tamaño de la ventana de hospedaje.

*nYRatio*<br/>
Define como un porcentaje hasta qué punto se cambia el tamaño vertical de un control secundario cuando el usuario cambia el tamaño de la ventana de hospedaje.

### <a name="return-value"></a>Valor devuelto

Un [SizeSettings](#sizesettings_structure) valor que encapsula la proporción de tamaño solicitado.

### <a name="remarks"></a>Comentarios

##  <a name="sizenone"></a>  CMFCDynamicLayout::SizeNone

Obtiene un [SizeSettings](#sizesettings_structure) valor que no representa ningún cambio de tamaño para un control secundario.

```
static SizeSettings SizeNone();
```

### <a name="return-value"></a>Valor devuelto

Un [SizeSettings](#sizesettings_structure) valor que corrige el control a un determinado tamaño, por lo que no cambia tamaño como el usuario cambia el tamaño de la ventana host.

### <a name="remarks"></a>Comentarios

##  <a name="sizesettings_structure"></a>  Estructura de cmfcdynamiclayout:: Sizesettings

Encapsula los datos de cambio de tamaño de los controles de un diseño dinámico.

```
struct CMFCDynamicLayout::SizeSettings;
```

### <a name="remarks"></a>Comentarios

Se trata de una clase anidada dentro de `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutsizesettingsishorizontal"></a>CMFCDynamicLayout::SizeSettings::IsHorizontal

Comprueba si los datos de cambio de tamaño especifican un cambio de tamaño horizontal distinto de cero.

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>Valor devuelto

Es TRUE si el objeto `SizeSettings` especifica un cambio de tamaño horizontal distinto de cero.

## <a name="cmfcdynamiclayoutsizesettingsisnone"></a>CMFCDynamicLayout::SizeSettings::IsNone

Comprueba si los datos de cambio de tamaño especifican que no se ha realizado ningún cambio en este sentido.

```
BOOL IsNone() const
```

## <a name="return-value"></a>Valor devuelto

Es TRUE si el objeto `SizeSettings` no especifica ningún cambio de tamaño.

## <a name="cmfcdynamiclayoutsizesettingsisvertical"></a>CMFCDynamicLayout::SizeSettings::IsVertical

Comprueba si los datos de cambio de tamaño especifican un cambio de tamaño vertical distinto de cero.

```
BOOL IsVertical() const
```

## <a name="return-value"></a>Valor devuelto

Es TRUE si el objeto `SizeSettings` especifica un cambio de tamaño vertical distinto de cero.

##  <a name="sizevertical"></a>  CMFCDynamicLayout::SizeVertical

Obtiene un [SizeSettings](#sizesettings_structure) valor que define cuánto un control secundario se redimensiona verticalmente cuando el usuario cambia el tamaño de su ventana de hospedaje.

```
static SizeSettings SizeVertical(int nRatio);
```

### <a name="parameters"></a>Parámetros

*nRatio*<br/>
Define como un porcentaje hasta qué punto se cambia el tamaño vertical de un control secundario cuando el usuario cambia el tamaño de la ventana de hospedaje.

### <a name="return-value"></a>Valor devuelto

Un [SizeSettings](#sizesettings_structure) valor que encapsula la proporción de tamaño solicitado.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
