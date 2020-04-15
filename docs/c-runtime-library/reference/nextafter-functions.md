---
title: nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl
ms.date: 4/2/2020
api_name:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
- _o__nextafter
- _o_nextafter
- _o_nextafterf
- _o_nextafterl
- _o_nexttoward
- _o_nexttowardf
- _o_nexttowardl
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- nextafter
- _nextafter
- nextafterf
- nextafterl
- _nextafterf
- math/nextafter
- math/nextafterf
- math/nextafterl
- nexttoward
- nexttowardf
- nexttowardl
- math/nexttoward
- math/nexttowardf
- math/nexttowardl
helpviewer_keywords:
- _nextafter function
- nextafter function
- _nextafterf function
- nextafterf function
- nextafterl function
- nexttoward function
- nexttowardf function
- nexttowardl function
ms.assetid: 9785bfb9-de53-4bd0-9637-f05fa0c1f6ab
ms.openlocfilehash: 7b1416147ed000dd3dd9a13bd52e41a474a8e9d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338563"
---
# <a name="nextafter-nextafterf-nextafterl-_nextafter-_nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl

Devuelve el siguiente valor de punto flotante que se pueda representar.

## <a name="syntax"></a>Sintaxis

```C
double nextafter( double x, double y );
float nextafterf( float x, float y );
long double nextafterl( long double x, long double y );

double _nextafter( double x, double y );
float _nextafterf( float x, float y ); /* x64 only */

double nexttoward( double x, long double y );
float nexttowardf( float x, long double y );
long double nexttowardl( long double x, long double y );
```

```cpp
float nextafter( float x, float y ); /* C++ only, requires <cmath> */
long double nextafter( long double x, long double y ); /* C++ only, requires <cmath> */

float nexttoward( float x, long double y ); /* C++ only, requires <cmath> */
long double nexttoward( long double x, long double y ); /* C++ only, requires <cmath> */
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Valor de punto flotante del que se va a comenzar.

*y y*<br/>
Valor de punto flotante al que se va.

## <a name="return-value"></a>Valor devuelto

Devuelve el siguiente valor de punto flotante representable del tipo de valor devuelto después de *x* en la dirección de *y*. Si *x* e *y* son iguales, la función devuelve *y*, convertido al tipo de valor devuelto, sin excepción desencadenada. Si *x* no es igual a *y*, y el resultado es un **denormal** o cero, se establecen los estados de excepción de punto flotante FE_UNDERFLOW y **FE_INEXACT** y el resultado correcto. Si *x* o *y* es un NAN, entonces el valor devuelto es uno de los NANs de entrada. Si *x* es finito y el resultado es infinito o no representable en el tipo, se devuelve un infinito o NAN firmado correctamente, se establecen **los** estados de excepción de punto flotante FE_OVERFLOW y **FE_INEXACT** y **errno** se establece en **ERANGE**.

## <a name="remarks"></a>Observaciones

Las familias de funciones **nextafter** y **nexttoward** son equivalentes, excepto para el tipo de parámetro de *y*. Si *x* e *y* son iguales, el valor devuelto es *y* convertido al tipo de valor devuelto.

Dado que C++ permite la \<sobrecarga, si incluye cmath> puede llamar a sobrecargas de **nextafter** y **nexttoward** que devuelven **float** y **long** **double** types. En un programa C, **después** y **siguiente** siempre devolver **doble**.

Las funciones **_nextafter** y **_nextafterf** son específicas de Microsoft. La función **_nextafterf** solo está disponible cuando se compila para x64.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario (C)|Encabezado necesario (C++)|
|-------------|---------------------------|-------------------------------|
|**siguiente,** **siguiente,** **siguiente,** **siguiente, _nextafterf**, **siguiente,** **siguiente**, siguiente , **siguiente**|\<math.h>|\<math.h> o \<cmath>|
|**_nextafter**|\<float.h>|\<float.h> o \<cfloat>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
