---
title: _pgmptr, _wpgmptr
ms.date: 11/04/2016
f1_keywords:
- pgmptr
- _pgmptr
- wpgmptr
- _wpgmptr
helpviewer_keywords:
- wpgmptr function
- _wpgmptr function
- _pgmptr function
- pgmptr function
ms.assetid: 4d44b515-0eff-4136-8bc4-684195f218f5
ms.openlocfilehash: beff0401d0aa2aa21819e58618ef4c02795d4393
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300162"
---
# <a name="_pgmptr-_wpgmptr"></a>_pgmptr, _wpgmptr

Ruta de acceso al archivo ejecutable. En desuso; use [_get_pgmptr](../c-runtime-library/reference/get-pgmptr.md) y [_get_wpgmptr](../c-runtime-library/reference/get-wpgmptr.md).

## <a name="syntax"></a>Sintaxis

```
extern char *_pgmptr;
extern wchar_t *_wpgmptr;
```

## <a name="remarks"></a>Notas

Cuando se ejecuta un programa desde el intérprete de comandos (Cmd.exe), `_pgmptr` se inicializa automáticamente en la ruta de acceso completa al archivo ejecutable. Por ejemplo, si se encuentra Hello.exe en C:\BIN, y C:\BIN está en la ruta de acceso, `_pgmptr` se establece en C:\BIN\Hello.exe cuando se ejecuta:

```
C> hello
```

Cuando un programa no se ejecuta desde la línea de comandos, `_pgmptr` podría inicializarse en el nombre del programa (nombre base del archivo sin la extensión de nombre de archivo) o en un nombre de archivo, una ruta de acceso relativa o una ruta de acceso completa.

`_wpgmptr` es el equivalente de caracteres anchos de `_pgmptr` para su uso con los programas que utilizan `wmain`.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|

## <a name="requirements"></a>Requisitos de

|Variable|Encabezado necesario|
|--------------|---------------------|
|`_pgmptr`, `_wpgmptr`|\<stdlib.h>|

## <a name="example"></a>Ejemplo

El siguiente programa muestra el uso de `_pgmptr`.

```c
// crt_pgmptr.c
// compile with: /W3
// The following program demonstrates the use of _pgmptr.
//
#include <stdio.h>
#include <stdlib.h>
int main( void )
{
   printf("The full path of the executing program is : %Fs\n",
     _pgmptr); // C4996
   // Note: _pgmptr is deprecated; use _get_pgmptr instead
}
```

Puede usar `_wpgmptr` cambiando `%Fs` a `%S` y `main` a `wmain`.

## <a name="see-also"></a>Vea también

[Variables globales](../c-runtime-library/global-variables.md)
