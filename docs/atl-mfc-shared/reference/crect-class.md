---
title: CRect (clase)
ms.date: 11/06/2018
f1_keywords:
- CRect
- ATLTYPES/ATL::CRect
- ATLTYPES/ATL::CRect::CRect
- ATLTYPES/ATL::CRect::BottomRight
- ATLTYPES/ATL::CRect::CenterPoint
- ATLTYPES/ATL::CRect::CopyRect
- ATLTYPES/ATL::CRect::DeflateRect
- ATLTYPES/ATL::CRect::EqualRect
- ATLTYPES/ATL::CRect::Height
- ATLTYPES/ATL::CRect::InflateRect
- ATLTYPES/ATL::CRect::IntersectRect
- ATLTYPES/ATL::CRect::IsRectEmpty
- ATLTYPES/ATL::CRect::IsRectNull
- ATLTYPES/ATL::CRect::MoveToX
- ATLTYPES/ATL::CRect::MoveToXY
- ATLTYPES/ATL::CRect::MoveToY
- ATLTYPES/ATL::CRect::NormalizeRect
- ATLTYPES/ATL::CRect::OffsetRect
- ATLTYPES/ATL::CRect::PtInRect
- ATLTYPES/ATL::CRect::SetRect
- ATLTYPES/ATL::CRect::SetRectEmpty
- ATLTYPES/ATL::CRect::Size
- ATLTYPES/ATL::CRect::SubtractRect
- ATLTYPES/ATL::CRect::TopLeft
- ATLTYPES/ATL::CRect::UnionRect
- ATLTYPES/ATL::CRect::Width
helpviewer_keywords:
- LPCRECT data type
- CRect class
- LPRECT operator
- RECT structure
ms.assetid: dee4e752-15d6-4db4-b68f-1ad65b2ed6ca
ms.openlocfilehash: 6e87d77eec526cbfcfe5c1e6e78b0287226f0613
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223485"
---
# <a name="crect-class"></a>CRect (clase)

