---
title: strcat_s, wcscat_s, _mbscat_s, _mbscat_s_l
ms.date: 01/22/2019
api_name:
- strcat_s
- _mbscat_s
- _mbscat_s_l
- wcscat_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strcat_s
- wcscat_s
- _mbscat_s
- _mbscat_s_l
helpviewer_keywords:
- wcscat_s function
- strcat_s function
- mbscat_s function
- strings [C++], appending
- _mbscat_s function
- _mbscat_s_l function
- appending strings
ms.assetid: 0f2f9901-c5c5-480b-98bc-f8f690792fc0
ms.openlocfilehash: 4449ec788b33a541a04a46d972f56f792797a16e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957989"
---
# <a name="strcat_s-wcscat_s-_mbscat_s-_mbscat_s_l"></a>strcat_s, wcscat_s, _mbscat_s, _mbscat_s_l

Anexa una cadena. Estas versiones de [strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md) incluyen mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbscat_s** y **_mbscat_s_l** no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t strcat_s(
   char *strDestination,
   size_t numberOfElements,
   const char *strSource
);
errno_t wcscat_s(
   wchar_t *strDestination,
   size_t numberOfElements,
   const wchar_t *strSource
);
errno_t _mbscat_s(
   unsigned char *strDestination,
   size_t numberOfElements,
   const unsigned char *strSource
);
errno_t _mbscat_s_l(
   unsigned char *strDestination,
   size_t numberOfElements,
   const unsigned char *strSource,
   _locale_t locale
);
template <size_t size>
errno_t strcat_s(
   char (&strDestination)[size],
   const char *strSource
); // C++ only
template <size_t size>
errno_t wcscat_s(
   wchar_t (&strDestination)[size],
   const wchar_t *strSource
); // C++ only
template <size_t size>
errno_t _mbscat_s(
   unsigned char (&strDestination)[size],
   const unsigned char *strSource
); // C++ only
template <size_t size>
errno_t _mbscat_s_l(
   unsigned char (&strDestination)[size],
   const unsigned char *strSource,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parámetros

*strDestination*<br/>
Búfer de cadena de destino terminada en NULL.

*numberOfElements*<br/>
Tamaño del búfer de cadena de destino.

*strSource*<br/>
Búfer de cadena de origen terminada en NULL.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.

### <a name="error-conditions"></a>Condiciones de error

|*strDestination*|*numberOfElements*|*strSource*|Valor devuelto|Contenido de *strDestination*|
|----------------------|------------------------|-----------------|------------------|----------------------------------|
|**Null** o sin terminar|any|any|**EINVAL**|no modificado|
|any|any|**NULL**|**EINVAL**|*strDestination* [0] se establece en 0|
|any|0, o demasiado pequeño|any|**ERANGE**|*strDestination* [0] se establece en 0|

## <a name="remarks"></a>Comentarios

La función **strcat_s** anexa *strSource* a *strDestination* y termina la cadena resultante con un carácter nulo. El carácter inicial de *strSource* sobrescribe el carácter nulo de terminación de *strDestination*. El comportamiento de **strcat_s** no está definido si las cadenas de origen y de destino se superponen.

Observe que el segundo parámetro es el tamaño total del búfer, no el tamaño restante:

```C
char buf[16];
strcpy_s(buf, 16, "Start");
strcat_s(buf, 16, " End");               // Correct
strcat_s(buf, 16 - strlen(buf), " End"); // Incorrect
```

**wcscat_s** y **_mbscat_s** son versiones de caracteres anchos y multibyte de **strcat_s**. Los argumentos y el valor devuelto de **wcscat_s** son cadenas de caracteres anchos; los de **_mbscat_s** son cadenas de caracteres multibyte. Estas tres funciones se comportan exactamente igual.

Si *strDestination* es un puntero nulo o no termina en null, o si *strSource* es un puntero **nulo** , o si la cadena de destino es demasiado pequeña, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **EINVAL** y establecen **errno** en **EINVAL**.

Las versiones de las funciones que tienen el sufijo **_L** tienen el mismo comportamiento, pero utilizan el parámetro de configuración regional que se pasa en lugar de la configuración regional actual. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Las versiones de depuración de estas funciones rellenan primero el búfer con 0xFD. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscat_s**|**strcat_s**|**_mbscat_s**|**wcscat_s**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strcat_s**|\<string.h>|
|**wcscat_s**|\<string.h> o \<wchar.h>|
|**_mbscat_s**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de código de [strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md).

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
