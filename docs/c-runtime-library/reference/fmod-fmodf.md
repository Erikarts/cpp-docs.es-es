---
title: fmod, fmodf, fmodl
ms.date: 04/05/2018
apiname:
- fmod
- fmodf
- fmodl
apilocation:
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
apitype: DLLExport
f1_keywords:
- fmod
- _fmodl
- fmodf
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmodl function
- fmod function
- floating-point numbers, calculating remainders
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
ms.openlocfilehash: 78677be1a0c9921c35e54d43a00b8956a9d858b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605351"
---
# <a name="fmod-fmodf-fmodl"></a>fmod, fmodf, fmodl

Calcula el resto de punto flotante.

## <a name="syntax"></a>Sintaxis

```C
double fmod(
   double x,
   double y
);
float fmod(
   float x,
   float y
);  // C++ only
long double fmod(
   long double x,
   long double y
);  // C++ only
float fmodf(
   float x,
   float y
);
long double fmodl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>Parámetros

*x*, *y*<br/>
Valores de punto flotante.

## <a name="return-value"></a>Valor devuelto

**fmod** devuelve el resto de punto flotante *x* / *y*. Si el valor de *y* es 0,0, **fmod** devuelve un valor NaN. Para obtener información acerca de la representación de un NaN reservado por la **printf** familia, vea [printf](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Comentarios

El **fmod** función calcula el resto de punto flotante *f* de *x* / *y* que *x*  =  *i* \* *y* + *f*, donde *i* es un entero, *f* tiene el mismo signo que *x*y el valor absoluto de *f* es menor que el valor absoluto de *y*.

C++ permite las sobrecargas, es posible llamar a las sobrecargas de **fmod** que toman y devuelven **float** y **largo** **doble** valores. En un programa C, **fmod** siempre toma dos **doble** argumentos y devuelve un **doble**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fmod**, **fmodf**, **fmodl**|\<math.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fmod.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = fmod( w, x );
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[_CIfmod](../../c-runtime-library/cifmod.md)<br/>
