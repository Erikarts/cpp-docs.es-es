---
title: _spawnlpe, _wspawnlpe
ms.date: 11/04/2016
apiname:
- _spawnlpe
- _wspawnlpe
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
- api-ms-win-crt-process-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- spawnlpe
- _wspawnlpe
- _spawnlpe
- wspawnlpe
helpviewer_keywords:
- _wspawnlpe function
- wspawnlpe function
- processes, creating
- spawnlpe function
- _spawnlpe function
- processes, executing new
- process creation
ms.assetid: e171ebfa-70e7-4c44-8331-2a291fc17bd6
ms.openlocfilehash: fa390c039a3d663cb79cb311667e568a6a053131
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62355164"
---
# <a name="spawnlpe-wspawnlpe"></a>_spawnlpe, _wspawnlpe

Crea y ejecuta un nuevo proceso.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
intptr_t _spawnlpe(
   int mode,
   const char *cmdname,
   const char *arg0,
   const char *arg1,
   ... const char *argn,
   NULL,
   const char *const *envp
);
intptr_t _wspawnlpe(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *arg0,
   const wchar_t *arg1,
   ... const wchar_t *argn,
   NULL,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>Parámetros

*mode*<br/>
Modo de ejecución para el proceso de llamada.

*cmdname*<br/>
Ruta de acceso del archivo que se va a ejecutar.

*arg0*, *arg1*,... *argn*<br/>
Lista de punteros a argumentos. El *arg0* argumento normalmente es un puntero a *cmdname*. Los argumentos *arg1* a través de *argn* son punteros a las cadenas de caracteres que forman la nueva lista de argumentos. Siga *argn*, debe haber un **NULL** puntero para marcar el final de la lista de argumentos.

*envp*<br/>
Matriz de punteros a la configuración del entorno.

## <a name="return-value"></a>Valor devuelto

El valor devuelto de un valor sincrónico **_spawnlpe** o **_wspawnlpe** (**_P_WAIT** especificado para *modo*) es el estado de la nueva salida proceso. El valor devuelto de asincrónico **_spawnlpe** o **_wspawnlpe** (**_P_NOWAIT** o **_P_NOWAITO** especificado para  *modo*) es el identificador de proceso. El estado de salida es 0 si el proceso finalizó normalmente. Puede establecer el estado de salida en un valor distinto de cero si el proceso generado usa específicamente un argumento distinto de cero para llamar a la **salir** rutina. Si el nuevo proceso no estableció explícitamente un estado de salida positivo, un estado de salida positivo indica un resultado anormal causado por una anulación o una interrupción. Un valor devuelto de -1 indica un error (no se inicia el proceso de nuevo). En este caso, **errno** se establece en uno de los siguientes valores.

|||
|-|-|
| **E2BIG** | La lista de argumentos supera los 1024 bytes. |
| **EINVAL** | *modo* argumento no es válido. |
| **ENOENT** | El archivo o la ruta de acceso no se encuentra. |
| **ENOEXEC** | El archivo especificado no es ejecutable o no tiene un formato de archivo ejecutable válido. |
| **ENOMEM** | Memoria insuficiente para ejecutar el nuevo proceso. |

Para obtener más información sobre estos y otros códigos de retorno, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

Cada una de estas funciones crea y ejecuta un proceso nuevo, pasa cada argumento de la línea de comandos como parámetro independiente y pasa una matriz de punteros a la configuración del entorno. Estas funciones usan la **ruta** variable de entorno para buscar el archivo para ejecutar.

Estas funciones validan sus parámetros. Si bien *cmdname* o *arg0* es una cadena vacía o se invoca un puntero nulo, el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL**y devuelven -1. No se genera ningún proceso nuevo.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_spawnlpe**|\<process.h>|
|**_wspawnlpe**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [Funciones _spawn y _wspawn](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, _wspawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec (funciones)](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
