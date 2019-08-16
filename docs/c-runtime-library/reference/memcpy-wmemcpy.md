---
title: memcpy, wmemcpy
ms.date: 11/04/2016
apiname:
- memcpy
- wmemcpy
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- wmemcpy
- memcpy
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
ms.openlocfilehash: f687e231060c287e206017dc61fe1d5193d8f0de
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499638"
---
# <a name="memcpy-wmemcpy"></a>memcpy, wmemcpy

Copia bytes entre búferes. Hay disponibles versiones más seguras de estas funciones; vea [memcpy_s, wmemcpy_s](memcpy-s-wmemcpy-s.md).

## <a name="syntax"></a>Sintaxis

```C
void *memcpy(
   void *dest,
   const void *src,
   size_t count
);
wchar_t *wmemcpy(
   wchar_t *dest,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Parámetros

*dest*<br/>
Nuevo búfer.

*src*<br/>
Búfer del que copiar.

*count*<br/>
Número de caracteres que se copiará.

## <a name="return-value"></a>Valor devuelto

El valor de *dest*.

## <a name="remarks"></a>Comentarios

**memcpy** copia el *número* de bytes de *src* a *dest*; **wmemcpy** copia el *número* de caracteres anchos (dos bytes). Si el origen y el destino se superponen, el comportamiento de **memcpy** es indefinido. Use **memmove** para administrar regiones superpuestas.

> [!IMPORTANT]
> Asegúrese de que el búfer de destino sea del mismo tamaño o mayor que el búfer de origen. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/win32/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer).

> [!IMPORTANT]
> Dado que se ha realizado un seguimiento de las saturaciones del búfer y, por lo tanto, de posibles vulnerabilidades de seguridad, al uso inadecuado de **memcpy**, el ciclo de vida de desarrollo de seguridad (SDL) incluye esta función entre las funciones "prohibidas".  Puede observar que algunas clases de biblioteca de VC + + siguen usando **memcpy**.  Además, puede observar que el optimizador del compilador de VC + + a veces emite llamadas a **memcpy**.  El producto Visual C++ se desarrolla de acuerdo con el proceso SDL, por lo que se ha evaluado con cuidado el uso de esta función prohibida.  En el caso de su uso por parte de bibliotecas, se han examinado meticulosamente las llamadas para garantizar que no provoquen saturaciones de búferes.  En el caso del compilador, a veces determinados patrones de código se reconocen como idénticos al patrón de **memcpy**y, por tanto, se reemplazan por una llamada a la función.  En tales casos, el uso de **memcpy** no es más seguro de lo que serían las instrucciones originales; simplemente se han optimizado para una llamada a la función **memcpy** optimizada para el rendimiento.  Al igual que el uso de funciones de CRT "seguras" no garantiza la seguridad (solo dificulta la falta de seguridad), el uso de funciones "prohibidas" no garantiza el peligro (solo se requiere un mayor escrutinio para garantizar la seguridad).
>
> Dado que el uso de **memcpy** por parte del compilador y las bibliotecas de VC + + se ha analizado cuidadosamente, se permiten estas llamadas dentro del código que, de otro modo, es compatible con SDL.  las llamadas a **memcpy** introducidas en el código fuente de la aplicación solo son conformes a SDL cuando el uso ha sido revisado por expertos en seguridad.

Las funciones **memcpy** y **wmemcpy** solo quedarán desusadas si la constante **_CRT_SECURE_DEPRECATE_MEMORY** se define antes de la instrucción de inclusión para que las funciones queden en desuso, como en el ejemplo siguiente:

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <memory.h>
```

o

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**memcpy**|\<memory.h> o \<string.h>|
|**wmemcpy**|\<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea [memmove](memmove-wmemmove.md) para obtener un ejemplo de cómo usar **memcpy**.

## <a name="see-also"></a>Vea también

[Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove, wmemmove](memmove-wmemmove.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
