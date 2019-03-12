---
title: E/S de bajo nivel
ms.date: 11/04/2016
f1_keywords:
- c.io
helpviewer_keywords:
- I/O [CRT], low-level
- I/O [CRT], functions
- low-level I/O routines
- file handles [C++]
- file handles [C++], I/O functions
ms.assetid: 53e11bdd-6720-481c-8b2b-3a3a569ed534
ms.openlocfilehash: 7812656bdcb3f58866f91009b6ad3de9fd67cebe
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740142"
---
# <a name="low-level-io"></a>E/S de bajo nivel

Estas funciones invocan el sistema operativo directamente para la operación cuyo nivel es más bajo que el que ofrecen las E/S de secuencias. Las llamadas para entradas y salidas de bajo nivel no se almacenan en el búfer ni aplican formato a los datos.

Las rutinas de bajo nivel pueden acceder a los flujos estándar abiertos al iniciar el programa mediante los descriptores de archivo predefinidos siguientes.

|Secuencia|Descriptor del archivo|
|------------|---------------------|
|**stdin**|0|
|**stdout**|1|
|**stderr**|2|

Las rutinas de E/S de bajo nivel establecen la variable global [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) cuando se produce un error. Debe incluir STDIO.H al usar funciones de bajo nivel solo si su programa requiere una constante que se define en STDIO.H, por ejemplo, el indicador de fin de archivo (**EOF**).

## <a name="low-level-io-functions"></a>Funciones de E/S de bajo nivel

|Función|Usar|
|--------------|---------|
|[_close](../c-runtime-library/reference/close.md)|Cerrar archivo|
|[_commit](../c-runtime-library/reference/commit.md)|Vaciar el archivo en el disco|
|[_creat, _wcreat](../c-runtime-library/reference/creat-wcreat.md)|Crear archivo|
|[_dup](../c-runtime-library/reference/dup-dup2.md)|Devolver el siguiente descriptor de archivo disponible para el archivo especificado|
|[_dup2](../c-runtime-library/reference/dup-dup2.md)|Crear el segundo descriptor para un archivo concreto|
|[_eof](../c-runtime-library/reference/eof.md)|Probar el final de archivo|
|[_lseek, _lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)|Cambiar la posición del puntero de archivo a la ubicación especificada|
|[_open, _wopen](../c-runtime-library/reference/open-wopen.md)|Abrir archivo|
|[_read](../c-runtime-library/reference/read.md)|Leer datos del archivo|
|[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s, _wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Abrir archivo para uso compartido|
|[_tell, _telli64](../c-runtime-library/reference/tell-telli64.md)|Obtener la posición del puntero de archivo actual|
|[_umask](../c-runtime-library/reference/umask.md), [_umask_s](../c-runtime-library/reference/umask-s.md)|Establecer la máscara de permisos de archivo|
|[_write](../c-runtime-library/reference/write.md)|Escribir datos en el archivo|

**_dup** y **_dup2** se suelen usar para asociar los descriptores de archivo predefinidos con distintos archivos.

## <a name="see-also"></a>Vea también

[Entrada y salida](../c-runtime-library/input-and-output.md)<br/>
[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Llamadas del sistema](../c-runtime-library/system-calls.md)<br/>
