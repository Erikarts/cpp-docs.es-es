---
title: _aligned_offset_recalloc
ms.date: 11/04/2016
apiname:
- _aligned_offset_recalloc
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
- aligned_offset_recalloc
- _aligned_offset_recalloc
helpviewer_keywords:
- aligned_offset_recalloc function
- _aligned_offset_recalloc function
ms.assetid: a258f54e-eeb4-4853-96fc-007d710f98e9
ms.openlocfilehash: 5ee163d257665b5481d6ab1ead54698ace1ef210
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335664"
---
# <a name="alignedoffsetrecalloc"></a>_aligned_offset_recalloc

Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](aligned-malloc.md) o [_aligned_offset_malloc](aligned-offset-malloc.md) e inicializa la memoria a 0.

## <a name="syntax"></a>Sintaxis

```C
void * _aligned_offset_recalloc(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero de bloque de memoria actual.

*number*<br/>
Número de elementos.

*size*<br/>
Longitud en bytes de cada elemento.

*alignment*<br/>
Valor de la alineación, que debe ser un entero potencia de 2.

*offset*<br/>
Desplazamiento en la asignación de memoria para imponer la alineación.

## <a name="return-value"></a>Valor devuelto

**_aligned_offset_recalloc** devuelve un puntero void al bloque de memoria reasignado (y, probablemente, trasladado). El valor devuelto es **NULL** si el tamaño es cero y el argumento de búfer no es **NULL**, o si no hay suficiente memoria disponible para expandir el bloque al tamaño determinado. En el primer caso, se libera el bloque original. En el segundo, el bloque original permanece inalterado. El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto a void, use una conversión de tipo en el valor devuelto.

**_aligned_offset_recalloc** está marcado como `__declspec(noalias)` y `__declspec(restrict)`, lo que significa que se garantiza que la función no se puede modificar las variables globales y que el puntero devuelto no es un alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).

## <a name="remarks"></a>Comentarios

Al igual que [_aligned_offset_malloc](aligned-offset-malloc.md), **_aligned_offset_recalloc** permite una estructura se alinean con un desplazamiento dentro de la estructura.

**_aligned_offset_recalloc** se basa en **malloc**. Para obtener más información sobre el uso de **_aligned_offset_malloc**, consulte [malloc](malloc.md). Si *memblock* es **NULL**, las llamadas de función **_aligned_offset_malloc** internamente.

Esta función establece **errno** a **ENOMEM** si produjo un error en la asignación de memoria o si el tamaño solicitado (*número* * *tamaño* ) era mayor que **_HEAP_MAXREQ**. Para obtener más información acerca de **errno**, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Además, **_aligned_offset_recalloc** valida sus parámetros. Si *alineación* no es una potencia de 2 o si *desplazamiento* es mayor o igual al tamaño solicitado y distinto de cero, esta función invoca al controlador de parámetros no válidos, como se describe en [parámetro Validación](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve **NULL** y establece **errno** a **EINVAL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_aligned_offset_recalloc**|\<malloc.h>|

## <a name="see-also"></a>Vea también

[Alineación de datos](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
