---
title: Tipos de archivos creados para proyectos de Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- header files [C++], Visual Studio projects
- ActiveX controls [C++], Help files
- def files
- project items [C++], files
- Visual Studio C++ projects, files and directories
- resource files, created by wizard
- files [C++], extensions
- Help files, for ActiveX controls
- Web projects [C++], adding items
- .def files
- licensing ActiveX controls
ms.assetid: 2b0ee2e0-ae81-4185-9bb9-11da3c99a283
ms.openlocfilehash: 7ef8127b829b60d84af72874292c33ae1c7c4636
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2019
ms.locfileid: "58327586"
---
# <a name="file-types-created-for-visual-studio-c-projects"></a>Tipos de archivos creados para proyectos de C++ de Visual Studio

En este tema se describe todos los tipos de archivos que están asociados con los proyectos de Visual Studio para aplicaciones de escritorio clásicos. Los archivos incluidos en el proyecto dependen del tipo de proyecto y de las opciones que seleccione al usar un asistente.

- [Archivos de proyecto y solución](project-and-solution-files.md)

- [Proyectos de CLR](files-created-for-clr-projects.md)

- [Archivos de encabezado y código fuente de controles o programas ATL](atl-program-or-control-source-and-header-files.md)

- [Archivos de encabezado y código fuente de controles o programas MFC](mfc-program-or-control-source-and-header-files.md)

- [Archivos de encabezado precompilados](../creating-precompiled-header-files.md)

- [Archivos de recursos](resource-files-cpp.md)

- [Archivos de ayuda (WinHelp)](help-files-winhelp.md)

- [Archivos de indicaciones](hint-files.md)

Al crear un proyecto de Visual Studio, es posible crear una nueva solución o agregando un proyecto a una solución. Las aplicaciones no triviales se suelen desarrollar con varios proyectos en una solución.

Los proyectos suelen producen un archivo EXE o DLL. Los proyectos pueden ser dependientes entre sí; durante el proceso de compilación, el entorno de Visual Studio comprueba las dependencias dentro y entre proyectos. Cada proyecto tiene código fuente básico y, según el tipo de proyecto, puede incluir muchos otros archivos que contienen distintos aspectos del proyecto. El contenido de estos archivos se indica mediante la extensión de archivo. El entorno de desarrollo de Visual Studio usa las extensiones de archivo para determinar cómo administrar el contenido del archivo durante una compilación.

En la tabla siguiente muestra los archivos comunes en un proyecto de Visual Studio y se identifica con su extensión de archivo.

