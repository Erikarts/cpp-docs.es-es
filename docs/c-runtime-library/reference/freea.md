---
title: _freea
ms.date: 11/04/2016
apiname:
- _freea
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
- freea
- _freea
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
ms.openlocfilehash: ac9c5528755898b0de131bccf94185b501b0e720
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333073"
---
# <a name="freea"></a>_freea

Desasigna o libera un bloque de memoria.

## <a name="syntax"></a>Sintaxis

```C
void _freea(
   void *memblock
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Bloque de memoria anteriormente asignada que se va a liberar.

## <a name="return-value"></a>Valor devuelto

Ninguno.

## <a name="remarks"></a>Comentarios

El **_freea** función desasigna un bloque de memoria (*memblock*) que se había asignado previamente mediante una llamada a [_malloca](malloca.md). **_freea** comprueba si se ha asignado la memoria en el montón o en la pila. Si se ha asignado en la pila, **_freea** no hace nada. Si se ha asignado en el montón, el número de bytes liberados es equivalente al número de bytes solicitado al asignar el bloque. Si *memblock* es **NULL**, se omite el puntero y **_freea** devuelve inmediatamente. Intento de liberación de un puntero no válido (un puntero a un bloque de memoria que no se ha asignado con **_malloca**) podría afectar a las solicitudes de asignación posteriores y provoque errores.

**_freea** llamadas **libre** internamente si encuentra que la memoria se asigna en el montón. Si la memoria está en el montón o en la pila lo determina un marcador que se coloca en la memoria en la dirección inmediatamente anterior a la memoria asignada.

Si se produce un error en que se libere la memoria, **errno** se establece con la información del sistema operativo de la naturaleza del error. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Una vez liberado un bloque de memoria, [_heapmin](heapmin.md) minimiza la cantidad de memoria libre en el montón al fusionar las regiones no usadas y liberarlas de nuevo en el sistema operativo. La memoria liberada que no se ha liberado en el sistema operativo se restaura en el grupo libre y vuelve a estar disponible para su asignación.

Una llamada a **_freea** debe acompañar a todas las llamadas a **_malloca**. También es un error llamar a **_freea** dos veces en la misma memoria. Cuando la aplicación se vincula con una versión de depuración de las bibliotecas de tiempo de ejecución de C, especialmente con [_malloc_dbg](malloc-dbg.md) características habilitadas mediante la definición de **_CRTDBG_MAP_ALLOC**, resulta más fácil de encontrar que faltan o duplicar las llamadas a **_freea**. Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

**_freea** está marcado como `__declspec(noalias)`, lo que significa que se garantiza que la función no se puede modificar las variables globales. Para obtener más información, consulte [noalias](../../cpp/noalias.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_freea**|\<stdlib.h> y \<malloc.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [_malloca](malloca.md).

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[_malloca](malloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
