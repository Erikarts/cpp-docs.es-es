---
title: _access_s, _waccess_s
ms.date: 11/04/2016
api_name:
- _access_s
- _waccess_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- waccess_s
- access_s
- _waccess_s
- _access_s
helpviewer_keywords:
- access_s function
- taccess_s function
- _taccess_s function
- waccess_s function
- _access_s function
- _waccess_s function
ms.assetid: fb3004fc-dcd3-4569-8b27-d817546e947e
ms.openlocfilehash: e7e61369635a1a59ef16aa6262650d9648277eb0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171325"
---
# <a name="_access_s-_waccess_s"></a>_access_s, _waccess_s

Determina los permisos de lectura y escritura del archivo. Se trata de una versión de [_access, _waccess](access-waccess.md) con mejoras de seguridad, tal y como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _access_s(
   const char *path,
   int mode
);
errno_t _waccess_s(
   const wchar_t *path,
   int mode
);
```

### <a name="parameters"></a>Parámetros

*path*<br/>
Ruta de acceso del directorio o archivo.

*mode*<br/>
Configuración de permisos.

## <a name="return-value"></a>Valor devuelto

Cada función devuelve 0 si el archivo tiene el modo especificado. La función devuelve un código de error si el archivo especificado no existe o no está accesible en el modo especificado. En este caso, la función devuelve un código de error del conjunto de la manera siguiente y también establece `errno` en el mismo valor.

|valor de errno|Condición|
|-|-|
`EACCES`|Acceso denegado. La configuración de permisos del archivo no permite el acceso especificado.
`ENOENT`|No se encuentra el nombre o la ruta de acceso del archivo.
`EINVAL`|Parámetro no válido.

Para obtener más información, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

Cuando se usa con archivos, la función **_access_s** determina si el archivo especificado existe y se puede obtener acceso a él según se especifica en el valor del *modo*. Cuando se usa con directorios, **_access_s** solo determina si existe el directorio especificado. En Windows 2000 y sistemas operativos posteriores, todos los directorios tienen acceso de lectura y escritura.

|valor del modo|Comprueba el archivo para|
|----------------|---------------------|
|00|Solo existencia.|
|02|Permiso de escritura.|
|04|Permiso de lectura.|
|06|Permisos de lectura y escritura.|

Los permisos para leer o escribir en el archivo no bastan para garantizar la posibilidad de abrir un archivo. Por ejemplo, si un archivo está bloqueado por otro proceso, es posible que no se pueda obtener acceso a él aunque **_access_s** devuelva 0.

**_waccess_s** es una versión de caracteres anchos de **_access_s**, donde el argumento de *ruta de acceso* que se va a **_waccess_s** es una cadena de caracteres anchos. De lo contrario, **_waccess_s** y **_access_s** se comportan exactamente igual.

Estas funciones validan sus parámetros. Si *path* es null o el *modo* no especifica un modo válido, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven `EINVAL`.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess_s`|**_access_s**|**_access_s**|**_waccess_s**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_access_s**|\<io.h>|\<errno.h>|
|**_waccess_s**|\<wchar.h> o \<io.h>|\<errno.h>|

## <a name="example"></a>Ejemplo

En este ejemplo se usa **_access_s** para comprobar el archivo denominado crt_access_s. c para ver si existe y si se permite la escritura.

```C
// crt_access_s.c

#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    errno_t err = 0;

    // Check for existence.
    if ((err = _access_s( "crt_access_s.c", 0 )) == 0 )
    {
        printf_s( "File crt_access_s.c exists.\n" );

        // Check for write permission.
        if ((err = _access_s( "crt_access_s.c", 2 )) == 0 )
        {
            printf_s( "File crt_access_s.c does have "
                      "write permission.\n" );
        }
        else
        {
            printf_s( "File crt_access_s.c does not have "
                      "write permission.\n" );
        }
    }
    else
    {
        printf_s( "File crt_access_s.c does not exist.\n" );
    }
}
```

```Output
File crt_access_s.c exists.
File crt_access_s.c does not have write permission.
```

## <a name="see-also"></a>Consulte también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat (Funciones)](stat-functions.md)
