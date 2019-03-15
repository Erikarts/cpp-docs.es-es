---
title: /Fx (Combinar código insertado)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExpandAttributedSource
- /Fx
- VC.Project.VCCLCompilerTool.ExpandAttributedSource
helpviewer_keywords:
- Fx compiler option [C++]
- -Fx compiler option [C++]
- injected code
- merging injected code
- /Fx compiler option [C++]
ms.assetid: 14f0e301-3bab-45a3-bbdf-e7ce66f20560
ms.openlocfilehash: f1a266eee4edc524fbbe49bdef31a8235f62bd3c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818146"
---
# <a name="fx-merge-injected-code"></a>/Fx (Combinar código insertado)

Genera una copia de cada archivo de origen con código insertado combinado en el origen.

## <a name="syntax"></a>Sintaxis

```
/Fx
```

## <a name="remarks"></a>Comentarios

Para distinguir un archivo de origen combinado de un archivo de origen original, **/Fx** agrega una extensión .mrg entre el nombre de archivo y la extensión de archivo. Por ejemplo, un archivo denominado MyCode.cpp que contiene código con atributos creado con **/Fx** crea un archivo denominado MyCode.mrg.cpp que contiene el código siguiente:

```
//+++ Start Injected Code
[no_injected_text(true)];      // Suppress injected text, it has
                               // already been injected
#pragma warning(disable: 4543) // Suppress warnings about skipping
                               // injected text
#pragma warning(disable: 4199) // Suppress warnings from attribute
                               // providers
//--- End Injected Code
```

En un archivo .mrg, el código insertado a causa de un atributo se delimita de la siguiente manera:

```
//+++ Start Injected Code
...
//--- End Injected Code
```

El atributo [no_injected_text](../../windows/no-injected-text.md) está insertado en un archivo .mrg, lo que permite la compilación del archivo .mrg sin volver a insertar texto.

Debe tener en cuenta que el archivo de origen .mrg está diseñado para ser una representación del código fuente insertado por el compilador. Es posible que el archivo .mrg no se compile ni ejecute exactamente como el archivo de origen.

Las macros no se expanden en el archivo .mrg.

Si el programa incluye un archivo de encabezado que usa código insertado, **/Fx** genera un archivo .mrg.h para ese encabezado. **/Fx** no combina archivos incluidos que no usan código insertado.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Archivos de salida** .

1. Modifique la propiedad **Código fuente con atributos expandidos** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExpandAttributedSource%2A>.

## <a name="see-also"></a>Vea también

[/F (Opciones del archivo de resultados)](output-file-f-options.md)<br/>
[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
