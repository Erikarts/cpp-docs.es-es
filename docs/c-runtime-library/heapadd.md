---
title: _heapadd
ms.date: 11/04/2016
api_name:
- _heapadd
api_location:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- heapadd
- _heapadd
helpviewer_keywords:
- _heapadd function
- memory, adding to heaps
- heaps, adding memory
- heapadd function
ms.assetid: 4d691fe2-2763-49f4-afb1-62738b7cd3ff
ms.openlocfilehash: 4be87710519c9a389adbaf41fefddb9ea8dfb1e6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940284"
---
# <a name="_heapadd"></a>_heapadd

Agrega memoria al montón.

> [!IMPORTANT]
>  Esta función está obsoleta. A partir de Visual Studio 2015, no está disponible en CRT.

## <a name="syntax"></a>Sintaxis

```
int _heapadd(
   void *memblock,
   size_t size
);
```

#### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero a la memoria del montón.

*size*<br/>
Tamaño de la memoria que se agregará, en bytes.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, `_heapadd` devuelve 0; en caso contrario, la función devuelve -1 y establece `errno` en `ENOSYS`.

Para más información sobre este y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

A partir de la versión 4.0 de Visual C++, la estructura del montón subyacente se movió a las bibliotecas de tiempo en ejecución de C para admitir las nuevas características de depuración. Como resultado, `_heapadd` ya no se admite en ninguna plataforma que se base en la API de Win32.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|`_heapadd`|\<malloc.h>|\<errno.h>|

Para obtener más información de compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md) en la Introducción.

## <a name="see-also"></a>Vea también

[Asignación de memoria](../c-runtime-library/memory-allocation.md)<br/>
[free](../c-runtime-library/reference/free.md)<br/>
[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapmin](../c-runtime-library/reference/heapmin.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[malloc](../c-runtime-library/reference/malloc.md)<br/>
[realloc](../c-runtime-library/reference/realloc.md)