Similar a un Windows [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura.

## <a name="syntax"></a>Sintaxis

```
class CRect : public tagRECT
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CRect::CRect](#crect)|Construye un objeto `CRect`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CRect::BottomRight](#bottomright)|Devuelve el punto de la esquina inferior derecha del `CRect`.|
|[CRect::CenterPoint](#centerpoint)|Devuelve el punto central de `CRect`.|
|[CRect::CopyRect](#copyrect)|Copia las dimensiones de un rectángulo de origen a `CRect`.|
|[CRect::DeflateRect](#deflaterect)|Reduce el ancho y alto de `CRect`.|
|[CRect::EqualRect](#equalrect)|Determina si `CRect` es igual que el rectángulo especificado.|
|[CRect::Height](#height)|Calcula el alto de `CRect`.|
|[CRect::InflateRect](#inflaterect)|Aumenta el ancho y alto de `CRect`.|
|[CRect::IntersectRect](#intersectrect)|Conjuntos de `CRect` igual que la intersección de dos rectángulos.|
|[CRect::IsRectEmpty](#isrectempty)|Determina si `CRect` está vacío. `CRect` está vacío si el ancho o alto es 0.|
|[CRect::IsRectNull](#isrectnull)|Determina si el `top`, `bottom`, `left`, y `right` las variables de miembro son iguales a 0.|
|[CRect::MoveToX](#movetox)|Mueve `CRect` para la coordenada x especificada.|
|[CRect::MoveToXY](#movetoxy)|Mueve `CRect` a las coordenadas x e y especificadas.|
|[CRect::MoveToY](#movetoy)|Mueve `CRect` para la coordenada y especificada.|
|[CRect::NormalizeRect](#normalizerect)|Normaliza el alto y ancho de `CRect`.|
|[CRect::OffsetRect](#offsetrect)|Mueve `CRect` por los desplazamientos especificados.|
|[CRect::PtInRect](#ptinrect)|Determina si el punto especificado está dentro de `CRect`.|
|[CRect::SetRect](#setrect)|Establece las dimensiones de `CRect`.|
|[CRect::SetRectEmpty](#setrectempty)|Conjuntos de `CRect` a un rectángulo vacío (todas las coordenadas igual a 0).|
|[CRect::Size](#size)|Calcula el tamaño de `CRect`.|
|[CRect::SubtractRect](#subtractrect)|Resta un rectángulo de otro.|
|[CRect::TopLeft](#topleft)|Devuelve el punto superior izquierdo del `CRect`.|
|[CRect::UnionRect](#unionrect)|Conjuntos de `CRect` igual que la unión de dos rectángulos.|
|[CRect::Width](#width)|Calcula el ancho de `CRect`.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CRect::operator-](#operator_-)|Resta los desplazamientos especificados desde `CRect` o desinfla `CRect` y devuelve el resultado `CRect`.|
|[CRect::operator LPCRECT](#operator_lpcrect)|Convierte `CRect` en `LPCRECT`.|
|[CRect::operator LPRECT](#operator_lprect)|Convierte `CRect` en `LPRECT`.|
|[CRect::operator !=](#operator_neq)|Determina si `CRect` no es igual a un rectángulo.|
|[CRect::operator &amp;](#operator_amp)|Crea la intersección de `CRect` y un rectángulo y devuelve el resultado `CRect`.|
|[CRect::operator &amp;=](#operator_amp_eq)|Conjuntos de `CRect` igual a la intersección de `CRect` y un rectángulo.|
|[CRect::operator &#124;](#operator_or)|Crea la unión de `CRect` y un rectángulo y devuelve el resultado `CRect`.|
|[CRect::operator &#124;=](#operator_or_eq)|Conjuntos de `CRect` igual que la unión de `CRect` y un rectángulo.|
|[CRect::operator +](#operator_add)|Agrega los desplazamientos especificados a `CRect` o infla `CRect` y devuelve el resultado `CRect`.|
|[CRect::operator +=](#operator_add_eq)|Agrega los desplazamientos especificados a `CRect` o infla `CRect`.|
|[CRect::operator =](#operator_eq)|Copia las dimensiones de un rectángulo a `CRect`.|
|[CRect::operator -=](#operator_-_eq)|Resta los desplazamientos especificados desde `CRect` o desinfla `CRect`.|
|[CRect::operator ==](#operator_eq_eq)|Determina si `CRect` es igual a un rectángulo.|

## <a name="remarks"></a>Comentarios

`CRect` También incluye funciones de miembro para manipular `CRect` objetos y Windows `RECT` estructuras.

Un `CRect` objeto se puede pasar como un parámetro de función siempre que sea un `RECT` estructura, `LPCRECT`, o `LPRECT` se pueden pasar.

> [!NOTE]
> Esta clase se deriva el `tagRECT` estructura. (El nombre `tagRECT` es un nombre menos usados para la `RECT` estructura.) Esto significa que los miembros de datos (`left`, `top`, `right`, y `bottom`) de la `RECT` estructura son miembros de datos accesibles de `CRect`.

Un `CRect` contiene variables de miembro que definen los puntos de la parte superior izquierda e inferior derecha de un rectángulo.

Al especificar un `CRect`, debe tener cuidado para crearlo para que lo se normaliza; en otras palabras, tal que el valor de la coordenada izquierda es inferior a la derecha y la parte superior es menor que la parte inferior. Por ejemplo, una parte superior izquierda de (10,10) y parte inferior derecha (20,20) define un rectángulo normalizado pero una parte superior izquierda de (20,20) y la parte inferior derecha de (10,10) define un rectángulo sin normalizar. Si el rectángulo no está normalizado, muchas `CRect` funciones miembro pueden devolver resultados incorrectos. (Consulte [CRect:: NormalizeRect](#normalizerect) para obtener una lista de estas funciones.) Antes de llamar a una función que requiere rectángulos normalizados, puede normalizar rectángulos no normalizado mediante una llamada a la `NormalizeRect` función.

Tenga cuidado al manipular un `CRect` con el [CDC::DPtoLP](../../mfc/reference/cdc-class.md#dptolp) y [CDC::LPtoDP](../../mfc/reference/cdc-class.md#lptodp) funciones miembro. Si el modo de asignación de un contexto de presentación es tal que la extensión y es negativa, como en `MM_LOENGLISH`, a continuación, `CDC::DPtoLP` transformará el `CRect` para que su superior es mayor que la parte inferior. Las funciones como `Height` y `Size` , a continuación, devolverá los valores negativos para el alto de transformado `CRect`, y el rectángulo será no normalizado.

Cuando uso sobrecargado `CRect` operadores, el primer operando debe ser un `CRect`; el segundo puede ser un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura o un `CRect` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tagRECT`

`CRect`

## <a name="requirements"></a>Requisitos

**Encabezado:** atltypes.h

##  <a name="bottomright"></a>  CRect::BottomRight

Las coordenadas se devuelven como una referencia a un [CPoint](cpoint-class.md) objeto que se encuentra en `CRect`.

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>Valor devuelto

Las coordenadas de la esquina inferior derecha del rectángulo.

### <a name="remarks"></a>Comentarios

Puede usar esta función para obtener o establecer la esquina inferior derecha del rectángulo. Establece la esquina mediante el uso de esta función en el lado izquierdo del operador de asignación.

### <a name="example"></a>Ejemplo

```cpp
// use BottomRight() to retrieve the bottom
// right POINT
CRect rect(210, 150, 350, 900);
CPoint ptDown;

ptDown = rect.BottomRight();

// ptDown is now set to (350, 900)
ASSERT(ptDown == CPoint(350, 900));

// or, use BottomRight() to set the bottom
// right POINT
CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);

CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);
rect2.BottomRight() = ptLow;

// rect2 is now (10, 10, 180, 180)
ASSERT(rect2 == CRect(10, 10, 180, 180));
```

##  <a name="centerpoint"></a>  CRect::CenterPoint

Calcula el punto central de `CRect` agregando los valores izquierdos y derecho y dividiendo por dos y agregar los valores superior e inferior y dividir por dos.

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>Valor devuelto

Un `CPoint` objeto que es el punto central de `CRect`.

### <a name="example"></a>Ejemplo

```cpp
// Code from this OnPaint() implementation can be pasted into your own application
// to draw lines that would look like a letter "Y" within your dialog.
void CMyDlg::OnPaint()
{
    CPaintDC dc(this);

    // device context for painting

    // get the size and position of the client area of
    // your window

    CRect rect;
    GetClientRect(&rect);

    // Move the current pen to the top left of the window. We call the
    // TopLeft() member of CRect here and it returns a CPoint object we
    // pass to the override of CDC::MoveTo() that accepts a CPoint.

    dc.MoveTo(rect.TopLeft());

    // Draw a line from the top left to the center of the window.
    // CenterPoint() gives us the middle point of the window as a
    // CPoint, and since CDC::LineTo() has an override that accepts a
    // CPoint, we can just pass it along.

    dc.LineTo(rect.CenterPoint());

    // Now, draw a line to the top right of the window. There's no
    // CRect member which returns a CPoint for the top right of the
    // window, so we'll reference the CPoint members directly and call
    // the CDC::LineTo() override which takes two integers.

    dc.LineTo(rect.right, rect.top);

    // The top part of the "Y" is drawn. Now, we'll draw the stem. We
    // start from the center point.

    dc.MoveTo(rect.CenterPoint());

    // and then draw to the middle of the bottom edge of the window.
    // We'll get the x-coordinate from the x member of the CPOINT
    // returned by CenterPoint(), and the y value comes directly from
    // the rect.

    dc.LineTo(rect.CenterPoint().x, rect.bottom);
}
```

##  <a name="copyrect"></a>  CRect::CopyRect

Copia el `lpSrcRect` rectángulo en `CRect`.

```
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>Parámetros

*lpSrcRect*<br/>
Apunta a la [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura o `CRect` objeto que se va a copiar.

### <a name="example"></a>Ejemplo

```cpp
CRect rectSource(35, 10, 125, 10);
CRect rectDest;

rectDest.CopyRect(&rectSource);

// rectDest is now set to (35, 10, 125, 10)

RECT rectSource2;
rectSource2.left = 0;
rectSource2.top = 0;
rectSource2.bottom = 480;
rectSource2.right = 640;

rectDest.CopyRect(&rectSource2);

// works against RECT structures, too!
// rectDest is now set to (0, 0, 640, 480)
```

##  <a name="crect"></a>  CRect::CRect

Construye un objeto `CRect`.

```
CRect() throw();
CRect(int l, int t, int r, int b) throw();
CRect(const RECT& srcRect) throw();
CRect(LPCRECT lpSrcRect) throw();
CRect(POINT point, SIZE size) throw();
CRect(POINT topLeft, POINT bottomRight) throw();
```

### <a name="parameters"></a>Parámetros

*l*<br/>
Especifica la posición izquierda de `CRect`.

*t*<br/>
Especifica la parte superior de `CRect`.

*r*<br/>
Especifica la posición del derecha `CRect`.

*b*<br/>
Especifica la parte inferior de `CRect`.

*srcRect*<br/>
Hace referencia a la [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura con las coordenadas para `CRect`.

*lpSrcRect*<br/>
Apunta a la `RECT` estructura con las coordenadas para `CRect`.

*point*<br/>
Especifica el punto de origen para el rectángulo que se va a construir. Corresponde a la esquina superior izquierda.

*size*<br/>
Especifica el desplazamiento desde la esquina superior izquierda a la esquina inferior derecha del rectángulo que se construirá.

*topLeft*<br/>
Especifica la posición superior izquierda de `CRect`.

*bottomRight*<br/>
Especifica la posición de la esquina inferior derecha de `CRect`.

### <a name="remarks"></a>Comentarios

Si no se proporcionan argumentos, `left`, `top`, `right`, y `bottom` no se inicializan los miembros.

El `CRect`(`const RECT&`) y `CRect`(`LPCRECT`) constructores realizan un [CopyRect](#copyrect). Los otros constructores inicializan las variables miembro del objeto directamente.

### <a name="example"></a>Ejemplo

```cpp
// default constructor doesn't initialize!
CRect rectUnknown;

// four-integers are left, top, right, and bottom
CRect rect(0, 0, 100, 50);
ASSERT(rect.Width() == 100);
ASSERT(rect.Height() == 50);

// Initialize from RECT stucture
RECT sdkRect;
sdkRect.left = 0;
sdkRect.top = 0;
sdkRect.right = 100;
sdkRect.bottom = 50;

CRect rect2(sdkRect);
// by reference
CRect rect3(&sdkRect);

// by address
ASSERT(rect2 == rect);
ASSERT(rect3 == rect);

// from a point and a size
CPoint pt(0, 0);
CSize sz(100, 50);
CRect rect4(pt, sz);
ASSERT(rect4 == rect2);

// from two points
CPoint ptBottomRight(100, 50);
CRect rect5(pt, ptBottomRight);
ASSERT(rect5 == rect4);
```

##  <a name="deflaterect"></a>  CRect::DeflateRect

`DeflateRect` desinfla `CRect` moviendo sus lados hacia su centro.

```
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Especifica el número de unidades a deflate a la izquierda y derecha del `CRect`.

*y*<br/>
Especifica el número de unidades a deflate la parte superior e inferior del `CRect`.

*size*<br/>
Un [tamaño](/windows/desktop/api/windef/ns-windef-tagsize) o [CSize](csize-class.md) que especifica el número de unidades a deflate `CRect`. El `cx` valor especifica el número de unidades a deflate los lados izquierdo y derecho y el `cy` valor especifica el número de unidades a deflate la parte superior e inferior.

*lpRect*<br/>
Apunta a un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura o `CRect` que especifica el número de unidades a deflate cada lado.

*l*<br/>
Especifica el número de unidades a deflate del lado izquierdo del `CRect`.

*t*<br/>
Especifica el número de unidades a deflate la parte superior de `CRect`.

*r*<br/>
Especifica el número de unidades a deflate el lado derecho de `CRect`.

*b*<br/>
Especifica el número de unidades a deflate la parte inferior de `CRect`.

### <a name="remarks"></a>Comentarios

Para ello, `DeflateRect` agrega unidades a la izquierda y la parte superior y la resta de unidades de la derecha e inferior. Los parámetros de `DeflateRect` se firman los valores; los valores positivos deflate `CRect` y los valores negativos infla.

Las dos primeras sobrecargas deflate ambos pares de lados opuestos `CRect` para que su ancho total se reduce en dos veces *x* (o `cx`) y su altura total se reduce en dos veces *y* () o `cy`). Las dos sobrecargas deflate cada lado de `CRect` independientemente de los demás.

