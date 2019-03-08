---
title: _aligned_offset_realloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_offset_realloc_dbg
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
- aligned_offset_realloc_dbg
- _aligned_offset_realloc_dbg
helpviewer_keywords:
- aligned_offset_realloc_dbg function
- _aligned_offset_realloc_dbg function
ms.assetid: 64e30a12-887e-453b-aea8-aed793fca9d8
ms.openlocfilehash: 7684a752f489eb726b2105b1055b6da1e86e9cd1
ms.sourcegitcommit: beeb77b2976e997debc55b1af35024cc62e62799
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/06/2018
ms.locfileid: "52977828"
---
# <a name="alignedoffsetreallocdbg"></a>_aligned_offset_realloc_dbg

Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](aligned-malloc.md) o [_aligned_offset_malloc](aligned-offset-malloc.md) (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void * _aligned_offset_realloc_dbg(
   void *memblock,
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero de bloque de memoria actual.

*size*<br/>
Tamaño de la asignación de memoria.

*Alineación*<br/>
Valor de la alineación, que debe ser un entero potencia de 2.

*offset*<br/>
Desplazamiento en la asignación de memoria para imponer la alineación.

*filename*<br/>
Puntero al nombre del archivo de código fuente que solicitó el **aligned_offset_realloc** operación o **NULL**.

*linenumber*<br/>
Número de línea en el archivo de código fuente donde el **aligned_offset_realloc** se solicitó la operación o **NULL**.

## <a name="return-value"></a>Valor devuelto

**_aligned_offset_realloc_dbg** devuelve un puntero void al bloque de memoria reasignado (y, probablemente, trasladado). El valor devuelto es **NULL** si el tamaño es cero y el argumento de búfer no es **NULL**, o si no hay suficiente memoria disponible para expandir el bloque al tamaño determinado. En el primer caso, se libera el bloque original. En el segundo, el bloque original permanece inalterado. El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto a void, use una conversión de tipo en el valor devuelto.

## <a name="remarks"></a>Comentarios

**_aligned_offset_realloc_dbg** es una versión de depuración de la [_aligned_offset_realloc](aligned-offset-realloc.md) función. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, cada llamada a **_aligned_offset_realloc_dbg** se reduce a una llamada a **_aligned_offset_realloc**. Ambos **_aligned_offset_realloc** y **_aligned_offset_realloc_dbg** reasignan un bloque de memoria del montón base, pero **_aligned_offset_realloc_dbg** contempla varias características de depuración: búferes situados a cada lado de la parte del usuario del bloque para comprobar si hay pérdidas, y *filename*/*linenumber* información para determinar el origen de solicitudes de asignación. Seguimiento de los tipos de asignación concretos con un parámetro de tipo de bloque no es una característica de depuración compatibles para las asignaciones de alineado. Las asignaciones de alineado aparecerá como un tipo de bloque _NORMAL_BLOCK.

Al igual que [_aligned_offset_malloc](aligned-offset-malloc.md), **_aligned_offset_realloc_dbg** permite una estructura se alinean con un desplazamiento dentro de la estructura.

**_realloc_dbg** reasigna el bloque de memoria especificado con un poco más de espacio solicitado *newSize*. *newSize* podría ser mayor o menor que el tamaño del bloque de memoria asignado originalmente. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. La reasignación podría hacer que el bloque de memoria original se ponga en una ubicación distinta del montón y cambiar el tamaño del bloque de memoria. Si se mueve el bloque de memoria, el contenido del bloque original se sobrescribe.

Esta función establece **errno** a **ENOMEM** si produjo un error en la asignación de memoria o si el tamaño solicitado es mayor que **_HEAP_MAXREQ**. Para obtener más información acerca de **errno**, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Además, **_aligned_offset_realloc_dbg** valida sus parámetros. Si *alineación* no es una potencia de 2 o si *desplazamiento* es mayor o igual a *tamaño* y distinto de cero, esta función invoca al controlador de parámetros no válidos, tal y como se describe en [ Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve **NULL** y establece **errno** a **EINVAL**.

Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_aligned_offset_realloc_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
