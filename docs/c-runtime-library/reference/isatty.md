---
title: _isatty
ms.date: 11/04/2016
apiname:
- _isatty
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
- _isatty
helpviewer_keywords:
- isatty function
- character device checking
- _isatty function
- checking character devices
ms.assetid: 9f1b2e87-0cd7-4079-b187-f2b7ca15fcbe
ms.openlocfilehash: ef0df5f859779c081df47ef4bfe938ec2601d524
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157479"
---
# <a name="isatty"></a>_isatty

Determina si un descriptor de archivo está asociado a un dispositivo de caracteres.

## <a name="syntax"></a>Sintaxis

```C
int _isatty( int fd );
```

### <a name="parameters"></a>Parámetros

*fd*<br/>
Descriptor de archivo que hace referencia al dispositivo que se va a probar.

## <a name="return-value"></a>Valor devuelto

**_isatty** devuelve un valor distinto de cero si descriptor está asociado con un dispositivo de caracteres. En caso contrario, **_isatty** devuelve 0.

## <a name="remarks"></a>Comentarios

El **_isatty** función determina si *fd* está asociado con un dispositivo de caracteres (un terminal, consola, impresora o puerto serie).

Esta función valida el *fd* parámetro. Si *fd* es un puntero de archivo incorrecto, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve 0 y establece **errno** a **EBADF**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_isatty**|\<io.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_isatty.c
/* This program checks to see whether
* stdout has been redirected to a file.
*/

#include <stdio.h>
#include <io.h>

int main( void )
{
   if( _isatty( _fileno( stdout ) ) )
      printf( "stdout has not been redirected to a file\n" );
   else
      printf( "stdout has been redirected to a file\n");
}
```

### <a name="sample-output"></a>Resultados del ejemplo

```Output
stdout has not been redirected to a file
```

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
