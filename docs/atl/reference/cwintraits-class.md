---
title: CWinTraits (clase)
ms.date: 11/04/2016
f1_keywords:
- CWinTraits
- ATLWIN/ATL::CWinTraits
- ATLWIN/ATL::CWinTraits::GetWndExStyle
- ATLWIN/ATL::CWinTraits::GetWndStyle
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
ms.openlocfilehash: 840433ffb325a4f181848371306607b62373e75a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276788"
---
# <a name="cwintraits-class"></a>CWinTraits (clase)

Esta clase proporciona un método de normalización de los estilos usados al crear un objeto de ventana.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```

#### <a name="parameters"></a>Parámetros

*t_dwStyle*<br/>
Estilos de ventana estándar de forma predeterminada.

*t_dwExStyle*<br/>
De forma predeterminada, los estilos de ventana extendidos.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CWinTraits::GetWndExStyle](#getwndexstyle)|(Estático) Recupera los estilos extendidos para el `CWinTraits` objeto.|
|[CWinTraits::GetWndStyle](#getwndstyle)|(Estático) Recupera los estilos estándar para el `CWinTraits` objeto.|

## <a name="remarks"></a>Comentarios

Esto [rasgos de las ventanas](../../atl/understanding-window-traits.md) clase proporciona un método sencillo para estandarizar los estilos utilizados para la creación de un objeto de ventana ATL. Usar una especialización de esta clase como un parámetro de plantilla [CWindowImpl](../../atl/reference/cwindowimpl-class.md) u otra de las clases de ventana de ATL para especificar los estilos predeterminados estándar y extendidos usados para las instancias de esa clase de ventana.

Use esta plantilla cuando desee proporcionar predeterminado estilos de ventana que se usará sólo cuando ningún otro estilo se especifica en la llamada a [CWindowImpl:: Create](../../atl/reference/cwindowimpl-class.md#create).

ATL proporciona tres especializaciones predefinidas de esta plantilla para combinaciones frecuentes de estilos de ventana:

- `CControlWinTraits`

   Diseñado para una ventana de control estándar. Se utilizan los estilos estándar siguientes: WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN y WS_CLIPSIBLINGS. No hay ningún estilos extendidos.

- `CFrameWinTraits`

   Diseñado para una ventana de marco estándar. Los estilos estándares utilizados incluyen: WS_OVERLAPPEDWINDOW WS_CLIPCHILDREN y WS_CLIPSIBLINGS. Los estilos extendidos utilizados incluyen: WS_EX_APPWINDOW y WS_EX_WINDOWEDGE.

- `CMDIChildWinTraits`

   Diseñado para una ventana MDI secundaria estándar. Los estilos estándares utilizados incluyen: WS_OVERLAPPEDWINDOW, WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN y WS_CLIPSIBLINGS. Los estilos extendidos utilizados incluyen: WS_EX_MDICHILD.

Si desea asegurarse de que se establecen algunos estilos para todas las instancias de la clase de ventana al tiempo que permite a otros estilos debe establecerse en una base por instancia, use [CWinTraitsOR](../../atl/reference/cwintraitsor-class.md) en su lugar.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="getwndstyle"></a>  CWinTraits::GetWndStyle

Llame a esta función para recuperar los estilos estándar de la `CWinTraits` objeto.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Estilos estándar que se usa para la creación de una ventana. Si *dwStyle* es 0, los valores de estilo de plantilla (`t_dwStyle`) se devuelven. Si *dwStyle* es distinto de cero, *dwStyle* se devuelve.

### <a name="return-value"></a>Valor devuelto

Los estilos de ventana estándar del objeto.

##  <a name="getwndexstyle"></a>  CWinTraits::GetWndExStyle

Llame a esta función para recuperar los estilos extendidos de la `CWinTraits` objeto.

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>Parámetros

*dwExStyle*<br/>
Estilos extendidos que se usa para la creación de una ventana. Si *dwExStyle* es 0, los valores de estilo de plantilla (`t_dwExStyle`) se devuelven. Si *dwExStyle* es distinto de cero, *dwExStyle* se devuelve.

### <a name="return-value"></a>Valor devuelto

Los estilos de ventana extendidos del objeto.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Descripción de rasgos de las ventanas](../../atl/understanding-window-traits.md)
