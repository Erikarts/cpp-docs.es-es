---
title: _strtime_s, _wstrtime_s
ms.date: 11/04/2016
apiname:
- _wstrtime_s
- _strtime_s
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wstrtime_s
- strtime_s
- wstrtime_s
- _strtime_s
helpviewer_keywords:
- wstrtime_s function
- copying time to buffers
- strtime_s function
- _wstrtime_s function
- time, copying
- _strtime_s function
ms.assetid: 42acf013-c334-485d-b610-84c0af8a46ec
ms.openlocfilehash: 579c4a99b52c66bd14cea947eaa1f301cc1127e1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375332"
---
# <a name="strtimes-wstrtimes"></a>_strtime_s, _wstrtime_s

Copia la hora actual en un búfer. Se trata de versiones de [_strtime, _wstrtime](strtime-wstrtime.md) que incluyen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _strtime_s(
   char *buffer,
   size_t numberOfElements
);
errno_t _wstrtime_s(
   wchar_t *buffer,
   size_t numberOfElements
);
template <size_t size>
errno_t _strtime_s(
   char (&buffer)[size]
); // C++ only
template <size_t size>
errno_t _wstrtime_s(
   wchar_t (&buffer)[size]
); // C++ only
```

### <a name="parameters"></a>Parámetros

*buffer*<br/>
Búfer (con una longitud mínima de 10 bytes) en el que se escribirá la hora.

*numberOfElements*<br/>
Tamaño del búfer.

## <a name="return-value"></a>Valor devuelto

Cero si es correcta.

Si se produce una condición de error, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si se produce un error, el valor devuelto es un código de error. Los códigos de error se definen en ERRNO.H; consulte la tabla siguiente para ver los errores exactos generados por esta función. Para obtener más información sobre los códigos de error, vea [errno (Constantes)](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Condiciones de error

|*buffer*|*numberOfElements*|Volver|Contenido de *búfer*|
|--------------|------------------------|------------|--------------------------|
|**NULL**|(cualquiera)|**EINVAL**|No modificado|
|No **NULL** (apunta al búfer válido)|0|**EINVAL**|No modificado|
|No **NULL** (apunta al búfer válido)|0 < tamaño < 9|**EINVAL**|Cadena vacía|
|No **NULL** (apunta al búfer válido)|Tamaño > 9|0|Hora actual con el formato especificado en la sección de comentarios|

## <a name="security-issues"></a>Problemas de seguridad

Pasar a un no válido que no sean de**NULL** valor para el búfer, se producirá una infracción de acceso si el *numberOfElements* parámetro es mayor que 9.

Pasar un valor para *numberOfElements* mayor que el tamaño real del búfer dará como resultado de la saturación del búfer.

## <a name="remarks"></a>Comentarios

Estas funciones proporcionan versiones más seguras de [_strtime](strtime-wstrtime.md) y [_wstrtime](strtime-wstrtime.md). El **_strtime_s** función copia la hora local actual en el búfer señalado por *timestr*. La hora se formatea como **hh: mm:** donde **hh** son dos dígitos que representa la hora en la notación de 24 horas, **mm** son dos dígitos que representa los minutos transcurridos tras la hora y **ss** son dos dígitos que representan los segundos. Por ejemplo, la cadena **18:23:44** representa 23 minutos y 44 segundos después de las 6 P.M. El búfer debe tener una longitud mínima de 9 bytes; el segundo parámetro especifica el tamaño real.

**_wstrtime** es una versión con caracteres anchos de **_strtime**; el argumento y el valor devuelto de **_wstrtime** son cadenas de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mapping"></a>Asignación de rutina de texto genérico:

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime_s**|**_strtime_s**|**_strtime_s**|**_wstrtime_s**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_strtime_s**|\<time.h>|
|**_wstrtime_s**|\<time.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// strtime_s.c

#include <time.h>
#include <stdio.h>

int main()
{
    char tmpbuf[9];
    errno_t err;

    // Set time zone from TZ environment variable. If TZ is not set,
    // the operating system is queried to obtain the default value
    // for the variable.
    //
    _tzset();

    // Display operating system-style date and time.
    err = _strtime_s( tmpbuf, 9 );
    if (err)
    {
       printf("_strdate_s failed due to an invalid argument.");
      exit(1);
    }
    printf( "OS time:\t\t\t\t%s\n", tmpbuf );
    err = _strdate_s( tmpbuf, 9 );
    if (err)
    {
       printf("_strdate_s failed due to an invalid argument.");
       exit(1);
    }
    printf( "OS date:\t\t\t\t%s\n", tmpbuf );

}
```

```Output
OS time:            14:37:49
OS date:            04/25/03
```

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
