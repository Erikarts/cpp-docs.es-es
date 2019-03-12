---
title: Controlar secuencias
ms.date: 11/04/2016
f1_keywords:
- Controlling Streams
helpviewer_keywords:
- streams, controlling
- controlling streams
- streams
ms.assetid: 267e9013-9afc-45f6-91e3-ca093230d9d9
ms.openlocfilehash: 85c7e1b22519287fbd03d89487d6639f197a8b63
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743316"
---
# <a name="controlling-streams"></a>Controlar secuencias

[fopen](../c-runtime-library/reference/fopen-wfopen.md) devuelve la dirección de un objeto de tipo `FILE`. Use esta dirección como el argumento `stream` de varias funciones de la biblioteca para realizar distintas operaciones en un archivo abierto. Para una secuencia de bytes, todas las entradas se realizan como si cada carácter se leyera mediante una llamada a [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md), y todas las salidas se obtienen como si cada carácter se escribiera mediante una llamada a [fputc](../c-runtime-library/reference/fputc-fputwc.md). Para una secuencia ancha, todas las entradas se realizan como si cada carácter se leyera mediante una llamada a [fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md), y todas las salidas se obtienen como si cada carácter se escribiera mediante una llamada a [fputwc](../c-runtime-library/reference/fputc-fputwc.md).

Puede cerrar un archivo mediante una llamada a [fclose](../c-runtime-library/reference/fclose-fcloseall.md), operación tras la cual la dirección del objeto `FILE` ya no es válida.

Un objeto `FILE` almacena el estado de una secuencia, incluidos:

- Un indicador de error establecido como no nulo por una función que detecta un error de lectura o escritura.

- Un indicador de final de archivo establecido como no nulo por una función que detecta el final del archivo durante la lectura.

- Un indicador de posición de archivo especifica el siguiente byte de la secuencia que se va a leer o escribir, en caso de que el archivo admita solicitudes de posicionamiento.

- Un [estado de secuencia](../c-runtime-library/stream-states.md) especifica si la secuencia aceptará lecturas o escrituras y si dicha secuencia no está vinculada, está basada en bits o es ancha.

- Un estado de conversión recuerda el estado de cualquier carácter multibyte generalizado generado o ensamblado parcialmente, así como cualquier estado de desplazamiento de la secuencia de bytes del archivo.

- Un búfer de archivo especifica la dirección y el tamaño de un objeto de matriz que las funciones de la biblioteca pueden usar para mejorar el rendimiento de las operaciones de lectura y escritura de la secuencia.

No modifique cualquier valor almacenado en un objeto `FILE` o en un búfer de archivo que especifique para usarlo con ese objeto. No puede copiar un objeto `FILE` y usar de manera portátil la dirección de la copia como un argumento `stream` para una función de la biblioteca.

## <a name="see-also"></a>Vea también

[Archivos y secuencias](../c-runtime-library/files-and-streams.md)
