---
title: strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l
ms.date: 03/25/2019
api_name:
- _mbstok_l
- _mbstok
- wcstok
- _mbstok
- strtok
- _wcstok_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbstok
- strtok
- _tcstok
- wcstok
helpviewer_keywords:
- mbstok_l function
- strings [C++], searching
- tcstok function
- _tcstok function
- _strtok_l function
- strtok function
- mbstok function
- wcstok_l function
- _mbstok function
- tcstok_l function
- tokens, finding in strings
- _mbstok_l function
- wcstok function
- _wcstok_l function
- _tcstok_l function
- strtok_l function
ms.assetid: 904cb734-f0d7-4d77-ba81-4791ddf461ae
ms.openlocfilehash: 62ed9edc6ec5a7ee60223f1c5e908aa14f421a25
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957655"
---
# <a name="strtok-_strtok_l-wcstok-_wcstok_l-_mbstok-_mbstok_l"></a>strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l

Busca el siguiente token en una cadena, con la configuración regional actual o con la configuración regional especificada que se pase. Hay disponibles versiones más seguras de estas funciones; vea [strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md).

> [!IMPORTANT]
> **_mbstok** y **_mbstok_l** no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
char *strtok(
   char *strToken,
   const char *strDelimit
);
char *strtok_l(
   char *strToken,
   const char *strDelimit,
   _locale_t locale
);
wchar_t *wcstok(
   wchar_t *strToken,
   const wchar_t *strDelimit
);
wchar_t *wcstok_l(
   wchar_t *strToken,
   const wchar_t *strDelimit,
   _locale_t locale
);
unsigned char *_mbstok(
   unsigned char *strToken,
   const unsigned char *strDelimit
);
unsigned char *_mbstok_l(
   unsigned char *strToken,
   const unsigned char *strDelimit,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*strToken*<br/>
Cadena que contiene tokens.

*strDelimit*<br/>
Juego de caracteres delimitadores.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero al siguiente token que se encuentra en *strToken*. Las funciones devuelven **null** cuando no se encuentran más tokens. Cada llamada modifica *strToken* sustituyendo un carácter nulo por el primer delimitador que aparece después del token devuelto.

## <a name="remarks"></a>Comentarios

La función **strtok** busca el siguiente token en *strToken*. El conjunto de caracteres de *strDelimit* especifica los delimitadores posibles del token que se va a encontrar en *strToken* en la llamada actual. **wcstok** y **_mbstok** son versiones de caracteres anchos y multibyte de **strtok**. Los argumentos y el valor devuelto de **wcstok** son cadenas de caracteres anchos; los de **_mbstok** son cadenas de caracteres multibyte. Estas tres funciones se comportan exactamente igual.

> [!IMPORTANT]
> Estas funciones representan una posible amenaza por un problema de saturación del búfer. Los problemas de saturación del búfer son un método frecuente de ataque del sistema, que produce una elevación de privilegios no justificada. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/win32/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer).

En la primera llamada a **strtok**, la función omite los delimitadores iniciales y devuelve un puntero al primer token en *strToken*, terminando el token con un carácter nulo. Una serie de llamadas a **strtok**puede desglosar más tokens del resto de *strToken* . Cada llamada a **strtok** modifica *strToken* insertando un carácter nulo después del **token** devuelto por la llamada. Para leer el siguiente token de *strToken*, llame a **strtok** con un valor **null** para el argumento *strToken* . El argumento *StrToken* **nulo** hace que **strtok** busque el siguiente token en la *strToken*modificada. El argumento *strDelimit* puede tomar cualquier valor de una llamada a la siguiente, por lo que el conjunto de delimitadores puede variar.

El valor de salida se ve afectado por la configuración de la categoría **LC_CTYPE** de la configuración regional. Para obtener más información, vea [setlocale](setlocale-wsetlocale.md).

Las versiones de estas funciones sin el sufijo **_L** usan la configuración regional actual para este comportamiento dependiente de la configuración regional. Las versiones con el sufijo **_L** son idénticas, salvo que usan en su lugar el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

> [!NOTE]
> Cada función usa una variable estática local de subproceso para dividir la cadena en tokens. Por consiguiente, varios subprocesos pueden llamar simultáneamente a estas funciones sin que se produzcan efectos no deseados. Sin embargo, dentro de un único subproceso, la intercalación de llamadas a una de estas funciones generará probablemente daños en los datos y resultados poco precisos. Al analizar diferentes cadenas, termine de analizar una cadena antes de empezar a analizar la siguiente. Además, tenga en cuenta el riesgo que puede existir al llamar a una de estas funciones dentro de un bucle donde se llama a otra función. Si la otra función usa una de estas funciones, se producirá una secuencia intercalada de llamadas y se generarán daños en los datos.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok**|**strtok**|**_mbstok**|**wcstok**|
|**_tcstok**|**_strtok_l**|**_mbstok_l**|**_wcstok_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strtok**|\<string.h>|
|**wcstok**|\<string.h> o \<wchar.h>|
|**_mbstok**, **_mbstok_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_strtok.c
// compile with: /W3
// In this program, a loop uses strtok
// to print all the tokens (separated by commas
// or blanks) in the string named "string".
//
#include <string.h>
#include <stdio.h>

char string[] = "A string\tof ,,tokens\nand some  more tokens";
char seps[]   = " ,\t\n";
char *token;

int main( void )
{
   printf( "Tokens:\n" );

   // Establish string and get the first token:
   token = strtok( string, seps ); // C4996
   // Note: strtok is deprecated; consider using strtok_s instead
   while( token != NULL )
   {
      // While there are tokens in "string"
      printf( " %s\n", token );

      // Get next token:
      token = strtok( NULL, seps ); // C4996
   }
}
```

```Output
Tokens:
A
string
of
tokens
and
some
more
tokens
```

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
