---
title: realloc
ms.date: 11/04/2016
apiname:
- realloc
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
- _brealloc
- _nrealloc
- realloc
- _frealloc
helpviewer_keywords:
- _brealloc function
- realloc function
- nrealloc function
- frealloc function
- _nrealloc function
- memory blocks, reallocating
- memory, reallocating
- _frealloc function
- reallocate memory blocks
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
ms.openlocfilehash: 0d61746365a8ded8d68072b1f398a18ba6ce7605
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357673"
---
# <a name="realloc"></a>realloc

Reasigna bloques de memoria.

## <a name="syntax"></a>Sintaxis

```C
void *realloc(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero al bloque de memoria asignado previamente.

*size*<br/>
Nuevo tamaño en bytes.

## <a name="return-value"></a>Valor devuelto

**realloc** devuelve un **void** puntero al bloque de memoria reasignado (y, probablemente, trasladado).

Si no hay suficiente memoria disponible para expandir el bloque al tamaño determinado, el bloque original permanece inalterado y **NULL** se devuelve.

Si *tamaño* es cero, el bloque señalado por *memblock* se libera; el valor devuelto es **NULL**, y *memblock* sigue apuntando a un bloque liberado.

El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto **void**, use un conversión de tipo en el valor devuelto.

## <a name="remarks"></a>Comentarios

El **realloc** función cambia el tamaño de un bloque de memoria asignado. El *memblock* argumento apunta al principio del bloque de memoria. Si *memblock* es **NULL**, **realloc** se comporta del mismo modo que **malloc** y asigna un nuevo bloque de *tamaño*bytes. Si *memblock* no **NULL**, debe ser un puntero devuelto por una llamada anterior a **calloc**, **malloc**, o **realloc** .

El *tamaño* argumento proporciona el nuevo tamaño del bloque, en bytes. El contenido del bloque es igual hasta el más pequeño de los tamaños nuevo y antiguo, aunque el bloque nuevo puede estar en otra ubicación. Dado que el bloque nuevo puede estar en una nueva ubicación de memoria, el puntero devuelto por **realloc** no se garantiza que el puntero que se pasa a través de la *memblock* argumento. **realloc** cero no recién asignados a la memoria en el caso de un crecimiento del búfer.

**realloc** establece **errno** a **ENOMEM** si se produce un error en la asignación de memoria o si la cantidad de memoria solicitada supera **_HEAP_MAXREQ**. Para obtener información sobre este y otros códigos de error, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**realloc** llamadas **malloc** para poder usar el C++ [_set_new_mode](set-new-mode.md) función para establecer el modo de controlador nuevo. El nuevo modo de controlador indica si, en caso de error, **malloc** consiste en llamar a la rutina del nuevo controlador según lo establecido por [_set_new_handler](set-new-handler.md). De forma predeterminada, **malloc** no llama a la rutina del nuevo controlador en caso de error para asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando **realloc** no puede asignar memoria, **malloc** llame a la rutina del nuevo controlador de la misma forma en que el **nuevo** operador Cuando se produce un error por la misma razón. Para invalidar el valor predeterminado, llame a

```C
_set_new_mode(1);
```

temprano en un programa o vincúlelo con NEWMODE.OBJ (vea [Opciones de vínculo](../../c-runtime-library/link-options.md)).

Cuando la aplicación se vincula con una versión de depuración de las bibliotecas de tiempo de ejecución de C, **realloc** se resuelve como [_realloc_dbg](realloc-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

**realloc** está marcado como `__declspec(noalias)` y `__declspec(restrict)`, lo que significa que se garantiza que la función no se puede modificar las variables globales y que el puntero devuelto no es un alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**realloc**|\<stdlib.h> y \<malloc.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_realloc.c
// This program allocates a block of memory for
// buffer and then uses _msize to display the size of that
// block. Next, it uses realloc to expand the amount of
// memory used by buffer and then calls _msize again to
// display the new amount of memory allocated to buffer.

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   long *buffer, *oldbuffer;
   size_t size;

   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )
      exit( 1 );

   size = _msize( buffer );
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );

   // Reallocate and show new size:
   oldbuffer = buffer;     // save pointer in case realloc fails
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))
        ==  NULL )
   {
      free( oldbuffer );  // free original block
      exit( 1 );
   }
   size = _msize( buffer );
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",
            size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after malloc of 1000 longs: 4000
Size of block after realloc of 1000 more longs: 8000
```

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