### <a name="example"></a>Ejemplo

```cpp
   CRect rect(10, 10, 50, 50);
   rect.DeflateRect(1, 2);
   ASSERT(rect.left == 11 && rect.right == 49);
   ASSERT(rect.top == 12 && rect.bottom == 48);

   CRect rect2(10, 10, 50, 50);
   CRect rectDeflate(1, 2, 3, 4);
   rect2.DeflateRect(&rectDeflate);
   ASSERT(rect2.left == 11 && rect2.right == 47);
   ASSERT(rect2.top == 12 && rect2.bottom == 46);
```

##  <a name="equalrect"></a>  CRect::EqualRect

Determina si `CRect` es igual que el rectángulo especificado.

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura o `CRect` objeto que contiene las coordenadas de la esquina superior izquierda e inferior derecha de un rectángulo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los dos rectángulos tienen el mismo superior, izquierdo, inferior y los valores correctos; en caso contrario, es 0.

> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1.EqualRect(rect2));
ASSERT(!rect1.EqualRect(rect3));
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1.EqualRect(&test));
```

##  <a name="height"></a>  CRect::Height

Calcula el alto de `CRect` restando el valor superior del valor de la parte inferior.

```
int Height() const throw();
```

### <a name="return-value"></a>Valor devuelto

El alto de `CRect`.

### <a name="remarks"></a>Comentarios

El valor resultante puede ser negativo.

> [!NOTE]
>  Se debe normalizar el rectángulo o esta función puede producir un error. Puede llamar a [NormalizeRect](#normalizerect) normalizar rectángulo antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

##  <a name="inflaterect"></a>  CRect::InflateRect

`InflateRect` infla `CRect` moviendo sus lados fuera de su centro.

```
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Especifica el número de unidades para aumentar la izquierda y derecha del `CRect`.

