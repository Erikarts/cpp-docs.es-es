---
title: __min
ms.date: 04/05/2018
apiname:
- __min
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
apitype: DLLExport
f1_keywords:
- __min
- min
- _min
helpviewer_keywords:
- __min macro
- min macro
- minimum macro
- _min macro
ms.assetid: 2037f26c-b48a-4a69-8870-22519f052a3c
ms.openlocfilehash: f9e867cd1f3e3519e440c91895e61e317d9688a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156556"
---
# <a name="min"></a>__min

Macro de preprocesador que devuelve el menor de dos valores.

## <a name="syntax"></a>Sintaxis

```C
#define __min(a,b) (((a) < (b)) ? (a) : (b))
```

### <a name="parameters"></a>Parámetros

*a*, *b*<br/>
Valores de cualquier tipo que el **<** operador funciona en.

## <a name="return-value"></a>Valor devuelto

El menor de los dos argumentos.

## <a name="remarks"></a>Comentarios

El **__min** macro compara dos valores y devuelve el valor del más pequeño. Los argumentos pueden ser de cualquier tipo de datos numérico, con o sin signo. Los argumentos y el valor devuelto deben ser del mismo tipo de datos.

El argumento devuelto se evalúa dos veces, la macro. Esto puede provocar resultados inesperados si el argumento es una expresión que se modifica su valor cuando sea evaluado, tales como `*p++`.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**__min**|\<stdlib.h>|

## <a name="example"></a>Ejemplo

```C
// crt_minmax.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int a = 10;
   int b = 21;

   printf( "The larger of %d and %d is %d\n",  a, b, __max( a, b ) );
   printf( "The smaller of %d and %d is %d\n", a, b, __min( a, b ) );
}
```

```Output
The larger of 10 and 21 is 21
The smaller of 10 and 21 is 10
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[__max](max.md)<br/>
