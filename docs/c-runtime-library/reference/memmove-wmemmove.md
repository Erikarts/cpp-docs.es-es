---
title: memmove, wmemmove
ms.date: 11/04/2016
api_name:
- memmove
- wmemmove
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
- memmove
- wmemmove
helpviewer_keywords:
- wmemmove function
- memmove function
ms.assetid: 3a906114-9cf3-40d7-bd99-ee452004f218
ms.openlocfilehash: bca0badb13dbbc754b6546f62cdd865eacd14fbc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951771"
---
# <a name="memmove-wmemmove"></a>memmove, wmemmove

Mueve un búfer a otro. Hay disponibles versiones más seguras de estas funciones; vea [memmove_s, wmemmove_s](memmove-s-wmemmove-s.md).

## <a name="syntax"></a>Sintaxis

```C
void *memmove(
   void *dest,
   const void *src,
   size_t count
);
wchar_t *wmemmove(
   wchar_t *dest,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Parámetros

*dest*<br/>
Objeto de destino.

*src*<br/>
Objeto de origen.

*count*<br/>
Número de bytes (**memmove**) o caracteres (**wmemmove**) que se van a copiar.

## <a name="return-value"></a>Valor devuelto

El valor de *dest*.

## <a name="remarks"></a>Comentarios

Copia los bytes de *recuento* (**memmove**) o los caracteres (**wmemmove**) de *src* a *dest*. Si algunas regiones del área de origen y del destino se superponen, ambas funciones se aseguran de que se copian los bytes de origen originales en la región superpuesta antes de que se sobrescriban.

**Nota de seguridad** Asegúrese de que el búfer de destino sea del mismo tamaño o mayor que el búfer de origen. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/win32/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer).

Las funciones **memmove** y **wmemmove** solo quedarán desusadas si la constante **_CRT_SECURE_DEPRECATE_MEMORY** se define antes de la instrucción de inclusión para que las funciones queden en desuso, como en el ejemplo siguiente:

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <string.h>
```

o

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**memmove**|\<string.h>|
|**wmemmove**|\<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_memcpy.c
// Illustrate overlapping copy: memmove
// always handles it correctly; memcpy may handle
// it correctly.
//

#include <memory.h>
#include <string.h>
#include <stdio.h>

char str1[7] = "aabbcc";

int main( void )
{
   printf( "The string: %s\n", str1 );
   memcpy( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );

   strcpy_s( str1, sizeof(str1), "aabbcc" );   // reset string

   printf( "The string: %s\n", str1 );
   memmove( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );
}
```

```Output
The string: aabbcc
New string: aaaabb
The string: aabbcc
New string: aaaabb
```

## <a name="see-also"></a>Vea también

[Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
