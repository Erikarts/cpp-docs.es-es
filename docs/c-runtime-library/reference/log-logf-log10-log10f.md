---
title: log, LOGF (, logl, log10, log10f (, log10l
ms.date: 04/05/2018
api_name:
- log10f
- logf
- log10
- log
- log10l
- logl
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- logf
- logl
- _log10l
- log
- _logl
- log10f
- log10l
- log10
helpviewer_keywords:
- calculating logarithms
- log10f function
- log10 function
- log function
- log10l function
- logl function
- logf function
- logarithms
ms.assetid: 7adc77c2-04f7-4245-a980-21215563cfae
ms.openlocfilehash: f610ead4d71a877051fdec8df2a1564089141eea
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953225"
---
# <a name="log-logf-logl-log10-log10f-log10l"></a>log, LOGF (, logl, log10, log10f (, log10l

Calcula logaritmos.

## <a name="syntax"></a>Sintaxis

```C
double log( double x );
float logf( float x );
long double logl( double x );
double log10( double x );
float log10f ( float x );
long double log10l( double x );
```

```cpp
float log( float x );  // C++ only
long double log( long double x );  // C++ only
float log10( float x );  // C++ only
long double log10( long double x );  // C++ only
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor cuyo logaritmo hay que calcular.

## <a name="return-value"></a>Valor devuelto

Las funciones de **registro** devuelven el logaritmo natural (base *e*) de *x* si se realiza correctamente. Las funciones **log10** devuelven el logaritmo en base 10. Si *x* es negativo, estas funciones devuelven un valor indefinido (Ind), de forma predeterminada. Si *x* es 0, devuelven infinito (INF).

|Entrada|Excepción SEH|Excepción de Matherr|
|-----------|-------------------|-----------------------|
|± QNAN, IND|ninguna|_DOMAIN|
|± 0|ZERODIVIDE|_SING|
|*x* < 0|INVALID|_DOMAIN|

**log** y **log10** tienen una implementación que usa las extensiones SIMD de streaming 2 (sse2). Consulte [_set_SSE2_enable](set-sse2-enable.md) para obtener información y conocer las restricciones sobre el uso de la implementación de SSE2.

## <a name="remarks"></a>Comentarios

C++permite las sobrecargas, por lo que puede llamar a las sobrecargas de **log** y **log10** que toman y devuelven valores de tipo **float** o **Long Double** . En un programa de C, **log** y **log10** siempre toman y devuelven un valor **Double**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**log**, **logf**, **logl**, **log10**, **log10f**, **log10l**|\<math.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_log.c
/* This program uses log and log10
* to calculate the natural logarithm and
* the base-10 logarithm of 9,000.
*/

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 9000.0;
   double y;

   y = log( x );
   printf( "log( %.2f ) = %f\n", x, y );
   y = log10( x );
   printf( "log10( %.2f ) = %f\n", x, y );
}
```

```Output
log( 9000.00 ) = 9.104980
log10( 9000.00 ) = 3.954243
```

Para generar los logaritmos para otras bases, use la siguiente relación matemática: logaritmo base b de a == logaritmo natural (a) / logaritmo natural (b).

```cpp
// logbase.cpp
#include <math.h>
#include <stdio.h>

double logbase(double a, double base)
{
   return log(a) / log(base);
}

int main()
{
   double x = 65536;
   double result;

   result = logbase(x, 2);
   printf("Log base 2 of %lf is %lf\n", x, result);
}
```

```Output
Log base 2 of 65536.000000 is 16.000000
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md) <br/>
[exp, expf, expl](exp-expf.md) <br/>
[_matherr](matherr.md) <br/>
[pow, powf, powl](pow-powf-powl.md) <br/>
[_CIlog](../../c-runtime-library/cilog.md) <br/>
[_CIlog10](../../c-runtime-library/cilog10.md)<br/>
