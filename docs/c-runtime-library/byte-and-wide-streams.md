---
title: Secuencias anchas y de bytes
ms.date: 11/04/2016
f1_keywords:
- Byte and Wide Streams
helpviewer_keywords:
- byte streams
- wide streams
ms.assetid: 61ef0587-4cbc-4eb8-aae5-4c298dbbc6f9
ms.openlocfilehash: 67de6b609b3e0546d539ef9c37f12db1067546ad
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739368"
---
# <a name="byte-and-wide-streams"></a>Secuencias anchas y de bytes

Una secuencia de bytes trata un archivo como una secuencia de bytes. Dentro del programa, la secuencia es la secuencia de bytes idéntica.

Por el contrario, una secuencia ancha trata un archivo como una secuencia de caracteres multibyte generalizados, lo que puede tener una amplia gama de reglas de codificación. (Los archivos de texto y binarios todavía se leen y escriben como se describió anteriormente). En el programa, el flujo es similar a la secuencia correspondiente de caracteres anchos. Las conversiones entre las dos representaciones se producen dentro de la biblioteca de C estándar. Las reglas de conversión, en principio, se pueden modificar mediante una llamada a [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) que modifica la categoría `LC_CTYPE`. Cada secuencia ancha determina sus reglas de conversión en el momento en que se convierte en ancha y conserva estas reglas incluso si la categoría `LC_CTYPE` cambia posteriormente.

El posicionamiento dentro de una secuencia ancha tiene las mismas limitaciones que las secuencias de texto. Además, el indicador de posición de archivo también puede tener que tratar con una codificación dependiente del estado. Normalmente, contiene tanto un desplazamiento de bytes en la secuencia como un objeto de tipo `mbstate_t`. Por lo tanto, la única manera confiable de obtener una posición de archivo dentro de una secuencia ancha consiste en llamar a [fgetpos](../c-runtime-library/reference/fgetpos.md), y la única manera confiable de restaurar una posición obtenida de esta manera consiste en llamar a [fsetpos](../c-runtime-library/reference/fsetpos.md).

## <a name="see-also"></a>Vea también

[Archivos y secuencias](../c-runtime-library/files-and-streams.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)