|Extensión de archivo|Tipo|Contenido|
|--------------------|----------|--------------|
|.asmx|Origen|Archivo de implementación.|
|.asp|Origen|Archivo de página Active Server.|
|.atp|Proyecto|Archivo de proyecto de plantilla de aplicación.|
|.bmp, .dib, .gif, .jpg, .jpe, .png|Recurso|Archivos de imagen general.|
|.bsc|Compilación|Archivo de código del explorador.|
|.cpp, .c|Origen|Archivos de código fuente principal de la aplicación.|
|.cur|Recurso|Archivo de gráficos de mapa de bits de cursor.|
|.dbp|Proyecto|Archivo de proyecto de base de datos.|
|.disco|Origen|Archivo de documento de detección dinámica. Controla la detección de servicios web XML.|
|.exe, .dll|Proyecto|Archivos de biblioteca de vínculos dinámicos o ejecutable.|
|.h|Origen|Archivo de inclusión de encabezado.|
|.htm, .html, .xsp, .asp, .htc, .hta, .xml|Recurso|Archivos web comunes.|
|.HxC|Proyecto|Archivo de proyecto de ayuda.|
|.ico|Recurso|Archivo de gráficos de mapa de bits de icono.|
|.idb|Compilación|Archivo de estado, con información sobre las dependencias entre los archivos de código fuente y las definiciones de clase, que puede usar el compilador durante la recompilación mínima y la compilación incremental. Use la opción [/Fd](fd-program-database-file-name.md) del compilador para especificar el nombre del archivo .idb. Consulte [/Gm (Habilitar recompilación mínima)](gm-enable-minimal-rebuild.md) para obtener más información.|
|.idl|Compilación|Archivo de lenguaje de definición de interfaz. Vea [Interface Definition (IDL) File](/windows/desktop/Rpc/the-interface-definition-language-idl-file) (Archivo de definición de interfaz (IDL)) en Windows SDK para obtener más información.|
|.ilk|Vinculación|Archivo de vinculación incremental. Vea [/INCREMENTAL](incremental-link-incrementally.md) para obtener más información.|
|.map|Vinculación|Archivo de texto que contiene información de enlazador. Use la opción [/Fm](fm-name-mapfile.md) del compilador para asignar un nombre al archivo de asignación. Vea [/MAP](map-generate-mapfile.md) para obtener más información.|
|.mfcribbon-ms|Recurso|Archivo de recursos que contiene el código XML que define los botones, los controles y los atributos de la cinta de opciones. Para obtener más información, vea [Ribbon Designer (MFC)](../../mfc/ribbon-designer-mfc.md).|
|.obj, .o||Archivos de objeto, compilados pero no vinculados.|
|.pch|Depuración|Archivo de encabezado precompilado.|
|.rc, .rc2|Recurso|[Archivos de script de recursos](../../windows/working-with-resource-files.md) para generar recursos.|
|.sbr|Compilación|Archivo intermedio de explorador de código fuente. Archivo de entrada para [BSCMAKE](bscmake-options.md).|
|.sln|Soluciones|Archivo de [solución](/visualstudio/ide/solutions-and-projects-in-visual-studio) .|
|.suo|Soluciones|Archivo de opciones de solución.|
|.txt|Recurso|Archivo de texto, normalmente el archivo "Léame".|
|.vap|Proyecto|Archivo de proyecto de Visual Studio Analyzer.|
|.vbg|Soluciones|Archivo de grupo de proyectos compatible.|
|.vbp, .vip, .vbproj|Proyecto|Archivo de proyecto de Visual Basic.|
|.vcxitems|Proyecto|Proyecto de elementos compartidos para compartir archivos de código entre varios proyectos de C++. Consulte [archivos de proyecto y solución](project-and-solution-files.md) para obtener más información.|
|.vcxproj|Proyecto|El archivo de proyecto de Visual Studio. Consulte [archivos de proyecto y solución](project-and-solution-files.md) para obtener más información.|
|.vcxproj.filters|Proyecto|Cuando se usa el Explorador de soluciones para agregar un archivo a un proyecto, el archivo de filtros define dónde se agrega el archivo en la vista de árbol del Explorador de soluciones, en función de su extensión de nombre de archivo.|
|.vdproj|Proyecto|Archivo de proyecto de implementación de Visual Studio.|
|.vmx|Proyecto|Archivo de proyecto de macros.|
|.vup|Proyecto|Archivo de proyecto de utilidad.|

Para obtener información sobre otros archivos asociados a Visual Studio, consulte [Tipos y extensiones de archivo en Visual Studio .NET](/visualstudio/ide/reference/project-and-solution-file-types).

Los archivos de proyecto se organizan en carpetas en el Explorador de soluciones. Visual Studio crea una carpeta para los archivos de código fuente, archivos de encabezado y archivos de recursos, pero puede reorganizar dichas carpetas o crear otros nuevos. Puede usar las carpetas para organizar de forma explícita clústeres lógicos de archivos dentro de la jerarquía de un proyecto. Por ejemplo, puede crear carpetas que contengan todos los archivos de origen de la interfaz de usuario, o las especificaciones, la documentación o los conjuntos de pruebas. Todos los nombres de las carpetas de archivos deben ser únicos.

Al agregar un elemento a un proyecto, el elemento se agrega a todas las configuraciones de ese proyecto, independientemente de si el elemento es compilable o no. Por ejemplo, si tiene un proyecto denominado MyProject, cuando agrega un elemento, este se agrega a las configuraciones de depuración y de lanzamiento del proyecto.

## <a name="see-also"></a>Vea también

[Creación y administración de proyectos de Visual Studio C++](../creating-and-managing-visual-cpp-projects.md)<br>
[Tipos de proyecto de C++ de Visual Studio](visual-cpp-project-types.md)<br>