---
title: 'Tutorial: Compilar un programa de C++/CX en la línea de comandos'
ms.date: 09/24/2018
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: 6acfa707ac64a647e838fd1dbcd5564c79faa1a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515146"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>Tutorial: Compilar un programa de C++/CX en la línea de comandos

Puede crear programas de Visual C++ destinados a Windows Runtime y compilarlos en la línea de comandos. Visual C++ admite las extensiones de componentes de Visual C++ (C++/CX), con tipos y operadores adicionales para tener como destino el modelo de programación de Windows Runtime. Puede usar C++ / c++ / CX para crear aplicaciones para escritorio de la plataforma Universal de Windows (UWP), Windows Phone 8.1 y Windows. Para obtener más información, consulte [recorrido por c++ A c++ / CX](https://msdn.microsoft.com/magazine/dn166929.aspx) y [extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md).

En este tutorial, utilizará un editor de texto para crear un programa básico de C++/CX y, a continuación, lo compilará en la línea de comandos. (Puede usar su propio programa de C++/CX en lugar de escribir el que se muestra o usar un código de ejemplo de C++/CX de otro artículo de ayuda. Esta técnica es útil para compilar y probar módulos pequeños que no tienen ningún elemento de interfaz de usuario).

> [!NOTE]
> También puede usar el IDE de Visual Studio para compilar programas de C++/CX. Dado que el IDE de incluye el diseño, depuración, emulación y compatibilidad con la implementación que no está disponible en la línea de comandos, se recomienda que use el IDE para compilar aplicaciones de plataforma Universal de Windows (UWP). Para obtener más información, consulte [crear una aplicación para UWP en C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

## <a name="prerequisites"></a>Requisitos previos

Comprender los aspectos básicos del lenguaje C++.

## <a name="compiling-a-ccx-program"></a>Compilación de un programa de C++/CX

Para habilitar la compilación de C / c++ / CX, debe usar el [/ZW](../build/reference/zw-windows-runtime-compilation.md) opción del compilador. El compilador de Visual C++ generará un archivo .exe destinado a Windows Runtime y vinculará las bibliotecas necesarias.

#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>Para compilar una aplicación de C++/CX en la línea de comandos

1. Abra un **símbolo** ventana. (En el **iniciar** ventana abierta **aplicaciones**. Abra el **Visual Studio Tools** carpeta en su versión de Visual Studio y, a continuación, elija el **símbolo del sistema para desarrolladores** acceso directo.) Para obtener más información sobre cómo abrir una ventana del símbolo del sistema para desarrolladores, consulte [código de C o C++ de compilación en la línea de comandos](../build/building-on-the-command-line.md).

   Puede que se requieran credenciales de administrador para compilar el código correctamente,en función del sistema operativo y de la configuración del equipo. Para ejecutar la ventana de símbolo del sistema como administrador, abra el menú contextual de **símbolo** y, a continuación, elija **ejecutar como administrador**.

1. En el símbolo del sistema, escriba **notepad basiccx.cpp**.

   Elija **Sí** cuando se le pedirá que cree un archivo.

1. En el Bloc de notas, escriba estas líneas:

    ```cpp
    using namespace Platform;

    int main(Platform::Array<Platform::String^>^ args)
    {
        Platform::Details::Console::WriteLine("This is a C++/CX program.");
    }
    ```

1. En la barra de menús, elija **archivo** > **guardar**.

   Ha creado un archivo de código fuente de Visual C++ que usa el Runtime de Windows [espacio de nombres Platform](../cppcx/platform-namespace-c-cx.md) espacio de nombres.

1. En el símbolo del sistema, escriba **cl /EHsc /ZW basiccx.cpp /link/SUBSYSTEM: Console**. El compilador cl.exe compila el código fuente en un archivo .obj y, después, ejecuta el enlazador para generar un programa ejecutable llamado basiccx.exe. (El [/EHsc](../build/reference/eh-exception-handling-model.md) opción del compilador especifica el modelo de control de excepciones de C++ y el [/link](../build/reference/link-pass-options-to-linker.md) marca especifica una aplicación de consola.)

1. Para ejecutar el programa basiccx.exe, en el símbolo del sistema, escriba **basiccx**.

   El programa mostrará este texto y se cerrará:

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Compilación de programas de C/C++](../build/building-c-cpp-programs.md)<br/>
[Opciones del compilador](../build/reference/compiler-options.md)