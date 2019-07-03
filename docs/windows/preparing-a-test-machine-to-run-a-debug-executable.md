---
title: Preparar un equipo de pruebas para ejecutar un archivo ejecutable de depuración
ms.date: 07/02/2019
helpviewer_keywords:
- debug executable, preparing a test machine to run
ms.assetid: f0400989-cc2e-4dce-9788-6bdbe91c6f5a
ms.openlocfilehash: 87d2bf434aef3a85bf7fa19f5886bec106515809
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552339"
---
# <a name="preparing-a-test-machine-to-run-a-debug-executable"></a>Preparar un equipo de pruebas para ejecutar un archivo ejecutable de depuración

Para preparar un equipo con el fin de probar la versión de depuración de una aplicación compilada con Visual C++, tiene que implementar versiones de depuración de los archivos DLL de biblioteca de Visual C++ de los que depende la aplicación. Para identificar qué archivos DLL se deben implementar, siga los pasos de [Descripción de las dependencias de una aplicación de Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md). Normalmente, las versiones de depuración de los archivos DLL de biblioteca de Visual C++ tienen nombres que terminan en "d"; por ejemplo, la versión de depuración del archivo msvcr100.dll se denomina msvcr100d.dll.

> [!NOTE]
>  Las versiones de depuración de una aplicación no son redistribuibles, como tampoco lo son las correspondientes a los archivos DLL de biblioteca de Visual C++. Puede implementar versiones de depuración de las aplicaciones y los archivos DLL de Visual C++ solo en otros equipos de su propiedad, con el único propósito de depurar y probar las aplicaciones en un equipo que no tiene Visual Studio instalado. Para obtener más información, vea [Redistributing Visual C++ Files](redistributing-visual-cpp-files.md).

Hay tres maneras de implementar versiones de depuración de archivos DLL de biblioteca de Visual C++ junto con la versión de depuración de una aplicación.

- Utilice la implementación central para instalar una versión de depuración de un archivo DLL de Visual C++ determinado en el directorio %windir%\system32\ mediante un proyecto de instalación que incluya módulos de fusión mediante combinación para la versión de biblioteca y la arquitectura de la aplicación correctas. Los módulos de combinación se encuentran en el directorio Archivos de programa o Archivos de programa (x86), en \Common Files\Merge Modules\\. La versión de depuración de un módulo de fusión mediante combinación contiene Debug en el nombre; por ejemplo, Microsoft_VC110 _DebugCRT_x86.msm. Puede encontrar un ejemplo de esta implementación en [Tutorial: Implementar una aplicación de Visual C++ mediante un proyecto de instalación](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

- Use la implementación local para instalar una versión de depuración de un archivo DLL de Visual C++ concreto en el directorio de instalación de la aplicación mediante los archivos que se proporcionan en el directorio Archivos de programa o Archivos de programa (x86), en \Microsoft Visual Studio \<versión>\VC\redist\Debug_NonRedist\\.

    > [!NOTE]
    >  Para la depuración remota de una aplicación compilada con Visual Studio 2005 o Visual Studio 2008 en otro equipo, tendrá que implementar versiones de depuración de Visual C++ archivos DLL como ensamblados en paralelo compartidos de biblioteca. Puede utilizar un proyecto de instalación o Windows Installer para instalar los módulos de combinación correspondientes.

- Use la opción **Implementar** del cuadro de diálogo **Administrador de configuración** de Visual Studio para copiar la salida del proyecto y otros archivos en el equipo remoto.

Una vez instalados los archivos DLL de Visual C++, puede ejecutar un depurador remoto en un recurso compartido de red. Para obtener más información sobre la depuración remota, vea [Depuración remota](/visualstudio/debugger/remote-debugging).

## <a name="see-also"></a>Vea también

[Implementación en Visual C++](deployment-in-visual-cpp.md)<br>
[Opciones de la línea de comandos de Windows Installer](/windows/desktop/Msi/command-line-options)<br>
[Ejemplos de implementación](deployment-examples.md)<br>
[Remote Debugging](/visualstudio/debugger/remote-debugging)
