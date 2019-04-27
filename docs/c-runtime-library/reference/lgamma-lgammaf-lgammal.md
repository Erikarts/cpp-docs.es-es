---
title: lgamma, lgammaf, lgammal
ms.date: 04/05/2018
apiname:
- lgamma
- lgammaf
- lgammal
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
- lgamma
- lgammaf
- lgammal
- math/lgamma
- math/lgammaf
- math/lgammal
helpviewer_keywords:
- lgamma function
- lgammal function
- lgammaf function
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
ms.openlocfilehash: 43ce1599ab9161b9fadf5643ddd2ec739ab2d8b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157314"
---
# <a name="lgamma-lgammaf-lgammal"></a>lgamma, lgammaf, lgammal

Determina el logaritmo natural del valor absoluto de la función gamma del valor especificado.

## <a name="syntax"></a>Sintaxis

```C
double lgamma( double x );
float lgammaf( float x );
long double lgammal( long double x );
```

```cpp
float lgamma( float x ); //C++ only
long double lgamma( long double x ); //C++ only
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor que se va a calcular.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve el logaritmo natural del valor absoluto de la función gamma de *x*.

|Problema|Volver|
|-----------|------------|
|*x* = NaN|NaN|
|*x* = ±0|+INFINITY|
|*x*= entero negativo|+INFINITY|
|±INFINITY|+INFINITY|
|error de polo|+HUGE_VAL, +HUGE_VALF o +HUGE_VALL|
|error de intervalo de desbordamiento|±HUGE_VAL, ±HUGE_VALF o ±HUGE_VALL|

Los errores se notifican tal como se especifica en [_matherr](matherr.md).

## <a name="remarks"></a>Comentarios

Dado que C++ admite sobrecargas, puede llamar a sobrecargas de **lgamma** que toman y devuelven **float** y **largo** **doble** tipos. En un programa C, **lgamma** siempre toma y devuelve un **doble**.

Si x es un número racional, esta función devuelve el logaritmo del factorial de (x - 1).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**lgamma**, **lgammaf**, **lgammal**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[tgamma, tgammaf, tgammal](tgamma-tgammaf-tgammal.md)<br/>
