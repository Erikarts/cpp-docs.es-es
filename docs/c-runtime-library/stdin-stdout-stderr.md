---
title: stdin, stdout, stderr
ms.date: 10/23/2018
f1_keywords:
- stdin
- stderr
- stdout
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
ms.openlocfilehash: 5de1ff01282f30ad133f909cb87f5d7c8d521ae5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741948"
---
# <a name="stdin-stdout-stderr"></a>stdin, stdout, stderr

## <a name="syntax"></a>Sintaxis

```
FILE *stdin;
FILE *stdout;
FILE *stderr;
#include <stdio.h>
```

## <a name="remarks"></a>Comentarios

Se trata de las secuencias estándar de entrada, salida y salida de errores.

De forma predeterminada, la entrada estándar se lee desde el teclado, mientras que la salida estándar y el error estándar se imprimen en la pantalla.

Los siguientes punteros de secuencia están disponibles para acceder a las secuencias estándar:

|Puntero|Secuencia|
|-------------|------------|
|`stdin`|Entrada estándar|
|`stdout`|Salida estándar|
|`stderr`|Error estándar|

Estos punteros pueden usarse como argumentos para las funciones. Algunas funciones, como [getchar](../c-runtime-library/reference/getchar-getwchar.md) y [putchar](../c-runtime-library/reference/putchar-putwchar.md), usan `stdin` y `stdout` automáticamente.

Estos punteros son constantes, y no se pueden asignar nuevos valores. La función [freopen](../c-runtime-library/reference/freopen-wfreopen.md) puede usarse para redirigir las secuencias a archivos de disco o a otros dispositivos. El sistema operativo permite redirigir una entrada y salida estándar del programa a nivel de comando.

## <a name="see-also"></a>Vea también

[E/S de secuencia](../c-runtime-library/stream-i-o.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
