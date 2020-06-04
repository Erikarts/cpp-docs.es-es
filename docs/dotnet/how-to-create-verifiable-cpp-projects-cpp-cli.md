---
title: Procedimiento Crear proyectos de C++ comprobables (C++ / c++ / CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- verifiable assemblies [C++], creating
- conversions, C++ projects
- Visual Studio C++ projects
ms.assetid: 4ef2cc1a-e3e5-4d67-8d8d-9c614f8ec5d3
ms.openlocfilehash: 0784e6f202750e846c75434eef62a12dab3952f1
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448112"
---
# <a name="how-to-create-verifiable-c-projects-ccli"></a>Cómo: crear proyectos de C++ comprobables (C++ / c++ / CLI)

Asistentes para aplicaciones de visuales C++ no crean proyectos comprobables.

> [!IMPORTANT]
> En desuso de Visual Studio 2015 y Visual Studio 2017 no admite la **/CLR: pure** y **/CLR: safe** creación de proyectos que se pueda comprobar. Si necesita código comprobable, se recomienda que trasladar el código en C#.

Sin embargo, si está utilizando una versión anterior de Microsoft C++ conjunto de herramientas del compilador que admita **/CLR: pure** y **/CLR: safe**, se pueden convertir los proyectos para que sea comprobable. Este tema describe cómo establecer las propiedades del proyecto y modificar archivos de código fuente del proyecto para transformar su Visual Studio C++ proyectos para producir aplicaciones comprobables.

## <a name="compiler-and-linker-settings"></a>Configuración de compilador y vinculador

De forma predeterminada, los proyectos de .NET use la marca de compilador/CLR y configuran al vinculador para hardware x86. Para código comprobable, debe usar el indicador/clr: safe e indicar al vinculador que genere MSIL en lugar de instrucciones máquina nativas.

### <a name="to-change-the-compiler-and-linker-settings"></a>Para cambiar la configuración del compilador y vinculador

1. Mostrar la página de propiedades del proyecto. Para obtener más información, consulte [establecer compilador y las propiedades de compilación](../build/working-with-project-properties.md).

1. En el **General** página en el **propiedades de configuración** de conjunto de nodos, el **compatible con tiempo de ejecución de Common Language** propiedad **seguro MSIL Common Language Compatibilidad en tiempo de ejecución (/ CLR: safe)**.

1. En el **avanzadas** página en el **vinculador** de conjunto de nodos, el **tipo de imagen CLR** propiedad **Forzar imagen de IL segura (/ CLRIMAGETYPE: safe)**.

## <a name="removing-native-data-types"></a>Quitar tipos de datos nativos

Dado que los tipos de datos nativos son que no es comprobable, incluso si no se usan realmente, debe quitar todos los archivos de encabezado que contiene los tipos nativos.

> [!NOTE]
> El siguiente procedimiento se aplica a los proyectos de aplicación de Windows Forms (. NET) y aplicación de consola (. NET).

### <a name="to-remove-references-to-native-data-types"></a>Para quitar las referencias a tipos de datos nativos

1. Marque como comentario todo el archivo Stdafx.h.

## <a name="configuring-an-entry-point"></a>Configurar un punto de entrada

Dado que las aplicaciones comprobables no pueden usar las bibliotecas de tiempo de ejecución de C (CRT), no puede depender de CRT para llamar a la función principal como punto de entrada estándar. Esto significa que debe proporcionar explícitamente el nombre de la llamada a función inicialmente al vinculador. (En este caso, Main() se utiliza en lugar de main() o _tmain () para indicar un punto de entrada que no son CRT, pero dado que el punto de entrada se debe especificar explícitamente, este nombre es arbitrario).

> [!NOTE]
> Los procedimientos siguientes se aplican a los proyectos de aplicación de consola (. NET).

#### <a name="to-configure-an-entry-point"></a>Para configurar un punto de entrada

1. Cambiar _tmain () por Main() en el archivo del proyecto .cpp principal.

1. Mostrar la página de propiedades del proyecto. Para obtener más información, consulte [establecer compilador y las propiedades de compilación](../build/working-with-project-properties.md).

1. En el **avanzadas** página bajo la **vinculador** nodo, escriba `Main` como el **punto de entrada** valor de propiedad.

## <a name="see-also"></a>Vea también

- [Código puro y comprobable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)
