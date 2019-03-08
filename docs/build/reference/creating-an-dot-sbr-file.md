---
title: Crear un archivo .Sbr
ms.date: 11/04/2016
helpviewer_keywords:
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
ms.openlocfilehash: 54cf19a7024f6f0a1db33e1f1ccde15cde95301b
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418534"
---
# <a name="creating-an-sbr-file"></a>Crear un archivo .Sbr

Los archivos de entrada para BSCMAKE son archivos. sbr. El compilador crea un archivo .sbr para cada archivo de objeto (.obj) lo compila. Al crear o actualizar el archivo de información de examen, todos los archivos .sbr para el proyecto deben estar disponibles en disco.

Para crear un archivo .sbr con toda la información posible, especifique [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md).

Para crear un archivo .sbr que no contenga símbolos locales, especifique [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md). Si los archivos .sbr contienen símbolos locales, se puede omitir en el archivo .bsc mediante el uso de BSCMAKE [opción /El](../../build/reference/bscmake-options.md)`.`

Puede crear un archivo .sbr sin realizar una compilación completa. Por ejemplo, puede especificar la opción /Zs al compilador que debe realizar una comprobación de sintaxis y seguirá generando un archivo .sbr si especifica /FR o/el fr.

El proceso de compilación puede ser más eficaz si los archivos .sbr se empaquetan en primer lugar para quitar las definiciones sin referencia. El compilador empaqueta automáticamente los archivos. sbr.

## <a name="see-also"></a>Vea también

[Crear un archivo .Bsc](../../build/reference/building-a-dot-bsc-file.md)
