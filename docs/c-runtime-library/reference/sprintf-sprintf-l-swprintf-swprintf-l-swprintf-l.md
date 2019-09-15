---
title: sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l
ms.date: 11/04/2016
api_name:
- __swprintf_l
- sprintf
- _sprintf_l
- _swprintf_l
- swprintf
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _stprintf_l
- __swprintf_l
- sprintf_l
- swprintf
- _sprintf_l
- sprintf
- _stprintf
- stprintf_l
helpviewer_keywords:
- _swprintf_l function
- _stprintf function
- __swprintf_l function
- stprintf function
- sprintf function
- _sprintf_l function
- _stprintf_l function
- swprintf function
- strings [C++], writing to
- _CRT_NON_CONFORMING_SWPRINTFS
- swprintf_l function
- stprintf_l function
- sprintf_l function
- formatted text [C++]
ms.assetid: f6efe66f-3563-4c74-9455-5411ed939b81
ms.openlocfilehash: c9a306788045fc6fe52da835029d32cfc42c0ed4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958290"
---
# <a name="sprintf-_sprintf_l-swprintf-_swprintf_l-__swprintf_l"></a>sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l

Escribir datos con formato en una cadena. Hay disponibles versiones más seguras de algunas de estas funciones; vea [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md). Las versiones seguras de **swprintf** y **_swprintf_l** no toman un parámetro de *recuento* .

## <a name="syntax"></a>Sintaxis

```C
int sprintf(
   char *buffer,
   const char *format [,
   argument] ...
);
int _sprintf_l(
   char *buffer,
   const char *format,
   locale_t locale [,
   argument] ...
);
int swprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format [,
   argument]...
);
int _swprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
int __swprintf_l(
   wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
template <size_t size>
int sprintf(
   char (&buffer)[size],
   const char *format [,
   argument] ...
); // C++ only
template <size_t size>
int _sprintf_l(
   char (&buffer)[size],
   const char *format,
   locale_t locale [,
   argument] ...
); // C++ only
```

### <a name="parameters"></a>Parámetros

*buffer*<br/>
Ubicación de almacenamiento para los resultados

*count*<br/>
Número máximo de caracteres que se van a almacenar en la versión Unicode de esta función.

*format*<br/>
Cadena de control de formato

*argument*<br/>
Argumentos opcionales

*locale*<br/>
Configuración regional que se va a usar.

Para más información, vea [Especificaciones de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Valor devuelto

Número de caracteres escritos, o-1 si se ha producido un error. Si *buffer* o *Format* es un puntero nulo, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven-1 y establecen **errno** en **EINVAL**.

**sprintf** devuelve el número de bytes almacenados en el *búfer*, sin contar el carácter null de terminación. **swprintf** devuelve el número de caracteres anchos almacenados en el *búfer*, sin contar el carácter ancho final null.

## <a name="remarks"></a>Comentarios

La función **sprintf** da formato y almacena una serie de caracteres y valores en el *búfer*. Cada *argumento* (si existe) se convierte y se genera de acuerdo con la especificación de formato correspondiente en *Format*. El formato consta de caracteres ordinarios y tiene el mismo formato y función que el argumento de *formato* de [printf](printf-printf-l-wprintf-wprintf-l.md). Un carácter null se anexa después del último carácter escrito. Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.

> [!IMPORTANT]
> Mediante **sprintf**, no hay forma de limitar el número de caracteres escritos, lo que significa que el código que usa **sprintf** es susceptible a las saturaciones del búfer. Considere la posibilidad de usar la función relacionada [_snprintf](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), que especifica un número máximo de caracteres que se van a escribir en el *búfer*, o use [_scprintf](scprintf-scprintf-l-scwprintf-scwprintf-l.md) para determinar el tamaño de un búfer necesario. Además, asegúrese de que el *formato* no sea una cadena definida por el usuario.

**swprintf** es una versión con caracteres anchos de **sprintf**; los argumentos de puntero a **swprintf** son cadenas de caracteres anchos. La detección de errores de codificación en **swprintf** puede diferir de la de la de **sprintf**. **swprintf** y **fwprintf** se comportan exactamente igual, salvo que **swprintf** escribe la salida en una cadena en lugar de en un destino de tipo **File**, y **swprintf** requiere el parámetro *Count* para especificar el número máximo de caracteres que se van a escribir. Las versiones de estas funciones con el sufijo **_L** son idénticas, salvo que utilizan el parámetro de configuración regional que se pasa en lugar de la configuración regional del subproceso actual.

**swprintf** se ajusta al estándar ISO C, que requiere el segundo parámetro, *Count*, de tipo **size_t**. Para forzar el comportamiento no estándar anterior, defina **_CRT_NON_CONFORMING_SWPRINTFS**. Es posible que el comportamiento anterior se quite en una versión futura, por lo que el código se debe cambiar de forma para que use el nuevo comportamiento estándar.

En C++, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf**|**sprintf**|**sprintf**|**_swprintf**|
|**_stprintf_l**|**_sprintf_l**|**_sprintf_l**|**__swprintf_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**sprintf**, **_sprintf_l**|\<stdio.h>|
|**swprintf**, **_swprintf_l**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_sprintf.c
// compile with: /W3
// This program uses sprintf to format various
// data and place them in the string named buffer.

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf( buffer,     "   String:    %s\n", s ); // C4996
   j += sprintf( buffer + j, "   Character: %c\n", c ); // C4996
   j += sprintf( buffer + j, "   Integer:   %d\n", i ); // C4996
   j += sprintf( buffer + j, "   Real:      %f\n", fp );// C4996
   // Note: sprintf is deprecated; consider using sprintf_s instead

   printf( "Output:\n%s\ncharacter count = %d\n", buffer, j );
}
```

```Output
Output:
   String:    computer
   Character: l
   Integer:   35
   Real:      1.732053

character count = 79
```

## <a name="example"></a>Ejemplo

```C
// crt_swprintf.c
// wide character example
// also demonstrates swprintf returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf fails because string contains WEOF (\xffff)
   printf( "wrote %d characters\n", len );
}
```

```Output
wrote 11 characters
wrote -1 characters
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf (funciones)](../../c-runtime-library/vprintf-functions.md)<br/>
