---
title: _fdopen, _wfdopen
ms.date: 12/12/2017
apiname:
- _fdopen
- _wfdopen
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tfdopen
- _fdopen
- _wfdopen
- wfdopen
- tfdopen
helpviewer_keywords:
- wfdopen function
- _fdopen function
- _wfdopen function
- tfdopen function
- fdopen function
- _tfdopen function
- streams, associating with files
ms.assetid: 262757ff-1e09-4472-a5b6-4325fc28f971
ms.openlocfilehash: 0cde110bf1dd12c23a6b0b658809502743d9edd3
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327166"
---
# <a name="fdopen-wfdopen"></a>_fdopen, _wfdopen

Asocia un flujo a un archivo que se abrió previamente para E/S de bajo nivel.

## <a name="syntax"></a>Sintaxis

```C
FILE *_fdopen(
   int fd,
   const char *mode
);
FILE *_wfdopen(
   int fd,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Parámetros

*FD*<br/>
Descriptor del archivo abierto.

*mode*<br/>
Tipo de acceso a archivos.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un puntero al flujo abierto. Un valor de puntero null indica un error. Si se produce un error, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EBADF**, lo que indica un descriptor de archivo incorrecto, o **EINVAL**, lo que indica que *modo*  era un puntero nulo.

Para obtener más información sobre estos y otros códigos error, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_fdopen** función asocia un flujo de E/S con el archivo que se identifica mediante *fd*, lo que permite a un archivo que está abierto para que E/S de bajo nivel se almacene en búfer y da formato. **_wfdopen** es una versión con caracteres anchos de **_fdopen**; el *modo* argumento **_wfdopen** es una cadena de caracteres anchos. **_wfdopen** y **_fdopen** en caso contrario, se comportan exactamente igual.

Pasado de descriptores de archivo **_fdopen** pertenecen por el valor devuelto **archivo &#42;**  secuencia. Si **_fdopen** es correcta, no llame a [ \_cerrar](close.md) en el descriptor de archivo. Una llamada a [fclose](fclose-fcloseall.md) devuelto **archivo &#42;**  también se cierra el descriptor de archivo.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|\_UNICODE y \_MBCS sin definir|\_MBCS definido|\_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

El *modo* cadena de caracteres especifica el tipo de acceso al archivo solicitado para el archivo:

| *mode* | Access |
|--------|--------|
| **"r"** | Abre para lectura. Si el archivo no existe o no se encuentra el **fopen** llamar se produce un error. |
| **"w"** | Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido. |
| **"a"** | Se abre para escritura al final del archivo (anexo). Crea el archivo si no existe. |
| **"r+"** | Abre para lectura y escritura. El archivo debe existir. |
| **"w+"** | Abre un archivo vacío para lectura y escritura. Si el archivo existe, se destruye su contenido. |
| **"a+"** | Se abre para lectura y anexado. Crea el archivo si no existe. |

Cuando se abre un archivo con el **"a"** o **"a +"** acceso tipo, todas las operaciones se producen al final del archivo de escritura. Se puede mover el puntero de archivo mediante [fseek](fseek-fseeki64.md) o [rebobinar](rewind.md), pero se desplaza siempre al final del archivo antes de cualquier escritura operación se lleva a cabo. Por consiguiente, los datos existentes no pueden sobrescribirse. Cuando el **"r +"**, **"w +"**, o **"a +"** se especifica el tipo de acceso, se permiten operaciones de lectura y escritura (se dice que el archivo esté abierto para "actualización"). Sin embargo, cuando se cambia entre lectura y escritura, debe haber una intervención [fflush](fflush.md), [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md), o [rebobinar](rewind.md) operación. Puede especificar la posición actual para el [fsetpos](fsetpos.md) o [fseek](fseek-fseeki64.md) operación, si desea.

Además de los valores anteriores, también se pueden incluir los siguientes caracteres en *modo* para especificar el modo de traducción de caracteres de nueva línea:

| *modo* modificador | Comportamiento |
|-----------------|----------|
| **t** | Abra en modo de texto (traducido). En este modo, las combinaciones de retorno de carro-avance de línea (CR-LF) se convierten en avances de una línea (LF) en la entrada, y los caracteres de LF se traducen en combinaciones de CR-LF en la salida. Además, Ctrl+Z se interpreta como carácter de final de archivo en la entrada. |
| **b** | Abre en modo binario (sin traducir). Las traducciones del **t** modo se suprimen. |
| **c** | Habilitar la marca de confirmación asociado *filename* para que el contenido del búfer del archivo se escribe directamente en el disco si **fflush** o **_flushall** se llama. |
| **n** | Restablecer la marca de confirmación asociado *filename* a "no-commit". Este es el valor predeterminado. También invalida la marca global de confirmación si vincula el programa a Commode.obj. El valor predeterminado de la marca global de confirmación es "no-commit" a menos que explícitamente vincule el programa a Commode.obj. |

El **t**, **c**, y **n** *modo* opciones son extensiones de Microsoft para **fopen** y **_fdopen**. No las use si desea conservar la portabilidad ANSI.

Si **t** o **b** no se proporciona en *modo*, el modo de traducción predeterminado está definido por la variable global [ \_fmode](../../c-runtime-library/fmode.md). Si **t** o **b** tiene como prefijo al argumento, la función no y devuelve NULL. Para obtener una descripción de los modos de texto y binario, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Los caracteres válidos para el *modo* cadena utilizada en **fopen** y **_fdopen** corresponden a *oflag* argumentos utilizados en [ \_abrir](open-wopen.md) y [ \_sopen](sopen-wsopen.md), tal y como se muestra en esta tabla:

|Los caracteres de *modo* cadena|Equivalente *oflag* valor **_open** y **_sopen**|
|---------------------------------|---------------------------------------------------|
|**a**|**\_O\_WRONLY &#124; \_O\_APPEND** (normalmente  **\_O\_WRONLY &#124; \_O\_crear &#124; \_o \_APPEND**)|
|**a +**|**\_O\_RDWR &#124; \_O\_APPEND** (normalmente  **\_O\_RDWR &#124; \_O\_APPEND &#124; \_O\_ CREAR** )|
|**r**|**\_O\_RDONLY**|
|**r +**|**\_O\_RDWR**|
|**W**|**\_O\_WRONLY** (normalmente  **\_O\_WRONLY &#124; \_O\_crear &#124; \_O\_TRUNC**)|
|**w +**|**\_O\_RDWR** (normalmente  **\_O\_RDWR &#124; \_O\_crear &#124; \_O\_TRUNC**)|
|**b**|**\_O\_BINARIO**|
|**t**|**\_O\_TEXTO**|
|**c**|Ninguna|
|**n**|Ninguna|

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fdopen**|\<stdio.h>|
|**_wfdopen**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```c
// crt_fdopen.c
// This program opens a file by using low-level
// I/O, then uses _fdopen to switch to stream
// access. It counts the lines in the file.

#include <stdlib.h>
#include <stdio.h>
#include <fcntl.h>
#include <io.h>
#include <share.h>

int main( void )
{
   FILE *stream;
   int  fd, count = 0;
   char inbuf[128];

   // Open a file.
   if( _sopen_s( &fd, "crt_fdopen.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
      exit( 1 );

   // Get stream from file descriptor.
   if( (stream = _fdopen( fd, "r" )) == NULL )
      exit( 1 );

   while( fgets( inbuf, 128, stream ) != NULL )
      count++;

   // After _fdopen, close by using fclose, not _close.
   fclose( stream );
   printf( "Lines in file: %d\n", count );
}
```

### <a name="input-crtfdopentxt"></a>Entrada: crt_fdopen.txt

```Input
Line one
Line two
```

### <a name="output"></a>Salida

```Output
Lines in file: 2
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[\_dup, \_dup2](dup-dup2.md)<br/>
[fclose, \_fcloseall](fclose-fcloseall.md)<br/>
[fopen, \_wfopen](fopen-wfopen.md)<br/>
[freopen, \_wfreopen](freopen-wfreopen.md)<br/>
[\_Abrir, \_wopen](open-wopen.md)<br/>
