---
title: _chdrive
ms.date: 11/04/2016
apiname:
- _chdrive
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- chdrive
- _chdrive
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
ms.openlocfilehash: 7e36867bb8237c549fd250be88a99244766920ba
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500286"
---
# <a name="_chdrive"></a>_chdrive

Cambia la unidad de trabajo actual.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _chdrive(
   int drive
);
```

### <a name="parameters"></a>Parámetros

*drive*<br/>
Entero de 1 a 26 que especifica la unidad de trabajo actual (1=A, 2=B, etc.).

## <a name="return-value"></a>Valor devuelto

Cero (0) si la unidad de trabajo actual se ha cambiado correctamente; de lo contrario, -1.

## <a name="remarks"></a>Comentarios

Si la *unidad* no está en el intervalo comprendido entre 1 y 26, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función **_chdrive** devuelve-1, **errno** se establece en **EACCES**y **_doserrno** se establece en **ERROR_INVALID_DRIVE**.

La función **_chdrive** no es segura para subprocesos porque depende de la función **SetCurrentDirectory**, que a su vez no es segura para subprocesos. Para usar **_chdrive** de forma segura en una aplicación multiproceso, debe proporcionar su propia sincronización de subprocesos. Para obtener más información, vea [SetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory).

La función **_chdrive** solo cambia la unidad de trabajo actual; **_chdir** cambia el directorio de trabajo actual.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_chdrive**|\<direct.h>|

Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [_getdrive](getdrive.md).

## <a name="see-also"></a>Vea también

[Control de directorio](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
