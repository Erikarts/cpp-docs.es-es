---
title: /RANGE
ms.date: 11/04/2016
f1_keywords:
- /RANGE
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
ms.openlocfilehash: 011a8f9b2c8d0722e9aff98d52bb47dc549cc769
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421641"
---
# <a name="range"></a>/RANGE

Modifica la salida de dumpbin cuando se usa con otras opciones de dumpbin, como /RAWDATA o/DISASM.

## <a name="syntax"></a>Sintaxis

```
/RANGE:vaMin[,vaMax]
```

## <a name="parameters"></a>Parámetros

*vaMin*<br/>
La dirección virtual en el que desea que comience la operación dumpbin.

*vaMax*<br/>
(Opcional) La dirección virtual en el que quiere que la operación de dumpbin para finalizar. Si no se especifica, dumpbin irá al final del archivo.

## <a name="remarks"></a>Comentarios

Para ver las direcciones virtuales para una imagen, use el archivo de asignación para la imagen (RVA + Base), el **/DISASM** o **/HEADERS** opción de dumpbin, o la ventana Desensamblado en el depurador de Visual Studio.

## <a name="example"></a>Ejemplo

En este ejemplo, **/rango** se usa para modificar la presentación de la **/DISASM** opción. En este ejemplo, el valor inicial se expresa como un número decimal y el valor final se especifica como un número hexadecimal.

```
dumpbin /disasm /range:4219334,0x004061CD t.exe
```

## <a name="see-also"></a>Vea también

[Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)
