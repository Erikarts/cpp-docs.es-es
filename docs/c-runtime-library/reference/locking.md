---
title: _locking
ms.date: 11/04/2016
apiname:
- _locking
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _locking
helpviewer_keywords:
- locking function
- bytes [C++], locking file
- files [C++], locking bytes
- files [C++], locking
- _locking function
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
ms.openlocfilehash: 90327ed3388d4f18e0f64f92c33112c9ddd800f5
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327049"
---
# <a name="locking"></a>_locking

Bloquea o desbloquea los bytes de un archivo.

## <a name="syntax"></a>Sintaxis

```C
int _locking(
   int fd,
   int mode,
   long nbytes
);
```

### <a name="parameters"></a>Parámetros

*FD*<br/>
Descriptor del archivo.

*mode*<br/>
Acción de bloqueo que se va a realizar.

*nbytes*<br/>
Número de bytes que se van a bloquear.

## <a name="return-value"></a>Valor devuelto

**_Locking** devuelve 0 si es correcto. Un valor devuelto de -1 indica un error, en cuyo caso [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se establece en uno de los siguientes valores.

|valor de errno|Condición|
|-|-|
| **EACCES** | Infracción de bloqueo (archivo ya bloqueado o desbloqueado). |
| **EBADF** | Descriptor de archivo no válido. |
| **EDEADLOCK** | Infracción de bloqueo. Devuelve cuando el **_LK_LOCK** o **_LK_RLCK** se especifica la marca y el archivo no se puede bloquear después de 10 intentos. |
| **EINVAL** | No se proporcionó un argumento no válido para **_locking**. |

Si el error se debe a un parámetro incorrecto, como un descriptor de archivo no válido, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Comentarios

El **_locking** función bloquea o desbloquea *nbytes* bytes del archivo especificado por *fd*. El bloqueo de bytes en un archivo impide que otros procesos obtengan acceso a dichos bytes. Todos los bloqueos o desbloqueos comienzan en la posición actual del puntero de archivo y continúan durante los próximos *nbytes* bytes. Se pueden bloquear bytes después del final del archivo.

*mode* debe ser una de las siguientes constantes de manifiesto, que se definen en Locking.h.

|*modo* valor|Efecto|
|-|-|
| **_LK_LOCK** | Bloquea los bytes especificados. Si no se pueden bloquear los bytes, el programa lo vuelve a intentar inmediatamente después de 1 segundo. Si después de 10 intentos no se pueden bloquear los bytes, la constante devuelve un error. |
| **_LK_NBLCK** | Bloquea los bytes especificados. Si no se pueden bloquear los bytes, la constante devuelve un error. |
| **_LK_NBRLCK** | Igual que **_LK_NBLCK**. |
| **_LK_RLCK** | Igual que **_LK_LOCK**. |
| **_LK_UNLCK** | Desbloquea los bytes especificados, que deben haberse bloqueado anteriormente. |

Se pueden bloquear varias regiones de un archivo que no se superponen. Para desbloquear una región, primero debe haberse bloqueado. **_Locking** combina regiones adyacentes; si dos regiones bloqueadas son adyacentes, cada región debe desbloquearse por separado. Las regiones deberían bloquearse solo brevemente y deberían desbloquearse antes de cerrar un archivo o de salir del programa.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_locking**|\<io.h> y \<sys/locking.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_locking.c
/* This program opens a file with sharing. It locks
* some bytes before reading them, then unlocks them. Note that the
* program works correctly only if the file exists.
*/

#include <sys/types.h>
#include <sys/stat.h>
#include <sys/locking.h>
#include <share.h>
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include <io.h>

int main( void )
{
   int  fh, numread;
   char buffer[40];

   /* Quit if can't open file or system doesn't
    * support sharing.
    */
   errno_t err = _sopen_s( &fh, "crt_locking.txt", _O_RDONLY, _SH_DENYNO,
                          _S_IREAD | _S_IWRITE );
   printf( "%d %d\n", err, fh );
   if( err != 0 )
      exit( 1 );

   /* Lock some bytes and read them. Then unlock. */
   if( _locking( fh, LK_NBLCK, 30L ) != -1 )
   {
      long lseek_ret;
      printf( "No one can change these bytes while I'm reading them\n" );
      numread = _read( fh, buffer, 30 );
      buffer[30] = '\0';
      printf( "%d bytes read: %.30s\n", numread, buffer );
      lseek_ret = _lseek( fh, 0L, SEEK_SET );
      _locking( fh, LK_UNLCK, 30L );
      printf( "Now I'm done. Do what you will with them\n" );
   }
   else
      perror( "Locking failed\n" );

   _close( fh );
}
```

### <a name="input-crtlockingtxt"></a>Entrada: crt_locking.txt

```Input
The first thirty bytes of this file will be locked.
```

## <a name="sample-output"></a>Resultados del ejemplo

```Output
No one can change these bytes while I'm reading them
30 bytes read: The first thirty bytes of this
Now I'm done. Do what you will with them
```

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
