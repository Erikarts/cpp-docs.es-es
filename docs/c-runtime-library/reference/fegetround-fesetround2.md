---
title: fegetround, fesetround
ms.date: 04/05/2018
apiname:
- fegetround
- fesetround
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fegetround
- fesetround
- fenv/fegetround
- fenv/fesetround
helpviewer_keywords:
- fegetround function
- fesetround function
ms.assetid: 596af00b-be2f-4f57-b2f5-460485f9ff0b
ms.openlocfilehash: 061f0c9563d284396e85c6de70a2fe0911218eb3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334377"
---
# <a name="fegetround-fesetround"></a>fegetround, fesetround

Obtiene o establece el modo de redondeo de punto flotante actual.

## <a name="syntax"></a>Sintaxis

```C
int fegetround(void);

int fesetround(
   int round_mode
);
```

### <a name="parameters"></a>Parámetros

*round_mode*<br/>
El modo de redondeo que se va a establecer, como una de las macros de redondeo de punto flotante. Si el valor no es igual a una de las macros de redondeo de punto flotante, no se cambiará el modo de redondeo.

## <a name="return-value"></a>Valor devuelto

Si se ejecuta correctamente, **fegetround** devuelve el modo de redondeo como uno de los valores de la macro de redondeo de punto flotante. Devuelve un valor negativo si no se puede determinar el modo de redondeo actual.

Si se ejecuta correctamente, **fesetround** devuelve 0. De lo contrario, devuelve un valor distinto de cero.

## <a name="remarks"></a>Comentarios

Las operaciones de punto flotante pueden usar uno de los distintos modos de redondeo. Estos controlan en qué dirección se redondean los resultados de las operaciones de punto flotante cuando se almacenan los resultados. Se trata de los nombres y comportamientos de las macros de redondeo de punto flotante que se definen en \<fenv.h>:

|Macro|Descripción|
|-----------|-----------------|
|FE_DOWNWARD|Redondeo a infinito negativo.|
|FE_TONEAREST|Redondeo al más próximo.|
|FE_TOWARDZERO|Redondeo a cero.|
|FE_UPWARD|Redondeo a infinito positivo.|

El comportamiento predeterminado de FE_TONEAREST es redondear los resultados que se encuentran entre valores representables al valor más próximo con un bit menos significativo par (0).

El modo de redondeo actual afecta a estas operaciones:

- Las conversiones de cadenas.

- Los resultados de los operadores aritméticos de punto flotante fuera de las expresiones constantes.

- La biblioteca de redondeo de las funciones, como **rint** y **nearbyint**.

- Los valores devueltos de las funciones matemáticas de la biblioteca estándar.

El modo de redondeo actual no afecta a estas operaciones:

- El **trunc**, **ceil**, **floor**, y **lround** funciones de la biblioteca.

- Las conversiones implícitas de punto flotante a entero, que siempre se redondean a cero.

- Los resultados de los operadores aritméticos de punto flotante en expresiones constantes, que siempre se redondean al valor más cercano.

Para usar estas funciones, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante la directiva `#pragma fenv_access(on)` antes de la llamada. Para obtener más información, consulte [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**fegetround**, **fesetround**|\<fenv.h>|\<cfenv>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[nearbyint, nearbyintf, nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint, rintf, rintl](rint-rintf-rintl.md)<br/>
[lrint, lrintf, lrintl, llrint, llrintf, llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
