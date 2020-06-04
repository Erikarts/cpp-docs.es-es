---
title: _execlp, _wexeclp
ms.date: 11/04/2016
api_name:
- _wexeclp
- _execlp
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
- api-ms-win-crt-process-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wexeclp
- wexeclp
- _execlp
helpviewer_keywords:
- execlp function
- _execlp function
- _wexeclp function
- wexeclp function
ms.assetid: 7b179163-4bcd-4d6a-8baf-68f886791928
ms.openlocfilehash: 6ae1805dd00428aee0acca4bcb3ee221bce1d271
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937183"
---
# <a name="_execlp-_wexeclp"></a>_execlp, _wexeclp

Carga y ejecuta nuevos procesos secundarios.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
intptr_t _execlp(
   const char *cmdname,
   const char *arg0,
   ... const char *argn,
   NULL
);
intptr_t _wexeclp(
   const wchar_t *cmdname,
   const wchar_t *arg0,
   ... const wchar_t *argn,
   NULL
);
```

### <a name="parameters"></a>Parámetros

*cmdname*<br/>
Ruta de acceso del archivo que se va a ejecutar.

*arg0*,... *argn*<br/>
Lista de punteros a parámetros.

## <a name="return-value"></a>Valor devuelto

Si se ejecutan correctamente, estas funciones no vuelven al proceso de llamada. Un valor devuelto de-1 indica un error, en cuyo caso se establece la variable global **errno** .

|valor **errno**|DESCRIPCIÓN|
|-------------------|-----------------|
|**E2BIG**|El espacio necesario para los argumentos y la configuración de entorno supera los 32 kB.|
|**EACCES**|El archivo especificado tiene un bloqueo o una infracción de uso compartido.|
|**EINVAL**|Parámetro no válido.|
|**EMFILE**|Hay demasiados archivos abiertos (se debe abrir el archivo especificado para determinar si es ejecutable).|
|**ENOENT**|No se encuentra el archivo o la ruta de acceso.|
|**ENOEXEC**|El archivo especificado no es ejecutable o tiene un formato de archivo ejecutable no válido.|
|**ENOMEM**|Memoria insuficiente para ejecutar el nuevo proceso; la memoria disponible se ha dañado; o existe un bloque no válido, lo que indica que el proceso de llamada no se asignó correctamente.|

Para obtener más información sobre estos y otros códigos de retorno, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

Cada una de estas funciones carga y ejecuta un proceso nuevo, pasando cada argumento de la línea de comandos como parámetro independiente y usando la variable de entorno **path** para buscar el archivo que se va a ejecutar.

Las funciones **_execlp** validan sus parámetros. Si *cmdname* o *arg0* es un puntero nulo o una cadena vacía, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** en **EINVAL** y devuelven-1. No se inicia ningún proceso nuevo.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|Encabezado opcional|
|--------------|---------------------|---------------------|
|**_execlp**|\<process.h>|\<errno.h>|
|**_wexeclp**|\<process.h> o \<wchar.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [Funciones _exec y _wexec](../../c-runtime-library/exec-wexec-functions.md).

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec (funciones)](../../c-runtime-library/exec-wexec-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