*y*<br/>
Especifica el número de unidades para aumentar la parte superior e inferior del `CRect`.

*size*<br/>
Un [tamaño](/windows/desktop/api/windef/ns-windef-tagsize) o [CSize](csize-class.md) que especifica el número de unidades se infle `CRect`. El `cx` valor especifica el número de unidades para aumentar los lados izquierdo y derecho y el `cy` valor especifica el número de unidades para aumentar la parte superior e inferior.

*lpRect*<br/>
Apunta a un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura o `CRect` que especifica el número de unidades se infle cada lado.

*l*<br/>
Especifica el número de unidades se infle el lado izquierdo de `CRect`.

*t*<br/>
Especifica el número de unidades para aumentar la parte superior de `CRect`.

*r*<br/>
Especifica el número de unidades se infle el lado derecho de `CRect`.

*b*<br/>
Especifica el número de unidades para aumentar la parte inferior de `CRect`.

### <a name="remarks"></a>Comentarios

Para ello, `InflateRect` resta unidades de la izquierda y la parte superior y las unidades se agrega a la derecha e inferior. Los parámetros de `InflateRect` están firmados valores positivos inflado valores `CRect` y los valores negativos deflate.

Las dos primeras sobrecargas inflado ambos pares de lados opuestos `CRect` para que su ancho total aumenta por dos veces *x* (o `cx`) y su altura total se incrementa en dos veces *y* () o `cy`). Las dos sobrecargas inflado cada lado de `CRect` independientemente de los demás.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

##  <a name="intersectrect"></a>  CRect::IntersectRect

Realiza una `CRect` igual a la intersección de dos rectángulos existentes.

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parámetros

*lpRect1*<br/>
Apunta a un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura o `CRect` objeto que contiene un rectángulo de origen.

*lpRect2*<br/>
Apunta a un `RECT` estructura o `CRect` objeto que contiene un rectángulo de origen.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la intersección no está vacía; 0 si la intersección está vacía.

### <a name="remarks"></a>Comentarios

La intersección es el rectángulo más grande contenido en ambos rectángulos existentes.

> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rectOne(125, 0, 150, 200);
CRect rectTwo(0, 75, 350,  95);
CRect rectInter;
```cpp
   CRect rectOne(125,  0, 150, 200);
   CRect rectTwo(0, 75, 350, 95);
   CRect rectInter;

   rectInter.IntersectRect(rectOne, rectTwo);
ASSERT(rectInter == CRect(125, 75, 150, 95));
// operator &= can do the same task:

CRect rectInter2 = rectOne;
rectInter2 &= rectTwo;
ASSERT(rectInter2 == CRect(125, 75, 150, 95));
```

##  <a name="isrectempty"></a>  CRect::IsRectEmpty

Determina si `CRect` está vacío.

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si `CRect` está vacío; 0 si `CRect` no está vacío.

### <a name="remarks"></a>Comentarios

Un rectángulo está vacío si el ancho o alto es 0 o negativo. Difiere de `IsRectNull`, que determina si todas las coordenadas del rectángulo son cero.

