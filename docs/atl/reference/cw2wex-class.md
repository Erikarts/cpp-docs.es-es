---
title: Clase CW2WEX
ms.date: 11/04/2016
f1_keywords:
- CW2WEX
- ATLCONV/ATL::CW2WEX
- ATLCONV/ATL::CW2WEX::CW2WEX
- ATLCONV/ATL::CW2WEX::m_psz
- ATLCONV/ATL::CW2WEX::m_szBuffer
helpviewer_keywords:
- CW2WEX class
ms.assetid: 46262e56-e0d2-41fe-855b-0b67ecc8fcd7
ms.openlocfilehash: d6d68f4f5c0f3532c39fee3f513e7b3102ec075d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299483"
---
# <a name="cw2wex-class"></a>Clase CW2WEX

Esta clase se utiliza por las macros de conversión de cadena CW2TEX y CT2WEX y la definición de tipo CW2W.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <int t_nBufferLength = 128>
class CW2WEX
```

#### <a name="parameters"></a>Parámetros

*t_nBufferLength*<br/>
El tamaño del búfer usado en el proceso de traducción. La longitud predeterminada es de 128 bytes.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CW2WEX::CW2WEX](#cw2wex)|El constructor.|
|[CW2WEX::~CW2WEX](#dtor)|Destructor.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CW2WEX::operator LPWSTR](#operator_lpwstr)|Operador de conversión.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CW2WEX::m_psz](#m_psz)|El miembro de datos que almacena la cadena de origen.|
|[CW2WEX::m_szBuffer](#m_szbuffer)|El búfer estático, utilizado para almacenar la cadena convertida.|

## <a name="remarks"></a>Comentarios

A menos que se requiere una funcionalidad adicional, use CW2TEX, CT2WEX o CW2W en el código.

Esta clase contiene un búfer estático de tamaño fijo que se usa para almacenar el resultado de la conversión. Si el resultado es demasiado grande para caber en el búfer estático, la clase asigna memoria mediante **malloc**, libere la memoria cuando el objeto queda fuera del ámbito. Esto garantiza que, a diferencia del texto macros de conversión disponibles en versiones anteriores de ATL, esta clase es segura para el uso en bucles y que no desbordarán la pila.

Si la clase intenta asignar memoria en el montón y se produce un error, llamará a `AtlThrow` con un argumento de E_OUTOFMEMORY.

De forma predeterminada, las macros y clases de conversión de ATL usan la página de códigos ANSI del subproceso actual para la conversión.

Las macros siguientes se basan en esta clase:

- CW2TEX

- CT2WEX

La siguiente definición de tipo se basa en esta clase:

- CW2W

Para obtener una explicación de estas macros de conversión de texto, consulte [Macros de conversión de cadena de MFC y ATL](string-conversion-macros.md).

## <a name="example"></a>Ejemplo

Consulte [Macros de conversión de cadena de MFC y ATL](string-conversion-macros.md) para obtener un ejemplo del uso de estas macros de conversión de cadena.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlconv.h

##  <a name="cw2wex"></a>  CW2WEX::CW2WEX

El constructor.

```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La cadena de texto que se va a convertir.

*nCodePage*<br/>
La página de códigos. No se utiliza en esta clase.

### <a name="remarks"></a>Comentarios

Crea el búfer necesario para la traducción.

##  <a name="dtor"></a>  CW2WEX::~CW2WEX

El destructor...

```
~CW2WEX() throw();
```

### <a name="remarks"></a>Comentarios

Libera el búfer asignado.

##  <a name="m_psz"></a>  CW2WEX::m_psz

El miembro de datos que almacena la cadena de origen.

```
LPWSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CW2WEX::m_szBuffer

El búfer estático, utilizado para almacenar la cadena convertida.

```
wchar_t m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpwstr"></a>  CW2WEX::operator LPWSTR

Operador de conversión.

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la cadena de texto como un tipo LPWSTR.

## <a name="see-also"></a>Vea también

[CA2AEX (clase)](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX (clase)](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX (clase)](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX (clase)](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX (clase)](../../atl/reference/cw2cwex-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
