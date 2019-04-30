---
title: _aligned_offset_realloc
ms.date: 11/04/2016
apiname:
- _aligned_offset_realloc
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- aligned_offset_realloc
- _aligned_offset_realloc
helpviewer_keywords:
- aligned_offset_realloc function
- _aligned_offset_realloc function
ms.assetid: e0263533-991e-41b0-acc9-1b8a51ab9ecd
ms.openlocfilehash: d5f87f9bdfff262826b8d4cc4da86069588cf9db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341462"
---
# <a name="alignedoffsetrealloc"></a>_aligned_offset_realloc

Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](aligned-malloc.md) o [_aligned_offset_malloc](aligned-offset-malloc.md).

## <a name="syntax"></a>Sintaxis

```C
void * _aligned_offset_realloc(
   void *memblock,
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero de bloque de memoria actual.

*size*<br/>
Tamaño de la asignación de memoria.

*alignment*<br/>
Valor de la alineación, que debe ser un entero potencia de 2.

*offset*<br/>
Desplazamiento en la asignación de memoria para imponer la alineación.

## <a name="return-value"></a>Valor devuelto

**_aligned_offset_realloc** devuelve un puntero void al bloque de memoria reasignado (y, probablemente, trasladado). El valor devuelto es **NULL** si el tamaño es cero y el argumento de búfer no es **NULL**, o si no hay suficiente memoria disponible para expandir el bloque al tamaño determinado. En el primer caso, se libera el bloque original. En el segundo, el bloque original permanece inalterado. El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto a void, use una conversión de tipo en el valor devuelto.

**_aligned_offset_realloc** está marcado como `__declspec(noalias)` y `__declspec(restrict)`, lo que significa que se garantiza que la función no se puede modificar las variables globales y que el puntero devuelto no es un alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).

## <a name="remarks"></a>Comentarios

Al igual que [_aligned_offset_malloc](aligned-offset-malloc.md), **_aligned_offset_realloc** permite una estructura se alinean con un desplazamiento dentro de la estructura.

**_aligned_offset_realloc** se basa en **malloc**. Para obtener más información sobre el uso de **_aligned_offset_malloc**, consulte [malloc](malloc.md). Si *memblock* es **NULL**, las llamadas de función **_aligned_offset_malloc** internamente.

Esta función establece **errno** a **ENOMEM** si produjo un error en la asignación de memoria o si el tamaño solicitado es mayor que **_HEAP_MAXREQ**. Para obtener más información acerca de **errno**, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Además, **_aligned_offset_realloc** valida sus parámetros. Si *alineación* no es una potencia de 2 o si *desplazamiento* es mayor o igual a *tamaño* y distinto de cero, esta función invoca al controlador de parámetros no válidos, tal y como se describe en [ Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve **NULL** y establece **errno** a **EINVAL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_aligned_offset_realloc**|\<malloc.h>|

## <a name="example"></a>Ejemplo

Para obtener más información, consulte [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Vea también

[Alineación de datos](../../c-runtime-library/data-alignment.md)<br/>
