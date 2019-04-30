---
title: rand_s
ms.date: 1/02/2018
apiname:
- rand_s
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- rand_s
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, cryptographically secure
- random numbers, generating
- rand_s function
- numbers, pseudorandom
- cryptographically secure random numbers
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: d196a6f5d7483deb9a7e1b8d7fa929532b6197db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358130"
---
# <a name="rands"></a>rand_s

Genera un número pseudoaleatorio. Se trata de una versión más segura de la función [rand](rand.md), con mejoras de seguridad, como se describe en [características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>Parámetros

*randomValue*<br/>
Un puntero a un entero que contenga el valor generado.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto, código de error en caso contrario. Si el puntero de entrada _randomValue_ es un puntero nulo, la función invoca un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve **EINVAL** y establece **errno** a **EINVAL**. Si se produce un error en la función por cualquier otra razón, *_randomValue_ se establece en 0.

## <a name="remarks"></a>Comentarios

El **rand_s** función escribe un entero pseudoaleatorio entre 0 y **UINT_MAX** al puntero de entrada. El **rand_s** función usa el sistema operativo para generar números aleatorios criptográficamente seguros. No utiliza el valor de inicialización generado por el [srand](srand.md) función, tampoco afecta a la secuencia de números aleatorios utilizada por [rand](rand.md).

El **rand_s** función requiere que la constante **_CRT_RAND_S** definirse antes de la declaración de inclusión de la función se declaren, como en el ejemplo siguiente:

```C
#define _CRT_RAND_S
#include <stdlib.h>
```

**rand_s** depende de la [RtlGenRandom](/windows/desktop/api/ntsecapi/nf-ntsecapi-rtlgenrandom) API, que solo está disponible en Windows XP y versiones posteriores.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**rand_s**|\<stdlib.h>|

Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_rand_s.c
// This program illustrates how to generate random
// integer or floating point numbers in a specified range.

// Remembering to define _CRT_RAND_S prior
// to inclusion statement.
#define _CRT_RAND_S

#include <stdlib.h>
#include <stdio.h>
#include <limits.h>

int main( void )
{
    int             i;
    unsigned int    number;
    double          max = 100.0;
    errno_t         err;

    // Display 10 random integers in the range [ 1,10 ].
    for( i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %u\n", (unsigned int) ((double)number /
                       ((double) UINT_MAX + 1 ) * 10.0) + 1);
    }

    printf_s("\n");

    // Display 10 random doubles in [0, max).
    for (i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %g\n", (double) number /
                          ((double) UINT_MAX + 1) * max );
    }
}
```

### <a name="sample-output"></a>Resultados del ejemplo

```Output
10
4
5
2
8
2
5
6
1
1

32.6617
29.4471
11.5413
6.41924
20.711
60.2878
61.0094
20.1222
80.9192
65.0712
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
[srand](srand.md)<br/>
