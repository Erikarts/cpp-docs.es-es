---
title: strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l
ms.date: 11/04/2016
apiname:
- _mbspbrk
- wcspbrk
- _mbspbrk_l
- strpbrk
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _fstrpbrk
- _mbspbrk
- strpbrk
- _tcspbrk
- _ftcspbrk
- wcspbrk
helpviewer_keywords:
- fstrpbrk function
- _ftcspbrk function
- _mbspbrk_l function
- strpbrk function
- _fstrpbrk function
- mbspbrk function
- characters [C++], scanning strings
- _tcspbrk function
- wcspbrk function
- ftcspbrk function
- character sets [C++], scanning strings for characters
- strings [C++], scanning
- tcspbrk function
- _mbspbrk function
- mbspbrk_l function
ms.assetid: 80b504f7-a167-4dde-97ad-4ae3000dc810
ms.openlocfilehash: 059b0659a8088783c6d169288de486b41a6e8d82
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209572"
---
# <a name="strpbrk-wcspbrk-mbspbrk-mbspbrkl"></a>strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l

Examina cadenas para buscar caracteres de juegos de caracteres especificados.

> [!IMPORTANT]
> `_mbspbrk` y `_mbspbrk_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
char *strpbrk(
   const char *str,
   const char *strCharSet
); // C only
char *strpbrk(
   char *str,
   const char *strCharSet
); // C++ only
const char *strpbrk(
   const char *str,
   const char *strCharSet
); // C++ only
wchar_t *wcspbrk(
   const wchar_t *str,
   const wchar_t *strCharSet
); // C only
wchar_t *wcspbrk(
   wchar_t *str,
   const wchar_t *strCharSet
); // C++ only
const wchar_t *wcspbrk(
   const wchar_t *str,
   const wchar_t *strCharSet
); // C++ only
unsigned char *_mbspbrk(
   const unsigned char *str,
   const unsigned char *strCharSet
); // C only
unsigned char *_mbspbrk(
   unsigned char *str,
   const unsigned char *strCharSet
); // C++ only
const unsigned char *_mbspbrk(
   const unsigned char *str,
   const unsigned char *strCharSet
); // C++ only
unsigned char *_mbspbrk_l(
   const unsigned char *str,
   const unsigned char *strCharSet,
   _locale_t locale
); // C only
unsigned char *_mbspbrk_l(
   unsigned char *str,
   const unsigned char *strCharSet,
   _locale_t locale
); // C++ only
const unsigned char *_mbspbrk_l(
   const unsigned char *str,
   const unsigned char* strCharSet,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parámetros

*str*<br/>
Cadena terminada en NULL en la que se ha buscado.

*strCharSet*<br/>
Juego de caracteres terminado en NULL.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la primera aparición de cualquier carácter de *strCharSet* en *str*, o un puntero NULL si los dos argumentos de cadena no tienen ningún carácter en común.

## <a name="remarks"></a>Comentarios

El `strpbrk` función devuelve un puntero a la primera aparición de un carácter en *str* que pertenece al conjunto de caracteres de *strCharSet*. En la búsqueda no se incluye el carácter nulo de finalización.

`wcspbrk` y `_mbspbrk` son versiones de caracteres anchos y multibyte de `strpbrk`. Los argumentos y el valor devuelto de `wcspbrk` son cadenas de caracteres anchos; los de `_mbspbrk` son cadenas de caracteres multibyte.

`_mbspbrk` valida sus parámetros. Si *str* o *strCharSet* es NULL, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `_mbspbrk` devuelve NULL y establece `errno` a EINVAL. `strpbrk` y `wcspbrk` no validan sus parámetros. Estas tres funciones se comportan exactamente igual.

`_mbspbrk` es similar a `_mbscspn`, salvo que `_mbspbrk` devuelve un puntero en lugar de un valor de tipo [size_t](../../c-runtime-library/standard-types.md).

En C, estas funciones toman una **const** puntero para el primer argumento. En C++, hay disponibles dos sobrecargas. La sobrecarga que toma un puntero a **const** devuelve un puntero a **const**; la versión que toma un puntero a que no sean de**const** devuelve un puntero a que no sean de**const** . Se define la macro _CRT_CONST_CORRECT_OVERLOADS si tanto el **const** y no-**const** versiones de estas funciones están disponibles. Si necesita que no sea**const** comportamiento para ambos C++ sobrecargas, defina el símbolo _CONST_RETURN.

El valor de salida se ve afectado por la configuración de la configuración de la categoría LC_CTYPE de la configuración regional. Para obtener más información, consulte [setlocale](setlocale-wsetlocale.md). Las versiones de estas funciones sin el **_l** sufijo usan la configuración regional actual de este comportamiento dependiente de la configuración regional; la versión con el **_l** sufijo es idéntico, salvo que usa el parámetro de configuración regional pasado en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcspbrk`|`strpbrk`|`_mbspbrk`|`wcspbrk`|
|**N/D**|**N/D**|`_mbspbrk_l`|**N/D**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`strpbrk`|\<string.h>|
|`wcspbrk`|\<string.h> o \<wchar.h>|
|`_mbspbrk`, `_mbspbrk_l`|\<mbstring.h>|

Para obtener más información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_strpbrk.c

#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[100] = "The 3 men and 2 boys ate 5 pigs\n";
   char *result = NULL;

   // Return pointer to first digit in "string".
   printf( "1: %s\n", string );
   result = strpbrk( string, "0123456789" );
   printf( "2: %s\n", result++ );
   result = strpbrk( result, "0123456789" );
   printf( "3: %s\n", result++ );
   result = strpbrk( result, "0123456789" );
   printf( "4: %s\n", result );
}
```

```Output
1: The 3 men and 2 boys ate 5 pigs

2: 3 men and 2 boys ate 5 pigs

3: 2 boys ate 5 pigs

4: 5 pigs
```

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strchr, wcschr, _mbschr, _mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
