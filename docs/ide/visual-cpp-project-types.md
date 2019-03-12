---
title: Tipos de proyecto de Visual C++
ms.date: 10/30/2017
helpviewer_keywords:
- programs [C++], projects
- project templates [Visual Studio], C++
- TODO comments [C++]
- projects [C++], types
- templates [C++], projects
- applications [C++], projects
- Visual C++ projects, types
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
ms.openlocfilehash: 7a81d73100ef52b61f834f7bffe4467bd296c079
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744553"
---
# <a name="visual-c-project-types"></a>Tipos de proyecto de Visual C++

Se puede usar una plantilla de proyecto para crear la estructura básica de programa, menús, barras de herramientas, iconos, referencias e instrucciones `#include` adecuados para el tipo de proyecto que quiera crear. Visual Studio incluye diversos tipos de plantilla de proyecto de Visual C++, muchos de ellos con su correspondiente asistente para que pueda personalizar sus proyectos mientras los va creando. Justo después de crear un proyecto, se puede compilar y ejecutar la aplicación; un procedimiento recomendado consiste en compilar cada cierto tiempo mientras se desarrolla la aplicación.

No es necesario usar una plantilla para crear un proyecto, pero muchas veces es lo más eficaz, dado que es más fácil modificar los archivos de proyecto y la estructura existentes que crearlos desde cero.

> [!NOTE]
> Puede crear un proyecto de lenguaje C con plantillas de proyecto de C++. En el proyecto generado, busque los archivos que tengan la extensión de nombre de archivo .cpp y cámbiela por .c. Luego, en la página **Propiedades del proyecto** del proyecto (no de la solución), expanda **Propiedades de configuración**y **C/C++** y seleccione **Avanzadas**. Cambie la opción **Compilar como** por **Compilar como código de C (/TC)**.

## <a name="project-templates"></a>Plantillas de proyecto

Las plantillas de proyecto que se incluyen en Visual Studio dependen de la versión del producto y de las cargas de trabajo que se hayan instalado. Si se ha instalado la carga de trabajo Desarrollo para el escritorio con C++, Visual Studio tiene estas plantillas de proyecto de Visual C++.

### <a name="windows-desktop"></a>Escritorio de Windows

|Plantilla de proyecto|Descripción|
|----------------------|-----------------------------|
|[Aplicación de consola Windows](../windows/creating-a-console-application.md)|Un proyecto para crear una aplicación de consola Windows.|
|[Aplicación de escritorio de Windows](../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|Un proyecto para crear una aplicación de escritorio de Windows (Win32).|
|[Biblioteca de vínculos dinámicos](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|Un proyecto para crear una biblioteca de vínculos dinámicos (DLL).|
|[Biblioteca estática](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|Un proyecto para crear una biblioteca estática (LIB).|
|Asistente para escritorio de Windows|Un asistente para crear aplicaciones de escritorio de Windows y bibliotecas con opciones adicionales.|

### <a name="general"></a>General

|Plantilla de proyecto|Descripción|
|----------------------|-----------------------------|
|Proyecto vacío|Un proyecto vacío para crear una aplicación, biblioteca o archivo DLL. Debe agregar el código o los recursos necesarios.|
|[Proyecto de archivo Make](../ide/creating-a-makefile-project.md)|Un proyecto para usar un sistema de compilación externo.|
|Proyecto de elementos compartidos|Un proyecto que se usa para compartir archivos entre varios proyectos.|

### <a name="atl"></a>ATL

|Plantilla de proyecto|Descripción|
|----------------------|-----------------------------|
|[Proyecto ATL](../atl/reference/creating-an-atl-project.md)|Un proyecto en el que se usa Active Template Library.|

### <a name="test"></a>Prueba

|Plantilla de proyecto|Descripción|
|----------------------|-----------------------------|
|[Proyecto de prueba unitaria nativo](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)|Un proyecto que contiene pruebas unitarias de C++ nativas.|

### <a name="mfc"></a>MFC

Si se agrega el componente de compatibilidad con MFC y ATL a la instalación de Visual Studio, estas plantillas de proyecto se agregan a Visual Studio.

|Plantilla de proyecto|Descripción|
|----------------------|-----------------------------|
|[Aplicación MFC](../mfc/reference/creating-an-mfc-application.md)|Un proyecto para crear una aplicación en la que se usa la biblioteca MFC (Microsoft Foundation Class).|
|[Control ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md)|Un proyecto para crear un control ActiveX en el que se usa la biblioteca MFC.|
|[DLL MFC](../mfc/reference/creating-an-mfc-dll-project.md)|Un proyecto para crear una biblioteca de vínculos dinámicos en la que se usa la biblioteca MFC.|

### <a name="windows-universal-apps"></a>Aplicaciones universales de Windows

Si se agrega el componente Herramientas de la plataforma universal de Windows a la instalación de Visual Studio, estas plantillas de proyecto se agregan a Visual Studio.

Para obtener información general sobre las aplicaciones universales de Windows en C++, vea [Aplicaciones universales de Windows (C++)](../windows/universal-windows-apps-cpp.md).

|Plantilla de proyecto|Descripción|
|----------------------|-----------------------------|
|Aplicación vacía|Un proyecto para una aplicación para Plataforma universal de Windows (UWP) de una sola página sin controles o diseños predefinidos.|
|Aplicación de DirectX 11|Un proyecto para una aplicación para Plataforma universal de Windows que usa DirectX 11.|
|Aplicación de DirectX 12|Un proyecto para una aplicación para Plataforma universal de Windows que usa DirectX 12.|
|Aplicación XAML y DirectX 11|Un proyecto para una aplicación para Plataforma universal de Windows que use DirectX 11 y XAML.|
|Aplicación de pruebas unitarias|Un proyecto para crear una aplicación de prueba unitaria para aplicaciones para Plataforma universal de Windows (UWP).|
|Archivo DLL|Un proyecto para una biblioteca de vínculos dinámicos nativa (DLL) que se pueda usar en una aplicación para Plataforma universal de Windows o un componente en tiempo de ejecución.|
|Biblioteca estática|Un proyecto para una biblioteca de vínculos estáticos (LIB) nativa que una aplicación para Plataforma universal de Windows o un componente en tiempo de ejecución puedan usar.|
|Componente de Windows en tiempo de ejecución|Un proyecto para un componente de Windows Runtime que se pueda usar en una aplicación para Plataforma universal de Windows, con independencia del lenguaje de programación en el que se escriba la aplicación.|
|Proyecto de paquete de aplicación de Windows|Un proyecto que crea un paquete UWP que permite que una aplicación de escritorio se transfiera localmente o se distribuya a través de Microsoft Store.|

## <a name="todo-comments"></a>Comentarios TODO

Muchos de los archivos que se generan mediante una plantilla de proyecto contienen comentarios TODO que ayudan a saber dónde puede incluir su propio código fuente. Para obtener más información sobre cómo agregar código, vea [Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md) y [Trabajar con archivos de recursos](../windows/working-with-resource-files.md).

## <a name="see-also"></a>Vea también

[Crear proyectos de escritorio con asistentes para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md)
