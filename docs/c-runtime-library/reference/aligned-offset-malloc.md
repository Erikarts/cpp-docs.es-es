---
title: _aligned_offset_malloc
ms.date: 11/04/2016
api_name:
- _aligned_offset_malloc
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _aligned_offset_malloc
- aligned_offset_malloc
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
ms.openlocfilehash: 3e8d6f839f3c675b7543ff14f3f633b0c7d5151f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943855"
---
# <a name="_aligned_offset_malloc"></a>_aligned_offset_malloc

Asigna memoria en un límite de alineación especificado.

## <a name="syntax"></a>Sintaxis

```C
void * _aligned_offset_malloc(
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Tamaño de la asignación de memoria solicitada.

*alignment*<br/>
Valor de la alineación, que debe ser un entero potencia de 2.

*offset*<br/>
Desplazamiento en la asignación de memoria para imponer la alineación.

## <a name="return-value"></a>Valor devuelto

Puntero al bloque de memoria que se asignó o **null** si se produjo un error en la operación.

## <a name="remarks"></a>Comentarios

**_aligned_offset_malloc** es útil en situaciones en las que se necesita la alineación en un elemento anidado; por ejemplo, si se necesita la alineación en una clase anidada.

**_aligned_offset_malloc** se basa en **malloc**; para obtener más información, consulte [malloc](malloc.md).

**_aligned_offset_malloc** está marcado `__declspec(noalias)` como `__declspec(restrict)`y, lo que significa que se garantiza que la función no modifica las variables globales y que el puntero devuelto no tiene alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).

Esta función establece **errno** en **ENOMEM** si se produce un error en la asignación de memoria o si el tamaño solicitado es mayor que **_HEAP_MAXREQ**. Para obtener más información acerca de **errno**, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Además, **_aligned_offset_malloc** valida sus parámetros. Si la *alineación* no es una potencia de 2 o si el *desplazamiento* es mayor o igual que *el tamaño* y distinto de cero, esta función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve **null** y establece **errno** en **EINVAL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_aligned_offset_malloc**|\<malloc.h>|

## <a name="example"></a>Ejemplo

Para obtener más información, consulte [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Vea también

[Alineación de datos](../../c-runtime-library/data-alignment.md)<br/>
