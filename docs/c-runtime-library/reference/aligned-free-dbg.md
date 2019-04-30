---
title: _aligned_free_dbg
ms.date: 11/04/2016
apiname:
- _aligned_free_dbg
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
- _aligned_free_dbg
- aligned_free_dbg
helpviewer_keywords:
- _aligned_free_dbg function
- aligned_free_dbg function
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
ms.openlocfilehash: f51b9b9573ab2e23a0a60979c55a33d2e5cff747
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341904"
---
# <a name="alignedfreedbg"></a>_aligned_free_dbg

Libera un bloque de memoria que se ha asignado con [_aligned_malloc](aligned-malloc.md) o [_aligned_offset_malloc](aligned-offset-malloc.md) (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void _aligned_free_dbg(
   void *memblock
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Un puntero al bloque de memoria que se devuelve a la [_aligned_malloc](aligned-malloc.md) o [_aligned_offset_malloc](aligned-offset-malloc.md) función.

## <a name="remarks"></a>Comentarios

El **_aligned_free_dbg** función es una versión de depuración de la [_aligned_free](aligned-free.md) función. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, cada llamada a **_aligned_free_dbg** se reduce a una llamada a `_aligned_free`. Ambos `_aligned_free` y **_aligned_free_dbg** liberan un bloque de memoria del montón base, pero **_aligned_free_dbg** admite una característica de depuración: bloquea la posibilidad de mantener liberados en la lista vinculada del montón para simular condiciones de memoria insuficiente.

**_aligned_free_dbg** realiza una comprobación de validez en todos los archivos especificados y las ubicaciones de bloques antes de realizar la operación de liberación. No se espera que la aplicación proporcione esta información. Cuando se libera un bloque de memoria, el administrador del montón de depuración comprueba automáticamente la integridad de los búferes situados a cada lado de la parte del usuario y emite un informe de error en caso de sobrescritura. Si el campo de tipo bit el _CRTDBG_DELAY_FREE_MEM_DF el [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) marca está establecida, el bloque liberado se rellena con el valor 0xDD, asigna el tipo de bloque _FREE_BLOCK y mantiene en la lista vinculada del montón de bloques de memoria.

Si se produce un error al liberar memoria, en `errno` se muestra información sobre la naturaleza del error proporcionada por el sistema operativo. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_aligned_free_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)