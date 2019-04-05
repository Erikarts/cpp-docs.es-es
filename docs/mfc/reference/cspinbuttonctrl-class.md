---
title: CSpinButtonCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::Create
- AFXCMN/CSpinButtonCtrl::CreateEx
- AFXCMN/CSpinButtonCtrl::GetAccel
- AFXCMN/CSpinButtonCtrl::GetBase
- AFXCMN/CSpinButtonCtrl::GetBuddy
- AFXCMN/CSpinButtonCtrl::GetPos
- AFXCMN/CSpinButtonCtrl::GetRange
- AFXCMN/CSpinButtonCtrl::SetAccel
- AFXCMN/CSpinButtonCtrl::SetBase
- AFXCMN/CSpinButtonCtrl::SetBuddy
- AFXCMN/CSpinButtonCtrl::SetPos
- AFXCMN/CSpinButtonCtrl::SetRange
helpviewer_keywords:
- CSpinButtonCtrl [MFC], CSpinButtonCtrl
- CSpinButtonCtrl [MFC], Create
- CSpinButtonCtrl [MFC], CreateEx
- CSpinButtonCtrl [MFC], GetAccel
- CSpinButtonCtrl [MFC], GetBase
- CSpinButtonCtrl [MFC], GetBuddy
- CSpinButtonCtrl [MFC], GetPos
- CSpinButtonCtrl [MFC], GetRange
- CSpinButtonCtrl [MFC], SetAccel
- CSpinButtonCtrl [MFC], SetBase
- CSpinButtonCtrl [MFC], SetBuddy
- CSpinButtonCtrl [MFC], SetPos
- CSpinButtonCtrl [MFC], SetRange
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
ms.openlocfilehash: 6f864a37c46158ab98776cd96d9f50d7cfaeb13d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776354"
---
# <a name="cspinbuttonctrl-class"></a>CSpinButtonCtrl (clase)

