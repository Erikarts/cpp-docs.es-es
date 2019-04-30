---
title: _setmode
ms.date: 11/04/2016
apiname:
- _setmode
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
- _setmode
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
ms.openlocfilehash: 67cca27ba03a99d7e192d438a98f1bb3a93845ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356410"
---
# <a name="setmode"></a>_setmode

Establece el modo de traducción del archivo.

## <a name="syntax"></a>Sintaxis

```C
int _setmode (
   int fd,
   int mode
);
```

### <a name="parameters"></a>Parámetros

*fd*<br/>
Descriptor del archivo.

*mode*<br/>
Nuevo modo de traducción.

## <a name="return-value"></a>Valor devuelto

Si es correcto, devuelve el modo de traducción anterior.

Si se pasan parámetros no válidos a esta función, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve -1 y establece **errno** como **EBADF**, lo que indica un descriptor de archivo no válido, o **EINVAL**, que indica un no válido *modo* argumento.

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_setmode** la función establece *modo* el modo de traducción de archivo indicado por *fd*. Pasar **_O_TEXT** como *modo* establece el texto (que es, traducido) modo. Combinaciones de fuentes (CR-LF) de carro y de retorno de línea se traducen en una sola línea, carácter de avance en la entrada. Los caracteres de salto de línea se traducen a combinaciones CR-LF en la salida. Pasar **_O_BINARY** establece binario (sin traducir) el modo, en el que estas conversiones se suprimen.

También puede pasar **_O_U16TEXT**, **_O_U8TEXT**, o **_O_WTEXT** para habilitar el modo Unicode, como se muestra en el segundo ejemplo más adelante en este documento.

> [!CAUTION]
> Es el modo Unicode de funciones de impresión ancho (por ejemplo, `wprintf`) y no se admite para las funciones de impresión estrechas. Uso de una función de impresión estrecha en una secuencia de modo Unicode desencadena una aserción.

**_setmode** normalmente se usa para modificar el modo de traducción predeterminado de **stdin** y **stdout**, pero puede usar en cualquier archivo. Si aplica **_setmode** al descriptor de archivo para un flujo, llame a **_setmode** antes de realizar cualquier operación de entrada o salida en la secuencia.

> [!CAUTION]
> Si escribe datos en una secuencia de archivo explícitamente vuelque el código mediante el uso de [fflush](fflush.md) antes de usar **_setmode** para cambiar el modo. Si no vuelca el código, podría producirse un comportamiento inesperado. Si no ha escrito datos en el flujo, no será necesario volcarlo.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezados opcionales|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_setmode.c
// This program uses _setmode to change
// stdin from text mode to binary mode.

#include <stdio.h>
#include <fcntl.h>
#include <io.h>

int main( void )
{
   int result;

   // Set "stdin" to have binary mode:
   result = _setmode( _fileno( stdin ), _O_BINARY );
   if( result == -1 )
      perror( "Cannot set mode" );
   else
      printf( "'stdin' successfully changed to binary mode\n" );
}
```

```Output
'stdin' successfully changed to binary mode
```

## <a name="example"></a>Ejemplo

```C
// crt_setmodeunicode.c
// This program uses _setmode to change
// stdout to Unicode. Cyrillic and Ideographic
// characters will appear on the console (if
// your console font supports those character sets).

#include <fcntl.h>
#include <io.h>
#include <stdio.h>

int main(void) {
    _setmode(_fileno(stdout), _O_U16TEXT);
    wprintf(L"\x043a\x043e\x0448\x043a\x0430 \x65e5\x672c\x56fd\n");
    return 0;
}
```

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_set_fmode](set-fmode.md)<br/>