> [!NOTE]
>  Se debe normalizar el rectángulo o esta función puede producir un error. Puede llamar a [NormalizeRect](#normalizerect) normalizar rectángulo antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
```cpp
   CRect rectNone(0, 0, 0, 0);
   CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
   ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
   ASSERT(rectEmpty.IsRectEmpty());
```

##  <a name="isrectnull"></a>  CRect::IsRectNull

Determina si la parte superior, izquierda, abajo y los valores de la derecha `CRect` son iguales a 0.

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si `CRect`de la parte superior, izquierda, abajo, y valores correctos son todo igual a 0; en caso contrario, 0.

### <a name="remarks"></a>Comentarios

Difiere de `IsRectEmpty`, que determina si el rectángulo está vacío.

### <a name="example"></a>Ejemplo

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
```cpp
   CRect rectNone(0, 0, 0, 0);
   CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectNull());
   ASSERT(!rectSome.IsRectNull());
// note that null means _all_ zeros

CRect rectNotNull(0, 0, 35, 50);
ASSERT(!rectNotNull.IsRectNull());
```

##  <a name="movetox"></a>  CRect::MoveToX

Llame a esta función para mover el rectángulo a la especificada por la coordenada x absoluta *x*.

```
void MoveToX(int x) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Coordenada x absoluta de la esquina superior izquierda del rectángulo.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);
```cpp
   CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

   // rect is now (10, 0, 110, 100);
   ASSERT(rect == CRect(10, 0, 110, 100));
```

##  <a name="movetoxy"></a>  CRect::MoveToXY

Llame a esta función para mover el rectángulo a la absoluta: coordenadas x e y-especificada.

```
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Coordenada x absoluta de la esquina superior izquierda del rectángulo.

*y*<br/>
Coordenada y absoluta de la esquina superior izquierda del rectángulo.

*point*<br/>
Un `POINT` estructura que especifica la esquina superior izquierda absoluta del rectángulo.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
```cpp
   CRect rect(0, 0, 100, 100);
   rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
   ASSERT(rect == CRect(10, 10, 110, 110));
```

##  <a name="movetoy"></a>  CRect::MoveToY

Llame a esta función para mover el rectángulo a la especificada por la coordenada y absoluta *y*.

```
void MoveToY(int y) throw();
```

### <a name="parameters"></a>Parámetros

*y*<br/>
Coordenada y absoluta de la esquina superior izquierda del rectángulo.

### <a name="example"></a>Ejemplo

```cpp
   CRect rect(0, 0, 100, 100);
   rect.MoveToY(10);
   // rect is now (0, 10, 100, 110);
   ASSERT(rect == CRect(0, 10, 100, 110));
```

##  <a name="normalizerect"></a>  CRect::NormalizeRect

Normaliza `CRect` para que el alto y ancho son positivos.

```
void NormalizeRect() throw();
```

### <a name="remarks"></a>Comentarios

El rectángulo se normaliza para cuadrante de la cuarta posición, que normalmente utiliza Windows de las coordenadas. `NormalizeRect` Compara los valores superior e inferior y puede intercambiarlos si la parte superior es mayor que la parte inferior. De forma similar, intercambia los valores izquierdos y derecho si es mayor que el derecho de la izquierda. Esta función es útil cuando se trabaja con los modos de asignación diferente e invierte rectángulos.

> [!NOTE]
> La siguiente `CRect` funciones de miembro requieren rectángulos normalizados para que funcione correctamente: [Alto](#height), [ancho](#width), [tamaño](#size), [IsRectEmpty](#isrectempty), [PtInRect](#ptinrect), [EqualRect](#equalrect), [UnionRect](#unionrect), [IntersectRect](#intersectrect), [SubtractRect](#subtractrect), [operador ==](#operator_eq_eq), [operador! =](#operator_neq), [operador &#124; ](#operator_or), [operador &#124;=](#operator_or_eq), [operador &](#operator_amp), y [operador & =](#operator_amp_eq).

### <a name="example"></a>Ejemplo

```cpp
   CRect rect1(110, 100, 250, 310);
   CRect rect2(250, 310, 110, 100);
   rect1.NormalizeRect();
   rect2.NormalizeRect();
   ASSERT(rect1 == rect2);
```

##  <a name="offsetrect"></a>  CRect::OffsetRect

Mueve `CRect` por los desplazamientos especificados.

```
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Especifica la cantidad para desplazar a la izquierda o derecha. Debe ser negativo para mover a la izquierda.

*y*<br/>
Especifica la cantidad para subir o Bajar. Debe ser negativo para mover hacia arriba.

*point*<br/>
Contiene un [punto](/windows/desktop/api/windef/ns-windef-tagpoint) estructura o [CPoint](cpoint-class.md) especificar tanto las dimensiones de forma que se va a mover el objeto.

*size*<br/>
Contiene un [tamaño](/windows/desktop/api/windef/ns-windef-tagsize) estructura o [CSize](csize-class.md) especificar tanto las dimensiones de forma que se va a mover el objeto.

### <a name="remarks"></a>Comentarios

Mueve `CRect` *x* unidades a lo largo del eje x y *y* unidades a lo largo del eje y. El *x* y *y* parámetros son valores con signo, por lo que `CRect` se pueden mover izquierda o derecha y hacia arriba o abajo.

### <a name="example"></a>Ejemplo

```cpp
   CRect rect(0, 0, 35, 35);
   rect.OffsetRect(230, 230);

   // rect is now (230, 230, 265, 265)
   ASSERT(rect == CRect(230, 230, 265, 265));
```

##  <a name="operator_lpcrect"></a>  CRect::operator LPCRECT convierte un `CRect` a un [LPCRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>Comentarios

Cuando se usa esta función, no es necesario de dirección (**&**) operador. Este operador se usa automáticamente al pasar un `CRect` objeto a una función que espera un `LPCRECT`.

##  <a name="operator_lprect"></a>  CRect::operator LPRECT

Convierte un `CRect` a un [LPRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPRECT() throw();
```

### <a name="remarks"></a>Comentarios

Cuando se usa esta función, no es necesario de dirección (**&**) operador. Este operador se usa automáticamente al pasar un `CRect` objeto a una función que espera un `LPRECT`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CRect::operator LPCRECT](#operator_lpcrect).

##  <a name="operator_eq"></a>  CRect::operator =

Asigna *srcRect* a `CRect`.

```
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>Parámetros

*srcRect*<br/>
Hace referencia a un rectángulo de origen. Puede ser un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) o `CRect`.

### <a name="example"></a>Ejemplo

```cpp
   CRect rect(0, 0, 127, 168);
   CRect rect2;

   rect2 = rect;
   ASSERT(rect2 == CRect(0, 0, 127, 168));
```

##  <a name="operator_eq_eq"></a>  CRect::operator ==

Determina si `rect` es igual a `CRect` comparando las coordenadas de sus esquinas superior izquierda e inferior derecha.

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
Hace referencia a un rectángulo de origen. Puede ser un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) o `CRect`.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si son iguales; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1 == rect2);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1 == test);
```

##  <a name="operator_neq"></a>  CRect::operator! =

Determina si *rect* no es igual a `CRect` comparando las coordenadas de sus esquinas superior izquierda e inferior derecha.

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
Hace referencia a un rectángulo de origen. Puede ser un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) o `CRect`.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si no son iguales; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999,  6,  3);
ASSERT(rect1 != rect3);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect3 != test);
```

##  <a name="operator_add_eq"></a>  CRect::operator +=

Mover las dos primeras sobrecargas `CRect` por los desplazamientos especificados.

```
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parámetros

