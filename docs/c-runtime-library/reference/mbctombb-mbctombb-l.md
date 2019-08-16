---
title: _mbctombb, _mbctombb_l
ms.date: 11/04/2016
apiname:
- _mbctombb_l
- _mbctombb
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbctombb_l
- _mbctombb
- mbctombb_l
- mbctombb
helpviewer_keywords:
- _mbctombb function
- mbctombb_l function
- mbctombb function
- _mbctombb_l function
ms.assetid: d90970b8-71ff-4586-b6a2-f9ceb811f776
ms.openlocfilehash: 7395d94a6ec18f989d4a7153425b7af406a0bf45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331602"
---
# <a name="mbctombb-mbctombbl"></a>_mbctombb, _mbctombb_l

Convierte un carácter multibyte de doble byte en el carácter multibyte de un solo byte correspondiente.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
unsigned int _mbctombb(
   unsigned int c
);
unsigned int _mbctombb_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*c*<br/>
Carácter multibyte que se va a convertir.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Si es correcto, **_mbctombb** y **_mbctombb_l** devuelve el carácter de un byte que corresponde a *c*; de lo contrario devuelve *c* .

## <a name="remarks"></a>Comentarios

El **_mbctombb** y **_mbctombb_l** funciones convierten un carácter multibyte determinado en un carácter multibyte de byte único correspondiente. Caracteres deben corresponder a los caracteres de byte único dentro del intervalo 0 x 20-0x7E o 0xA1 - 0xDF va a convertir.

El valor de salida se ve afectado por el valor de la categoría **LC_CTYPE** de la configuración regional; vea [setlocale](setlocale-wsetlocale.md) para obtener más información. La versión de esta función sin el **_l** sufijo usa la configuración regional actual para este comportamiento dependiente de la configuración regional; la versión con el **_l** sufijo es idéntico, salvo que use el parámetro locale pasado en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En versiones anteriores, **_mbctombb** se llamó a **zentohan**. Use **_mbctombb** en su lugar.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbctombb**|\<mbstring.h>|
|**_mbctombb_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[_mbbtombc, _mbbtombc_l](mbbtombc-mbbtombc-l.md)<br/>
[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)<br/>
[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)<br/>
[_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)<br/>
