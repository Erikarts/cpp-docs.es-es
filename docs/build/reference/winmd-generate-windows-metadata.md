---
title: /WINMD (generar metadatos de Windows)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
ms.openlocfilehash: 45d6492c87b7543a54d031f02dcf09e319150131
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449741"
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD (generar metadatos de Windows)

Habilita la generación de un archivo de metadatos en tiempo de ejecución de Windows (.winmd).

> **/WINMD**\[ **:** {**NO**\|**ONLY**}]

## <a name="arguments"></a>Argumentos

**/WINMD**<br/>
La configuración predeterminada para aplicaciones de la plataforma Universal de Windows. El vinculador genera el archivo ejecutable binario y el archivo de metadatos de winmd.

**/WINMD:NO**<br/>
El vinculador genera solo el archivo ejecutable binario, pero no es un archivo winmd.

**/WINMD:ONLY**<br/>
El vinculador genera solo el archivo .winmd, pero no el archivo ejecutable binario.

## <a name="remarks"></a>Comentarios

El **/WINMD** opción del vinculador se usa para que aplicaciones de UWP y componentes de Windows en tiempo de ejecución para controlar la creación de un archivo de metadatos (.winmd) de Windows en tiempo de ejecución. Un archivo .winmd es un tipo de archivo DLL que contiene los metadatos para los tipos de Windows en tiempo de ejecución y, en el caso de los componentes en tiempo de ejecución, las implementaciones de esos tipos. Los metadatos siguen el [ECMA-335](https://www.ecma-international.org/publications/standards/Ecma-335.htm) estándar.

De forma predeterminada, el nombre de archivo de salida tiene el formato *NombreBinario*.winmd. Para especificar un nombre de archivo diferente, use el [/WINMDFILE](winmdfile-specify-winmd-file.md) opción.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **Windows metadatos** página de propiedades.

1. En el **generar metadatos de Windows** lista desplegable, seleccione la opción que desee.

## <a name="see-also"></a>Vea también

[Tutorial: Crear un componente Simple en tiempo de ejecución de Windows y llamarlo desde JavaScript](/windows/uwp/winrt-components/walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript)<br/>
[Introducción al lenguaje de definición de interfaz de Microsoft 3.0](/uwp/midl-3/intro)<br/>
[/WINMDFILE (Especificar archivo winmd)](winmdfile-specify-winmd-file.md)<br/>
[/WINMDKEYFILE (Especificar archivo de clave winmd)](winmdkeyfile-specify-winmd-key-file.md)<br/>
[/WINMDKEYCONTAINER (Especificar contenedor de claves)](winmdkeycontainer-specify-key-container.md)<br/>
[/WINMDDELAYSIGN (Firmar parcialmente un archivo winmd)](winmddelaysign-partially-sign-a-winmd.md)<br/>
[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
