---
title: _CrtDoForAllClientObjects
ms.date: 11/04/2016
apiname:
- _CrtDoForAllClientObjects
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
- _CrtDoForAllClientObjects
- CrtDoForAllClientObjects
- crtdbg/_CrdDoForAllClientObjects
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
ms.openlocfilehash: 86268bd9ac49c8ea27f715404236bcb9291f5d8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339724"
---
# <a name="crtdoforallclientobjects"></a>_CrtDoForAllClientObjects

Llama a una función proporcionada por la aplicación para todos los **_CLIENT_BLOCK** tipos del montón (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void _CrtDoForAllClientObjects(
   void ( * pfn )( void *, void * ),
   void *context
);
```

### <a name="parameters"></a>Parámetros

*pfn*<br/>
Puntero a la función de devolución de llamada proporcionada por la aplicación. El primer parámetro de esta función señala a los datos. El segundo parámetro es el puntero de contexto que se pasa a la llamada a **_CrtDoForAllClientObjects**.

*context*<br/>
Puntero al contexto proporcionado por la aplicación que se va a pasar a la función proporcionada por la aplicación.

## <a name="remarks"></a>Comentarios

El **_CrtDoForAllClientObjects** función busca en lista vinculada del montón bloques de memoria con el **_CLIENT_BLOCK** tipo y llama a la función proporcionada por la aplicación cuando un bloque de este tipo se encuentra. El bloque encontrado y el *contexto* parámetros se pasan como argumentos a la función proporcionada por la aplicación. Durante la depuración, una aplicación puede realizar un seguimiento de un grupo específico de asignaciones llamar explícitamente a la depuración funciones del montón para asignar memoria y especificando que se asigne a los bloques de la **_CLIENT_BLOCK** tipo de bloque. A continuación, se puede realizar el seguimiento y la notificación de estos bloques por separado durante la detección de pérdidas y la creación de informes sobre el estado de la memoria.

Si el **_CRTDBG_ALLOC_MEM_DF** campo de bits de la [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) marca no está activada, **_CrtDoForAllClientObjects** devuelve inmediatamente. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, las llamadas a **_CrtDoForAllClientObjects** se quitan durante el preprocesamiento.

Para obtener más información sobre la **_CLIENT_BLOCK** escribir y ver cómo puede usar otras funciones de depuración, [tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

Si *pfn* es **NULL**, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) está establecido en **EINVAL** y devuelve la función.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtDoForAllClientObjects**|\<crtdbg.h>, \<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

**Bibliotecas:** Versiones de depuración de universales bibliotecas de tiempo de ejecución de C solo.

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
[Funciones que indican el estado del montón](/visualstudio/debugger/crt-debug-heap-details)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
