---
title: _cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l
ms.date: 11/04/2016
apiname:
- _cwscanf_s_l
- _cwscanf_s
- _cscanf_s
- _cscanf_s_l
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
apitype: DLLExport
f1_keywords:
- cscanf_s
- cscanf_s_l
- cwscanf_s
- _cwscanf_s
- _tcscanf_s
- _cscanf_s
- _cwscanf_s_l
- _cscanf_s_l
- cwscanf_s_l
- _tcscanf_s_l
- tcscanf_s
- tcscanf_s_l
helpviewer_keywords:
- cscanf_s function
- _cwscanf_s_l function
- tcscanf_s function
- console [C++], reading from
- _cscanf_s function
- data [C++], reading from the console
- cwscanf_s function
- _tcscanf_s_l function
- _cscanf_s_l function
- cscanf_s_l function
- cwscanf_s_l function
- reading data [C++], from the console
- _cwscanf_s function
- _tcscanf_s function
- tcscanf_s_l function
ms.assetid: 9ccab74d-916f-42a6-93d8-920525efdf4b
ms.openlocfilehash: b49c464c7262a60bb7744a68c0144234e152edd3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62288919"
---
# <a name="cscanfs-cscanfsl-cwscanfs-cwscanfsl"></a>_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l

Lee datos con formato de la consola. Estas versiones más seguras de [_cscanf, _cscanf_l, _cwscanf, _cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md) incluyen mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _cscanf_s(
   const char *format [,
   argument] ...
);
int _cscanf_s_l(
   const char *format,
   locale_t locale [,
   argument] ...
);
int _cwscanf_s(
   const wchar_t *format [,
   argument] ...
);
int _cwscanf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>Parámetros

*format*<br/>
Cadena de control de formato.

*argument*<br/>
Parámetros opcionales.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Número de campos que se convirtieron y asignaron correctamente. El valor devuelto no incluye los campos que se leyeron pero no se asignaron. El valor devuelto es **EOF** para un intento de leer al final del archivo. Esto puede tener lugar cuando la entrada de teclado se redirige en el nivel de la línea de comandos del sistema operativo. Un valor devuelto de 0 indica que no se ha asignado ningún campo.

Estas funciones validan sus parámetros. Si *formato* es un puntero nulo, estas funciones invocan el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **EOF** y **errno** está establecido en **EINVAL**.

## <a name="remarks"></a>Comentarios

El **_cscanf_s** función lee los datos directamente desde la consola en las ubicaciones especificadas por *argumento*. La función [_getche](getch-getwch.md) se usa para leer caracteres. Cada parámetro opcional debe ser un puntero a una variable con un tipo que se corresponde con un especificador de tipo en *formato*. El formato controla la interpretación de la entrada campos y tiene la misma forma y función que el *formato* parámetro para el [scanf_s](scanf-scanf-l-wscanf-wscanf-l.md) función. Mientras **_cscanf_s** suele repetir el carácter de entrada, no lo hace si fue la última llamada **_ungetch**.

Como otras versiones seguras de funciones en el **scanf** familia, **_cscanf_s** y **_cswscanf_s** requieren argumentos de tamaño para los caracteres de campo de tipo **c** , **C**, **s**, **S**, y **[**. Para obtener más información, consulte [scanf (Especificación de ancho)](../../c-runtime-library/scanf-width-specification.md).

> [!NOTE]
> El parámetro de tamaño es de tipo **sin signo**, no **size_t**.

Las versiones de estas funciones con el **_l** sufijo son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcscanf_s**|**_cscanf_s**|**_cscanf_s**|**_cwscanf_s**|
|**_tcscanf_s_l**|**_cscanf_s_l**|**_cscanf_s_l**|**_cwscanf_s_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_cscanf_s**, **_cscanf_s_l**|\<conio.h>|
|**_cwscanf_s**, **_cwscanf_s_l**|\<conio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_cscanf_s.c
// compile with: /c
/* This program prompts for a string
* and uses _cscanf_s to read in the response.
* Then _cscanf_s returns the number of items
* matched, and the program displays that number.
*/

#include <stdio.h>
#include <conio.h>

int main( void )
{
   int result, n[3];
   int i;

   result = _cscanf_s( "%i %i %i", &n[0], &n[1], &n[2] );
   _cprintf_s( "\r\nYou entered " );
   for( i=0; i<result; i++ )
      _cprintf_s( "%i ", n[i] );
   _cprintf_s( "\r\n" );
}
```

```Input
1 2 3
```

```Output
You entered 1 2 3
```

## <a name="see-also"></a>Vea también

[E/S de consola y de puerto](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
