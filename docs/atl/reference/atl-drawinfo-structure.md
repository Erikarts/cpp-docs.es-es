---
title: ATL_DRAWINFO (estructura)
ms.date: 11/04/2016
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
ms.openlocfilehash: 77ef56f73be1ed9ddfc63c459b6bab3ad4decb3f
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503414"
---
# <a name="atldrawinfo-structure"></a>ATL_DRAWINFO (estructura)

Contiene información utilizada para la representación a varios destinos, como una impresora, metarchivo o control ActiveX.

## <a name="syntax"></a>Sintaxis

```
struct ATL_DRAWINFO {
    UINT cbSize;
    DWORD dwDrawAspect;
    LONG lindex;
    DVTARGETDEVICE* ptd;
    HDC hicTargetDev;
    HDC hdcDraw;
    LPCRECTL prcBounds;
    LPCRECTL prcWBounds;
    BOOL bOptimize;
    BOOL bZoomed;
    BOOL bRectInHimetric;
    SIZEL ZoomNum;
    SIZEL ZoomDen;
};
```

## <a name="members"></a>Miembros

`cbSize`<br/>
El tamaño de la estructura, en bytes.

`dwDrawAspect`<br/>
Especifica cómo se puede representar el destino. Representaciones pueden incluir contenido, un icono, una vista en miniatura o un documento impreso. Para obtener una lista de valores posibles, vea [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect) y [DVASPECT2](/windows/desktop/api/ocidl/ne-ocidl-tagdvaspect2).

`lindex`<br/>
Parte del destino que es de interés para la operación de dibujo. Su interpretación varía según el valor de la `dwDrawAspect` miembro.

`ptd`<br/>
Puntero a un [DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice) estructura que permite optimizaciones de dibujos dependen del aspecto especificado. Tenga en cuenta que más reciente objetos y contenedores que admiten las interfaces de dibujos optimizadas admiten a también este miembro. Antiguos objetos y contenedores que no admiten interfaces dibujos optimizadas siempre especifican NULL para este miembro.

`hicTargetDev`<br/>
Información de contexto para el dispositivo de destino que apunta `ptd` desde el que el objeto puede extraer las métricas del dispositivo y probar las funcionalidades del dispositivo. Si `ptd` es NULL, el objeto debe omitir el valor en el `hicTargetDev` miembro.

`hdcDraw`<br/>
El contexto de dispositivo en el que se va a dibujar. Para un objeto sin ventana, el `hdcDraw` miembro está en el `MM_TEXT` modo de asignación con sus coordenadas lógicas coincidencia de las coordenadas de cliente de la ventana contenedora. Además, el contexto de dispositivo debe estar en el mismo estado que normalmente se pasa por un `WM_PAINT` mensaje.

`prcBounds`<br/>
Puntero a un [RECTL](/previous-versions//dd162907\(v=vs.85\)) estructura que especifica el rectángulo en `hdcDraw` y en la que se debe dibujar el objeto. Este miembro controla el posicionamiento y la ampliación del objeto. Este miembro debe ser NULL para dibujar el objeto activo en contexto sin ventana. En todas las otras situaciones, NULL no es un valor válido y debe tener como resultado un `E_INVALIDARG` código de error. Si el contenedor pasa un valor distinto de NULL a un objeto sin ventana, el objeto debe representar el aspecto solicitado en el contexto de dispositivo especificado y el rectángulo. Un contenedor puede solicitarla desde un objeto sin ventana para representar una vista en segundo lugar, no activos del objeto o para imprimir el objeto.

`prcWBounds`<br/>
Si `hdcDraw` es un contexto de dispositivo de metarchivo (consulte [GetDeviceCaps](/windows/desktop/api/wingdi/nf-wingdi-getdevicecaps) en el SDK de Windows), este es un puntero a un `RECTL` estructura que especifica el rectángulo delimitador en el metarchivo subyacente. La estructura de rectángulo contiene la extensión de la ventana y el origen de la ventana. Estos valores son útiles para dibujar metarchivos. El rectángulo indicado por `prcBounds` está anidada dentro de este `prcWBounds` rectángulo; están en el mismo espacio de coordenadas.

`bOptimize`<br/>
Distinto de cero si el dibujo del control es ser optimizado, en caso contrario, 0. Si se optimiza el dibujo, el estado del contexto del dispositivo se restaura automáticamente cuando termine de representación.

`bZoomed`<br/>
Distinto de cero si el destino tiene un factor de zoom, de lo contrario, 0. El factor de zoom se almacena en `ZoomNum`.

`bRectInHimetric`<br/>
Distinto de cero si las dimensiones de `prcBounds` en HIMETRIC, en caso contrario, 0.

`ZoomNum`<br/>
El ancho y alto del rectángulo en el que se representa el objeto. El factor de zoom en el eje x (la proporción de tamaño natural del objeto a su alcance actual) del destino es el valor de `ZoomNum.cx` dividido por el valor de `ZoomDen.cx`. De forma similar, se consigue el factor de zoom en el eje y.

`ZoomDen`<br/>
El ancho real y el alto del destino.

## <a name="remarks"></a>Comentarios

Uso típico de esta estructura sería la recuperación de información durante la representación del objeto de destino. Por ejemplo, podría recuperar valores de ATL_DRAWINFO dentro de la sobrecarga de [CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).

Esta estructura almacena información pertinente que se usa para representar la apariencia de un objeto para el dispositivo de destino. La información proporcionada puede usarse en dibujar en la pantalla, una impresora o incluso un metarchivo.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="see-also"></a>Vea también

[Clases y structs](../../atl/reference/atl-classes.md)<br/>
[IViewObject::Draw](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
