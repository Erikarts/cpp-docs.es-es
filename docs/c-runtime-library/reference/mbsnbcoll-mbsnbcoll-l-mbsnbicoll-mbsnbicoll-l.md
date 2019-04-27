---
title: _mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l
ms.date: 11/04/2016
apiname:
- _mbsnbicoll_l
- _mbsnbcoll_l
- _mbsnbcoll
- _mbsnbicoll
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
- mbsnbicoll
- mbsnbcoll
- mbsnbicoll_l
- _mbsnbcoll
- _mbsnbicoll
- _ftcsnicoll
- _ftcsncoll
- mbsnbcoll_l
helpviewer_keywords:
- _mbsnbcoll_l function
- mbsnbcoll_l function
- _mbsnbcoll function
- _tcsnicoll function
- mbsnbcoll function
- mbsnbicoll_l function
- mbsnbicoll function
- _tcsncoll function
- _mbsnbicoll function
- _mbsnbicoll_l function
- tcsncoll function
- tcsnicoll function
ms.assetid: d139ed63-ccba-4458-baa2-61cbcef03e94
ms.openlocfilehash: c18faa3c93969a683b3ee3ef58dd02e1c1ae61f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156725"
---
# <a name="mbsnbcoll-mbsnbcolll-mbsnbicoll-mbsnbicolll"></a>_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l

Compara *n* bytes de dos cadenas de caracteres multibyte usando información de la página de códigos multibyte.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _mbsnbcoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbcoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
int _mbsnbicoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*string1*, *string2*<br/>
Cadenas que se van a comparar.

*count*<br/>
Número de bytes que se van a comparar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

El valor devuelto indica la relación de las subcadenas de *string1* y *cadena2*.

|Valor devuelto|Descripción|
|------------------|-----------------|
|< 0|*cadena1* subcadena menor *cadena2* subcadena.|
|0|*cadena1* idéntico de la subcadena *cadena2* subcadena.|
|> 0|*cadena1* subcadena mayor *cadena2* subcadena.|

Si *string1* o *cadena2* es **NULL** o *recuento* es mayor que **INT_MAX**, el no válido se invoca el controlador de parámetros, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **_NLSCMPERROR** y establecer **errno** a **EINVAL**. Para usar **_NLSCMPERROR**, incluya String.h o Mbstring.h.

## <a name="remarks"></a>Comentarios

Cada una de estas funciones intercala, como máximo, la primera *recuento* bytes en *string1* y *cadena2* y devuelve un valor que indica la relación entre resultante las subcadenas de *string1* y *cadena2*. Si el byte final de la subcadena de *string1* o *cadena2* es un byte inicial, no se incluye en la comparación; estas funciones solo comparan caracteres completos de las subcadenas. **_mbsnbicoll** es una versión de mayúsculas y minúsculas **_mbsnbcoll**. Al igual que [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) y [_mbsnbicmp](mbsnbicmp-mbsnbicmp-l.md), **_mbsnbcoll** y **_mbsnbicoll** intercalan las dos cadenas de caracteres multibyte según la orden lexicográfico especificado en la [página de códigos](../../c-runtime-library/code-pages.md) actualmente en uso.

En el caso de algunas páginas de códigos y los juegos de caracteres correspondientes, el orden de los caracteres del juego de caracteres no es igual que el orden lexicográfico de los caracteres. En la configuración regional de "C" no es así: el orden de los caracteres del juego de caracteres ASCII es igual que el orden lexicográfico de los caracteres. Sin embargo, en algunas páginas de códigos europeas, por ejemplo, el carácter “a” (valor 0x61) precede el carácter “ä” (valor 0xE4) en el juego de caracteres, pero el carácter “ä” precede el carácter “a” lexicográficamente. Para realizar una comparación lexicográfica de cadenas por bytes en ese caso, utilice **_mbsnbcoll** lugar **_mbsnbcmp**; para comprobar únicamente la igualdad de cadena, utilice **_mbsnbcmp**.

Dado que el **coll** funciones intercalan lexicográficamente las cadenas para la comparación, mientras que el **cmp** funciones prueban simplemente si las cadenas, el **coll** funciones son mucho más lento que el correspondiente **cmp** versiones. Por lo tanto, el **coll** funciones deben usarse solo cuando hay una diferencia entre el orden del conjunto de caracteres y el orden lexicográfico de los caracteres en la página de códigos actual y la diferencia de interés para la comparación.

El valor de salida se ve afectado por el valor de la categoría **LC_CTYPE** de la configuración regional; vea [setlocale](setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones sin el sufijo **_l** usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo **_l** son idénticas salvo que usan el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncoll**|[_strncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll**|[_wcsncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsncoll_l**|[_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll_l**|[_wcsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsnicoll**|[_strnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll**|[_wcsnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|
|**_tcsnicoll_l**|[_strnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll_l**|[_wcsnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbsnbcoll**|\<mbstring.h>|
|**_mbsnbcoll_l**|\<mbstring.h>|
|**_mbsnbicoll**|\<mbstring.h>|
|**_mbsnbicoll_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcoll (funciones)](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