Proporciona la funcionalidad del control de botón de número común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CSpinButtonCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|Construye un objeto `CSpinButtonCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSpinButtonCtrl::Create](#create)|Crea un control de botón de número y lo adjunta a un `CSpinButtonCtrl` objeto.|
|[CSpinButtonCtrl::CreateEx](#createex)|Crea un control de botón de número con los estilos extendidos de Windows especificados y lo asocia a un `CSpinButtonCtrl` objeto.|
|[CSpinButtonCtrl::GetAccel](#getaccel)|Recupera información de aceleración para un control de botón de número.|
|[CSpinButtonCtrl::GetBase](#getbase)|Recupera la base actual de un control de botón de número.|
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|Recupera un puntero a la actual ventana relacionada.|
|[CSpinButtonCtrl::GetPos](#getpos)|Recupera la posición actual de un control de botón de número.|
|[CSpinButtonCtrl::GetRange](#getrange)|Recupera los límites superiores e inferiores (intervalo) de un control de botón de número.|
|[CSpinButtonCtrl::SetAccel](#setaccel)|Establece la aceleración de un control de botón de número.|
|[CSpinButtonCtrl::SetBase](#setbase)|Establece la base de un control de botón de número.|
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|Establece la ventana relacionada para un control de botón de número.|
|[CSpinButtonCtrl::SetPos](#setpos)|Establece la posición actual del control.|
|[CSpinButtonCtrl::SetRange](#setrange)|Establece los límites superiores e inferiores (intervalo) de un control de botón de número.|

## <a name="remarks"></a>Comentarios

Un "spin control button" (también conocido como control de flechas) es un par de botones de flecha que el usuario puede hacer clic para incrementar o disminuir un valor, como una posición de desplazamiento o un número que aparece en un control complementario. El valor asociado a un control de botón de número se llama a su posición actual. Un control de botón de número se suele utilizar con un control complementario, denominado "ventana relacionada".

Este control (y, por tanto, la `CSpinButtonCtrl` clase) está disponible solo para programas que se ejecutan en Windows 95/98 y Windows NT versión 3.51 y versiones posteriores.

Para el usuario, un control de botón de número y su ventana relacionada a menudo se ven como un único control. Puede especificar que un control de botón de número automáticamente colocarse junto a su ventana relacionada, y que establece automáticamente el título de la ventana relacionada a su posición actual. Puede usar un control de botón de número con un control de edición para preguntar al usuario para entrada numérica.

Al hacer clic en la flecha hacia arriba mueve la posición actual en el valor máximo y haga clic en la flecha hacia abajo mueve la posición actual hacia el mínimo. De forma predeterminada, el valor mínimo es 100 y el máximo es 0. Cada vez que el valor mínimo es mayor que el máximo configurado (por ejemplo, cuando se usa la configuración predeterminada), al hacer clic en las salidas de la flecha hacia arriba el valor de posición y haga clic en la flecha hacia abajo aumenta.

Un control de botón de número sin ventana relacionada funciona como una especie de barra de desplazamiento simplificado. Por ejemplo, un control de ficha a veces muestra un control de botón de número para permitir al usuario Desplazar fichas adicionales en la vista.

Para obtener más información sobre el uso de `CSpinButtonCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [usar CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="create"></a>  CSpinButtonCtrl::Create

Crea un control de botón de número y lo adjunta a un `CSpinButtonCtrl` objeto...

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de botón de número. Se aplican a cualquier combinación de los estilos de control de botón de número para el control. Estos estilos se describen en [estilos de Control de flechas](/windows/desktop/Controls/up-down-control-styles) en el SDK de Windows.

*rect*<br/>
Especifica el tamaño y la posición del control de botón de número. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura

*pParentWnd*<br/>
Un puntero a la ventana del elemento primario del control de botón de número, normalmente un `CDialog`. No debe ser NULL.

*nID*<br/>
Especifica el identificador. del control de botón de número

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Construir un `CSpinButtonCtrl` objeto en dos pasos en primer lugar, llame al constructor y, a continuación, llame a `Create`, que crea el control de botón de número y lo adjunta a la `CSpinButtonCtrl` objeto.

Para crear un control de botón de número con estilos de ventana extendidos, llame a [CSpinButtonCtrl::CreateEx](#createex) en lugar de `Create`.

##  <a name="createex"></a>  CSpinButtonCtrl::CreateEx

Crea un control (una ventana secundaria) y lo asocia a la `CSpinButtonCtrl` objeto.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwExStyle*<br/>
Especifica el estilo extendido del control que se está creando. Para obtener una lista de los estilos extendidos de windows, consulte el *dwExStyle* parámetro [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) en el SDK de Windows.

*dwStyle*<br/>
Especifica el estilo del control de botón de número. Se aplican a cualquier combinación de los estilos de control de botón de número para el control. Estos estilos se describen en [estilos de Control de flechas](/windows/desktop/Controls/up-down-control-styles) en el SDK de Windows.

*rect*<br/>
Una referencia a un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura que describe el tamaño y posición de la ventana que se creará, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Un puntero a la ventana que es primario del control.

*nID*<br/>
Identificador de ventana secundaria. del control

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Use `CreateEx` en lugar de [crear](#create) para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows WS_EX_.

##  <a name="cspinbuttonctrl"></a>  CSpinButtonCtrl::CSpinButtonCtrl

Construye un objeto `CSpinButtonCtrl`.

```
CSpinButtonCtrl();
```

##  <a name="getaccel"></a>  CSpinButtonCtrl::GetAccel

Recupera información de aceleración para un control de botón de número.

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>Parámetros

*nAccel*<br/>
Número de elementos de la matriz especificada por *pAccel*.

*pAccel*<br/>
Puntero a una matriz de [UDACCEL](/windows/desktop/api/commctrl/ns-commctrl-_udaccel) estructuras que recibe información de aceleración.

### <a name="return-value"></a>Valor devuelto

Recupera el número de estructuras del acelerador.

##  <a name="getbase"></a>  CSpinButtonCtrl::GetBase

Recupera la base actual de un control de botón de número.

```
UINT GetBase() const;
```

### <a name="return-value"></a>Valor devuelto

El valor base actual.

##  <a name="getbuddy"></a>  CSpinButtonCtrl::GetBuddy

Recupera un puntero a la actual ventana relacionada.

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la actual ventana relacionada.

##  <a name="getpos"></a>  CSpinButtonCtrl::GetPos

Recupera la posición actual de un control de botón de número.

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>Parámetros

*lpbError*<br/>
Un puntero a un valor booleano que se establece en cero si el valor se recuperó correctamente o que se distinto de cero si se produce un error. Si este parámetro se establece en NULL, no se notifican errores.

### <a name="return-value"></a>Valor devuelto

La primera versión, devuelve la posición actual de 16 bits en la palabra de orden inferior. La palabra de orden superior es distinto de cero si se produjo un error.

La segunda versión, devuelve la posición de 32 bits.

### <a name="remarks"></a>Comentarios

Cuando procesa el valor devuelto, el control actualice su posición actual en función de la leyenda de la ventana relacionada. El control devuelve un error si no hay ninguna ventana relacionada o si el título especifica un valor no válido o fuera de intervalo.

##  <a name="getrange"></a>  CSpinButtonCtrl::GetRange

Recupera los límites superiores e inferiores (intervalo) de un control de botón de número.

```
DWORD GetRange() const;

void GetRange(
    int& lower,
    int& upper) const;

void GetRange32(
    int& lower,
    int &upper) const;
```

### <a name="parameters"></a>Parámetros

*inferior*<br/>
Referencia a un entero que recibe el límite inferior para el control.

*superior*<br/>
Referencia a un entero que recibe el límite superior para el control.

### <a name="return-value"></a>Valor devuelto

La primera versión, devuelve un valor de 32 bits que contiene los límites superiores e inferiores. La palabra de orden inferior es el límite superior para el control y la palabra de orden superior es el límite inferior.

### <a name="remarks"></a>Comentarios

La función miembro `GetRange32` recupera el intervalo del control de botón de número como un entero de 32 bits.

##  <a name="setaccel"></a>  CSpinButtonCtrl::SetAccel

Establece la aceleración de un control de botón de número.

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>Parámetros

*nAccel*<br/>
Número de [UDACCEL](/windows/desktop/api/commctrl/ns-commctrl-_udaccel) estructuras especificado por *pAccel*.

*pAccel*<br/>
Puntero a una matriz de estructuras UDACCEL, que contienen información de aceleración. Los elementos se deben ordenar en orden ascendente según la `nSec` miembro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="setbase"></a>  CSpinButtonCtrl::SetBase

Establece la base de un control de botón de número.

```
int SetBase(int nBase);
```

### <a name="parameters"></a>Parámetros

*nBase*<br/>
Nuevo valor de base para el control. Puede ser 10 para separar los decimales o 16 en formato hexadecimal.

### <a name="return-value"></a>Valor devuelto

El valor base anterior si se realiza correctamente, o cero si no se especifica una base no válida.

### <a name="remarks"></a>Comentarios

El valor base determina si la ventana relacionada muestra los números de dígitos decimales o hexadecimales. Los números hexadecimales son siempre sin signo; se firman los números decimales.

##  <a name="setbuddy"></a>  CSpinButtonCtrl::SetBuddy

Establece la ventana relacionada para un control de botón de número.

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>Parámetros

*pWndBuddy*<br/>
Puntero a la nueva ventana relacionada.

### <a name="return-value"></a>Valor devuelto

Un puntero a la ventana relacionada anterior.

### <a name="remarks"></a>Comentarios

Casi siempre está asociado con otra ventana, como un control de edición, que muestra algún contenido de un control de número. Esta ventana de otra se denomina a "buddy" del control de flechas.

##  <a name="setpos"></a>  CSpinButtonCtrl::SetPos

Establece la posición actual de un control de botón de número.

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Nueva posición del control. Este valor debe ser en el intervalo especificado por los límites superiores e inferiores del control.

### <a name="return-value"></a>Valor devuelto

La posición anterior (16 bits de precisión para `SetPos`, 32 bits precisión para `SetPos32`).

### <a name="remarks"></a>Comentarios

`SetPos32` establece la posición de 32 bits.

##  <a name="setrange"></a>  CSpinButtonCtrl::SetRange

Establece los límites superiores e inferiores (intervalo) de un control de botón de número.

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>Parámetros

*nLower* y *nUpper*<br/>
Límites superior e inferior del control. Para `SetRange`, ni límite puede ser mayor que UD_MAXVAL o menor que UD_MINVAL; Además, la diferencia entre los dos límites no puede superar los UD_MAXVAL. `SetRange32` impone ninguna restricción sobre los límites; Utilice los enteros.

### <a name="remarks"></a>Comentarios

La función miembro `SetRange32` establece el rango de 32 bits para el control de botón de número.

> [!NOTE]
>  El intervalo predeterminado para el botón de número tiene el máximo establecido en cero (0) y el mínimo establecido en 100. Dado que el valor máximo es menor que el valor mínimo, al hacer clic en la flecha arriba se reducirá la posición y al hacer clic en la flecha hacia abajo, aumentará. Use `CSpinButtonCtrl::SetRange` para ajustar estos valores.

## <a name="see-also"></a>Vea también

[MFC Sample CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CSliderCtrl (clase)](../../mfc/reference/csliderctrl-class.md)