*point*<br/>
Un [punto](/windows/desktop/api/windef/ns-windef-tagpoint) estructura o [CPoint](cpoint-class.md) objeto que especifica el número de unidades para mover el rectángulo.

*size*<br/>
Un [tamaño](/windows/desktop/api/windef/ns-windef-tagsize) estructura o [CSize](csize-class.md) objeto que especifica el número de unidades para mover el rectángulo.

*lpRect*<br/>
Apunta a un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura o `CRect` objeto que contiene el número de unidades se infle cada lado de `CRect`.

### <a name="remarks"></a>Comentarios

El parámetro *x* y *y* (o `cx` y `cy`) se agregan valores a `CRect`.

La tercera sobrecarga aumenta `CRect` por el número de unidades especificadas en cada miembro del parámetro.

### <a name="example"></a>Ejemplo

```cpp
   CRect   rect1(100, 235, 200, 335);
   CPoint  pt(35, 65);
   CRect   rect2(135, 300, 235, 400);

   rect1 += pt;
   ASSERT(rect1 == rect2);
```

##  <a name="operator_-_eq"></a>  CRect::operator =

Mover las dos primeras sobrecargas `CRect` por los desplazamientos especificados.

```
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parámetros

*point*<br/>
Un [punto](/windows/desktop/api/windef/ns-windef-tagpoint) estructura o [CPoint](cpoint-class.md) objeto que especifica el número de unidades para mover el rectángulo.

*size*<br/>
Un [tamaño](/windows/desktop/api/windef/ns-windef-tagsize) estructura o [CSize](csize-class.md) objeto que especifica el número de unidades para mover el rectángulo.

*lpRect*<br/>
Apunta a un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura o `CRect` objeto que contiene el número de unidades a deflate cada lado de `CRect`.

### <a name="remarks"></a>Comentarios

El parámetro *x* y *y* (o `cx` y `cy`) se restan valores `CRect`.

La tercera sobrecarga desinfla `CRect` por el número de unidades especificadas en cada miembro del parámetro. Tenga en cuenta que esta sobrecarga funciona como [DeflateRect](#deflaterect).

### <a name="example"></a>Ejemplo

```cpp
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);

   rect1 -= pt;
   CRect   rectResult(65, 170, 165, 270);
   ASSERT(rect1 == rectResult);
```

##  <a name="operator_amp_eq"></a>  CRect::operator &amp;=

Conjuntos de `CRect` igual a la intersección de `CRect` y `rect`.

```
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
Contiene un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) o `CRect`.

### <a name="remarks"></a>Comentarios

La intersección es el rectángulo más grande que se encuentra en dos rectángulos.

> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CRect::IntersectRect](#intersectrect).

##  <a name="operator_or_eq"></a>  CRect::operator &#124;=

Conjuntos de `CRect` igual que la unión de `CRect` y `rect`.

```
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
Contiene un `CRect` o [RECT](/windows/desktop/api/windef/ns-windef-tagrect).

### <a name="remarks"></a>Comentarios

La unión es el rectángulo más pequeño que contiene ambos rectángulos de origen.

> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);

   rect1 |= rect2;
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect1);
```

##  <a name="operator_add"></a>  CRect::operator +

Las dos primeras sobrecargas devuelven un `CRect` objeto que es igual a `CRect` desplazados por los desplazamientos especificados.

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>Parámetros

*point*<br/>
Un [punto](/windows/desktop/api/windef/ns-windef-tagpoint) estructura o [CPoint](cpoint-class.md) objeto que especifica el número de unidades para mover el valor devuelto.

*size*<br/>
Un [tamaño](/windows/desktop/api/windef/ns-windef-tagsize) estructura o [CSize](csize-class.md) objeto que especifica el número de unidades para mover el valor devuelto.

*lpRect*<br/>
Apunta a un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura o `CRect` objeto que contiene el número de unidades se infle cada lado del valor devuelto.

### <a name="return-value"></a>Valor devuelto

El `CRect` resultante de mover o lo que infla `CRect` por el número de unidades especificadas en el parámetro.

### <a name="remarks"></a>Comentarios

El parámetro *x* y *y* (o `cx` y `cy`) se agregan parámetros a `CRect`posición de.

La tercera sobrecarga devuelve un nuevo `CRect` que es igual a `CRect` aumenta el número de unidades especificadas en cada miembro del parámetro.

### <a name="example"></a>Ejemplo

```cpp
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2;

   rect2 = rect1 + pt;
   CRect   rectResult(135, 300, 235, 400);
   ASSERT(rectResult == rect2);
```

##  <a name="operator_-"></a>  CRect::operator-

Las dos primeras sobrecargas devuelven un `CRect` objeto que es igual a `CRect` desplazados por los desplazamientos especificados.

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parámetros

*point*<br/>
Un [punto](/windows/desktop/api/windef/ns-windef-tagpoint) estructura o `CPoint` objeto que especifica el número de unidades para mover el valor devuelto.

*size*<br/>
Un [tamaño](/windows/desktop/api/windef/ns-windef-tagsize) estructura o `CSize` objeto que especifica el número de unidades para mover el valor devuelto.

*lpRect*<br/>
Apunta a un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura o `CRect` objeto que contiene el número de unidades a deflate cada lado del valor devuelto.

### <a name="return-value"></a>Valor devuelto

El `CRect` resultante de mover o desinflándose `CRect` por el número de unidades especificadas en el parámetro.

### <a name="remarks"></a>Comentarios

El parámetro *x* y *y* (o `cx` y `cy`) parámetros que se restan del `CRect`posición de.

La tercera sobrecarga devuelve un nuevo `CRect` que es igual a `CRect` disminuye el número de unidades especificadas en cada miembro del parámetro. Tenga en cuenta que esta sobrecarga funciona como [DeflateRect](#deflaterect), no [SubtractRect](#subtractrect).

### <a name="example"></a>Ejemplo

```cpp
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2;

   rect2 = rect1 - pt;
   CRect   rectResult(65, 170, 165, 270);
   ASSERT(rect2 == rectResult);
```

##  <a name="operator_amp"></a>  CRect::operator &amp;

Devuelve un `CRect` que es la intersección de `CRect` y *rect2*.

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>Parámetros

*rect2*<br/>
Contiene un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) o `CRect`.

### <a name="return-value"></a>Valor devuelto

Un `CRect` que es la intersección de `CRect` y *rect2*.

### <a name="remarks"></a>Comentarios

La intersección es el rectángulo más grande que se encuentra en dos rectángulos.

> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3 = rect1 & rect2;
   CRect   rectResult(100, 100, 200, 200);
   ASSERT(rectResult == rect3);
```

##  <a name="operator_or"></a>  CRect::operator &#124;

Devuelve un `CRect` que es la unión de `CRect` y *rect2*.

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>Parámetros

*rect2*<br/>
Contiene un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) o `CRect`.

### <a name="return-value"></a>Valor devuelto

Un `CRect` que es la unión de `CRect` y *rect2*.

### <a name="remarks"></a>Comentarios

La unión es el rectángulo más pequeño que contiene dos rectángulos.

> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3 = rect1 | rect2;
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect3);
```

##  <a name="ptinrect"></a>  CRect::PtInRect

Determina si el punto especificado está dentro de `CRect`.

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>Parámetros

*point*<br/>
Contiene un [punto](/windows/desktop/api/windef/ns-windef-tagpoint) estructura o [CPoint](cpoint-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el punto se encuentra dentro de `CRect`; de lo contrario, 0.

### <a name="remarks"></a>Comentarios

Un punto está dentro de `CRect` si se encuentra en el lado izquierdo o superior o está dentro de los cuatro lados. Un punto en el lado derecho o inferior está fuera `CRect`.

> [!NOTE]
>  Se debe normalizar el rectángulo o esta función puede producir un error. Puede llamar a [NormalizeRect](#normalizerect) normalizar rectángulo antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(5, 5, 100, 100);
CPoint pt1(35, 50);
CPoint pt2(125, 298);

// this is true, because pt1 is inside the rectangle
ASSERT(rect.PtInRect(pt1));

// this is NOT true, because pt2 is outside the rectangle
ASSERT(!rect.PtInRect(pt2));

// note that the right and the bottom aren't inside
ASSERT(!rect.PtInRect(CPoint(35, 100)));
ASSERT(!rect.PtInRect(CPoint(100, 98)));

// but the top and the left are inside
ASSERT(rect.PtInRect(CPoint(5, 65)));
ASSERT(rect.PtInRect(CPoint(88, 5)));

// and that PtInRect() works against a POINT, too
POINT pt;
pt.x = 35;
pt.y = 50;
ASSERT(rect.PtInRect(pt));
```

##  <a name="setrect"></a>  CRect::SetRect

Establece las dimensiones de `CRect` a las coordenadas especificadas.

```
void SetRect(int x1, int y1, int x2, int y2) throw();
```

### <a name="parameters"></a>Parámetros

*x1*<br/>
Especifica la coordenada x de la esquina superior izquierda.

*y1*<br/>
Especifica la coordenada y de la esquina superior izquierda.

*x2*<br/>
Especifica la coordenada x de la esquina inferior derecha.

*y2*<br/>
Especifica la coordenada y de la esquina inferior derecha.

### <a name="example"></a>Ejemplo

```cpp
   CRect rect;
   rect.SetRect(256, 256, 512, 512);
   ASSERT(rect == CRect(256, 256, 512, 512));
```

##  <a name="setrectempty"></a>  CRect::SetRectEmpty

Hace que `CRect` un rectángulo null estableciendo todas las coordenadas en cero.

```
void SetRectEmpty() throw();
```

### <a name="example"></a>Ejemplo

```cpp
CRect rect;
rect.SetRectEmpty();

// rect is now (0, 0, 0, 0)
ASSERT(rect.IsRectEmpty());
```

##  <a name="size"></a>  CRect::SIZE

El `cx` y `cy` miembros del valor devuelto contienen el alto y ancho de `CRect`.

```
CSize Size() const throw();
```

### <a name="return-value"></a>Valor devuelto

Un [CSize](csize-class.md) objeto que contiene el tamaño de `CRect`.

### <a name="remarks"></a>Comentarios

El alto o ancho puede ser negativo.

> [!NOTE]
>  Se debe normalizar el rectángulo o esta función puede producir un error. Puede llamar a [NormalizeRect](#normalizerect) normalizar rectángulo antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

##  <a name="subtractrect"></a>  CRect::SubtractRect

Hace que las dimensiones de la `CRect` igual que el resultado de restar `lpRectSrc2` desde `lpRectSrc1`.

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>Parámetros

*lpRectSrc1*<br/>
Apunta a la [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura o `CRect` objeto desde el que un rectángulo se va a restar.

*lpRectSrc2*<br/>
Apunta a la `RECT` estructura o `CRect` objeto que se va a restar el rectángulo que apunta el *lpRectSrc1* parámetro.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La resta es el rectángulo más pequeño que contiene todos los puntos de *lpRectScr1* que no están en la intersección de *lpRectScr1* y *lpRectScr2*.

El rectángulo especificado por *lpRectSrc1* cambiará si el rectángulo especificado por *lpRectSrc2* completamente no se superponga el rectángulo especificado por *lpRectSrc1*en al menos una de las direcciones x o y.

Por ejemplo, si *lpRectSrc1* fueron (10,10, 100,100) y *lpRectSrc2* fueron (50,50, 150,150), el rectángulo que apunta *lpRectSrc1* podría estar sin cambios al Devuelve la función. Si *lpRectSrc1* fueron (10,10, 100,100) y *lpRectSrc2* fueron (50,10, 150,150), sin embargo, el rectángulo apunta *lpRectSrc1* contendría las coordenadas (10,10, 50.100) cuando se devuelve la función.

`SubtractRect` no es igual a [operador -](#operator_-) ni [operador-=](#operator_-_eq). Ninguno de estos operadores nunca llama a `SubtractRect`.

> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
   RECT   rectOne;
   RECT   rectTwo;

   rectOne.left = 10;
   rectOne.top = 10;
   rectOne.bottom = 100;
   rectOne.right = 100;

   rectTwo.left = 50;
   rectTwo.top = 10;
   rectTwo.bottom = 150;
   rectTwo.right = 150;

   CRect   rectDiff;

   rectDiff.SubtractRect(&rectOne, &rectTwo);
CRect   rectResult(10, 10, 50, 100);

   ASSERT(rectDiff == rectResult);

   // works for CRect, too, since there is
   // implicit CRect -> LPCRECT conversion

   CRect rect1(10, 10, 100, 100);
   CRect rect2(50, 10, 150, 150);
   CRect rectOut;

   rectOut.SubtractRect(rect1, rect2);
   ASSERT(rectResult == rectOut);
```

##  <a name="topleft"></a>  CRect::TopLeft

Las coordenadas se devuelven como una referencia a un [CPoint](cpoint-class.md) objeto que se encuentra en `CRect`.

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>Valor devuelto

Las coordenadas de la esquina superior izquierda del rectángulo.

### <a name="remarks"></a>Comentarios

Puede usar esta función para obtener o establecer la esquina superior izquierda del rectángulo. Establece la esquina mediante el uso de esta función en el lado izquierdo del operador de asignación.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CRect::CenterPoint](#centerpoint).

##  <a name="unionrect"></a>  CRect::UnionRect

Hace que las dimensiones de `CRect` igual que la unión de los rectángulos de dos de origen.

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parámetros

*lpRect1*<br/>
Apunta a un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) o `CRect` que contiene un rectángulo de origen.

*lpRect2*<br/>
Apunta a un `RECT` o `CRect` que contiene un rectángulo de origen.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la unión no está vacía; 0 si la unión está vacía.

### <a name="remarks"></a>Comentarios

La unión es el rectángulo más pequeño que contiene ambos rectángulos de origen.

Windows omite las dimensiones del rectángulo vacío; es decir, un rectángulo que no tiene alto o no tiene ancho.

> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3.UnionRect(&rect1, &rect2);
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect3);
```

##  <a name="width"></a>  CRect::Width

Calcula el ancho de `CRect` restando el valor izquierdo desde el valor correcto.

```
int Width() const throw();
```

### <a name="return-value"></a>Valor devuelto

El ancho de `CRect`.

### <a name="remarks"></a>Comentarios

El ancho puede ser negativo.

> [!NOTE]
>  Se debe normalizar el rectángulo o esta función puede producir un error. Puede llamar a [NormalizeRect](#normalizerect) normalizar rectángulo antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
   CRect rect(20, 30, 80, 70);
   int nWid = rect.Width();
   // nWid is now 60
   ASSERT(nWid == 60);
```

## <a name="see-also"></a>Vea también

[CPoint (clase)](cpoint-class.md)<br/>
[CSize (clase)](csize-class.md)<br/>
[RECT](/windows/desktop/api/windef/ns-windef-tagrect)
