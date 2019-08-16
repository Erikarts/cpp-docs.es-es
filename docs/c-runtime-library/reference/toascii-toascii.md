---
title: toascii, __toascii
ms.date: 11/04/2016
apiname:
- __toascii
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __toascii
- toascii
- ctype/toascii
- ctype/__toascii
helpviewer_keywords:
- toascii function
- string conversion, to ASCII characters
- __toascii function
- ASCII characters, converting to
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
ms.openlocfilehash: 22f76bdbdb21eb5b3cc9a226c111e321ee2fd0ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155529"
---
# <a name="toascii-toascii"></a>toascii, __toascii

Convierte caracteres en ASCII de 7 bits por truncamiento.

## <a name="syntax"></a>Sintaxis

```C
int __toascii(
   int c
);
#define toascii __toascii
```

### <a name="parameters"></a>Parámetros

*c*<br/>
Carácter que se va a convertir.

## <a name="return-value"></a>Valor devuelto

**__toascii** convierte el valor de *c* a la ASCII de 7 bits de intervalo y devuelve el resultado. No se reserva ningún valor devuelto para indicar un error.

## <a name="remarks"></a>Comentarios

El **__toascii** rutina convierte el carácter especificado en un carácter ASCII al truncarlo a los 7 bits de orden inferior. No se aplica ninguna otra transformación.

El **__toascii** rutina se define como una macro, a menos que la macro de preprocesador _ctype_disable_macros. Por compatibilidad con versiones anteriores, **toascii** se define como una macro solo cuando [ &#95; &#95;STDC&#95; &#95; ](../../preprocessor/predefined-macros.md) no está definido o se define como 0; en caso contrario, está sin definir.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**toascii**, **__toascii**|C: \<ctype.h><br /><br /> C++: \<cctype> o \<ctype.h>|

El **toascii** macro es una extensión POSIX y **__toascii** es una implementación específica de Microsoft de la extensión POSIX. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[is, isw (rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
[to (funciones)](../../c-runtime-library/to-functions.md)<br/>
