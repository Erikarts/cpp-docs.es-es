---
title: Compilar bibliotecas de importación y archivos de exportación
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLibrarianTool.ModuleDefinitionFile
- VC.Project.VCLibrarianTool.ExportNamedFunctions
- VC.Project.VCLibrarianTool.GenerateDebug
- VC.Project.VCLibrarianTool.ForceSymbolReferences
helpviewer_keywords:
- OUT library manager option
- INCLUDE library manager option
- /DEF library manager option
- exporting data
- import libraries, building
- -INCLUDE library manager option
- /OUT library manager option
- DEF library manager option
- -DEF library manager option
- -OUT library manager option
- /INCLUDE library manager option
- -EXPORT library manager option
- exporting data, export (.exp) files
- /EXPORT library manager option
- EXPORT library manager option
- .lib files
- EXP files
ms.assetid: 2fe4f30a-1dd6-4b05-84b5-0752e1dee354
ms.openlocfilehash: 37c3169b66e1120dbfdb3a69379430e9bc8a1586
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813492"
---
# <a name="building-an-import-library-and-export-file"></a>Compilar bibliotecas de importación y archivos de exportación

Para generar una biblioteca de importación y exportación de archivo, use la sintaxis siguiente:

> **LIB /DEF**[**:**<em>deffile</em>] [*options*] [*objfiles*] [*libraries*]

Cuando se especifica/def, LIB crea los archivos de salida de las especificaciones de exportación que se pasan en el comando LIB. Hay tres métodos para especificar exportaciones, aparece en el orden recomendado de uso:

1. Un **__declspec (dllexport)** definición en uno de los *archivos (objfiles)* o *bibliotecas*

1. Una especificación de/Export:*nombre* en la línea de comandos LIB

1. Una definición en un **exportaciones** instrucción en un *archivo (deffile)*

Estos son los mismos métodos que se usa para especificar exportaciones al vincular un programa exportador. Un programa puede usar más de un método. Puede especificar las partes del comando LIB (por ejemplo, varios *archivos (objfiles)* o especificaciones/Export) en un archivo de comandos en el comando LIB, al igual que podía puede en un comando de LINK.

Las siguientes opciones se aplican a la creación de una biblioteca de importación y exportación de archivo:

> **/ OUT:** *importar*

Invalida el nombre del archivo de salida predeterminado para el *importar* biblioteca que se está creando. Cuando no se especifica/out, el nombre predeterminado es el nombre base del primer archivo objeto o biblioteca en el comando LIB y la extensión. lib. El archivo de exportación tiene el mismo nombre base que la biblioteca de importación y la extensión. exp.

> **/ EXPORT:** *entrada* \[ **=** *internalname*]\[,**\@** <em>ordinal</em>\[, **NONAME**]]\[, **datos**]

Exporta una función desde el programa para permitir que otros programas para llamar a la función. También puede exportar datos (mediante la **datos** palabra clave). Las exportaciones se definen normalmente en un archivo DLL.

El *entrada* es el nombre de la función o elemento de datos que va a ser utilizada por el programa que realiza la llamada. Opcionalmente, puede especificar el *internalname* como la función conocida en el programa que define; de forma predeterminada, *internalname* es el mismo que *entrada*. El *ordinal* especifica un índice en la tabla de exportación en el intervalo 1 a 65535; si no especifica *ordinal*, LIB asigna un valor. El **NONAME** palabra clave exporta la función solo como un valor ordinal, sin un *entrada*. El **datos** palabra clave se usa para exportar objetos sólo de datos.

> **/INCLUDE:** *symbol*

Agrega el objeto especificado *símbolos* a la tabla de símbolos. Esta opción es útil para forzar el uso de un objeto de biblioteca que de lo contrario no estarían incluido.

Tenga en cuenta que si crea la biblioteca de importación en un paso preliminar, antes de crear el archivo .dll, debe pasar el mismo conjunto de archivos de objeto al compilar el archivo .dll, que se pasa al compilar la biblioteca de importación.

## <a name="see-also"></a>Vea también

[Trabajar con bibliotecas de importación y archivos de exportación](working-with-import-libraries-and-export-files.md)
