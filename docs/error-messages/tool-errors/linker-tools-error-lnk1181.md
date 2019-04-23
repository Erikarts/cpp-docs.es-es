---
title: Error de las herramientas del vinculador LNK1181
ms.date: 08/22/2018
f1_keywords:
- LNK1181
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
ms.openlocfilehash: 657e78ece2ce4039eb8dc8561abd455c60aaff75
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59035081"
---
# <a name="linker-tools-error-lnk1181"></a>Error de las herramientas del vinculador LNK1181

no se puede abrir el archivo de entrada 'filename'

No se pudo encontrar el vinculador `filename` porque no existe o no se encontró la ruta de acceso.

Algunas causas comunes de error LNK1181 se incluyen:

- `filename` se hace referencia como una dependencia adicional en la línea del vinculador, pero el archivo no existe.

- Un **/libpath** instrucción que especifica el directorio que contiene `filename` falta.

Para resolver los problemas mencionados anteriormente, asegúrese de que los archivos que se hace referencia en la línea del vinculador están presentes en el sistema.  Asegúrese también de hay un **/libpath** instrucción para cada directorio que contiene un archivo dependiente del vinculador.

Para obtener más información, consulte [archivos .lib como entrada del vinculador](../../build/reference/dot-lib-files-as-linker-input.md).

Otra causa posible de LNK1181 es que un nombre de archivo largo con espacios incrustados no estaba entre comillas.  En ese caso, el vinculador solo reconoce un nombre de archivo hasta el primer espacio y, a continuación, se supone una extensión de archivo. obj.  La solución a esta situación es incluir el nombre de archivo largos (nombre de archivo además de la ruta de acceso) entre comillas.

Compilar con la [/P (Preprocesar para un archivo)](../../build/reference/p-preprocess-to-a-file.md) opción puede producir LNK1181 porque esta opción suprime la creación de archivos .obj.

## <a name="see-also"></a>Vea también

[/LIBPATH (Directorios de bibliotecas adicionales)](../../build/reference/libpath-additional-libpath.md)