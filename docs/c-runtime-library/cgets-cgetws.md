---
title: _cgets, _cgetws
ms.date: 4/2/2020
api_name:
- _cgetws
- _cgets
- _o__cgets
- _o__cgetws
api_location:
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-conio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- cgetws
- _cgetws
- _cgets
helpviewer_keywords:
- _cgetws function
- strings [C++], getting from console
- console, getting strings from
- _cgets function
- cgetws function
- cgets function
ms.assetid: 4d5e134a-58c3-4f62-befd-5d235b0212f4
ms.openlocfilehash: afffb691ca8bf8d180cac11ac5f16a84d871b1b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334412"
---
# <a name="_cgets-_cgetws"></a>_cgets, _cgetws

Obtiene una cadena de caracteres de la consola. Hay disponibles versiones más seguras de estas funciones; vea [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

> [!IMPORTANT]
> Estas funciones están obsoletas. A partir de Visual Studio 2015, no están disponibles en CRT. Las versiones seguras de estas funciones, _cgets_s y _cgetws_s, siguen estando disponibles. Para obtener información sobre estas funciones alternativas, vea [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```
char *_cgets(
   char *buffer
);
wchar_t *_cgetws(
   wchar_t *buffer
);
template <size_t size>
char *_cgets(
   char (&buffer)[size]
); // C++ only
template <size_t size>
wchar_t *_cgetws(
   wchar_t (&buffer)[size]
); // C++ only
```

#### <a name="parameters"></a>Parámetros

*Búfer*<br/>
Ubicación de almacenamiento de los datos.

## <a name="return-value"></a>Valor devuelto

`_cgets` y `_cgetws` devuelven un puntero al principio de la cadena, en `buffer[2]`. Si `buffer` es **NULL**, estas funciones invocan el controlador de parámetros no válido, como se describe en [Validación de parámetros](../c-runtime-library/parameter-validation.md). Si se permite que la ejecución continúe, devuelven **NULL** y establecen `errno` en `EINVAL`.

## <a name="remarks"></a>Observaciones

Estas funciones leen una cadena de caracteres de la consola y almacenan la cadena y su longitud en la ubicación que indica `buffer`. El parámetro `buffer` debe ser un puntero a una matriz de caracteres. El primer elemento de la matriz, `buffer[0]`, debe contener la longitud máxima (en caracteres) de la cadena que se va a leer. La matriz debe tener suficientes elementos para contener la cadena, un carácter de terminación nulo ('\0') y 2 bytes adicionales. La función lee los caracteres hasta una combinación de retorno de carro–salto de línea (CR-LF), o hasta que se lee el número de caracteres especificado. La cadena se almacena a partir de `buffer[2]`. Si la función lee una combinación CR-LF, almacena el carácter nulo ('\0'). A continuación, la función almacena la longitud real de la cadena en el segundo elemento de la matriz, `buffer[1]`.

Como todas las claves de edición están activas cuando se llama a `_cgets` o `_cgetws` desde una ventana de la consola, al presionar F3 se repite la última entrada.

En C++, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones. Para obtener más información, vea [Sobrecargas de plantilla seguras](../c-runtime-library/secure-template-overloads.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_cgetts`|`_cgets`|`_cgets`|`_cgetws`|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`_cgets`|\<conio.h>|
|`_cgetws`|\<conio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```c
// crt_cgets.c
// compile with: /c /W3
// This program creates a buffer and initializes
// the first byte to the size of the buffer. Next, the
// program accepts an input string using _cgets and displays
// the size and text of that string.

#include <conio.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
   char buffer[83] = { 80 };  // Maximum characters in 1st byte
   char *result;

   printf( "Input line of text, followed by carriage return:\n");

   // Input a line of text:
   result = _cgets( buffer ); // C4996
   // Note: _cgets is deprecated; consider using _cgets_s
   if (!result)
   {
      printf( "An error occurred reading from the console:"
              " error code %d\n", errno);
   }
   else
   {
      printf( "\nLine length = %d\nText = %s\n",
              buffer[1], result );
   }
}
```

```Output

      A line of input.Input line of text, followed by carriage return:
Line Length = 16
Text = A line of input.
```

## <a name="see-also"></a>Consulte también

[E/S de consola y puerto](../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch, _getwch](../c-runtime-library/reference/getch-getwch.md)
