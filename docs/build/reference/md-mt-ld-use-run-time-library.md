---
title: /MD,-MT,-LD (usar la biblioteca en tiempo de ejecución)
ms.date: 07/17/2019
f1_keywords:
- /ld
- /mt
- VC.Project.VCCLWCECompilerTool.RuntimeLibrary
- VC.Project.VCCLCompilerTool.RuntimeLibrary
- /md
- /ml
helpviewer_keywords:
- /MT compiler option [C++]
- -MD compiler option [C++]
- threading [C++], multithread compiler option
- MSVCRTD.lib
- MSVCRT.lib
- LIBCMT.lib
- MD compiler option [C++]
- /MD compiler option [C++]
- MT compiler option [C++]
- LD compiler option [C++]
- MDd compiler option [C++]
- -MDd compiler option [C++]
- LIBCD.lib
- -MTd compiler option [C++]
- MTd compiler option [C++]
- /MTd compiler option [C++]
- -LD compiler option [C++]
- /MDd compiler option [C++]
- multithread compiler option
- _STATIC_CPPLIB symbol
- LIBC.lib
- /LD compiler option [C++]
- DLLs [C++], compiler options
- LIBCMTD.lib
- -MT compiler option [C++]
ms.assetid: cf7ed652-dc3a-49b3-aab9-ad60e5395579
ms.openlocfilehash: a66677ebbef984e9a4c8190f184ca3a9126a7b83
ms.sourcegitcommit: d4da3693f83a24f840e320e35c24a4a07cae68e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/18/2020
ms.locfileid: "83550763"
---
# <a name="md-mt-ld-use-run-time-library"></a>/MD, /MT, /LD (utilizar la biblioteca en tiempo de ejecución)

Indica si un módulo multiproceso es un archivo DLL y especifica versiones comerciales o de depuración de la biblioteca en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```
/MD[d]
/MT[d]
/LD[d]
```

## <a name="remarks"></a>Observaciones

|Opción|Descripción|
|------------|-----------------|
|**/MD**|Hace que la aplicación use la versión específica para multiproceso y la versión específica para DLL de la biblioteca en tiempo de ejecución. Define `_MT` y `_DLL` y hace que el compilador sitúe el nombre de la biblioteca MSVCRT.lib en el archivo .obj.<br /><br /> Las aplicaciones compiladas con esta opción se vinculan estáticamente con MSVCRT.lib. Esta biblioteca proporciona un nivel de código que permite al vinculador resolver referencias externas. El código de trabajo real se encuentra en MSVCR*versionNumber*. DLL, que debe estar disponible en tiempo de ejecución para las aplicaciones vinculadas con MSVCRT. lib.|
|**/MDd**|Define `_DEBUG`, `_MT` y `_DLL` y hace que la aplicación use la versión de depuración multiproceso y la versión específica para DLL de la biblioteca en tiempo de ejecución. También hace que el compilador coloque el nombre de la biblioteca MSVCRTD.lib en el archivo .obj.|
|**/MT**|Hace que la aplicación use la versión estática multiproceso de la biblioteca en tiempo de ejecución. Define `_MT` y hace que el compilador sitúe el nombre de biblioteca LIBCMT.lib en el archivo .obj para que el vinculador utilice LIBCMT.lib al resolver símbolos externos.|
|**/MTd**|Define `_DEBUG` y `_MT`. Esta opción también hace que el compilador coloque el nombre de la biblioteca LIBCMTD.lib en el archivo .obj, así el vinculador usará LIBCMTD.lib para resolver los símbolos externos.|
|**/LD**|Crea un archivo DLL.<br /><br /> Pasa la opción **/dll** al enlazador. El vinculador busca una función `DllMain`, aunque esta función no es obligatoria. Si no escribe una función `DllMain`, el vinculador inserta una función `DllMain` que devuelve TRUE.<br /><br /> Vincula el código de inicio de DLL.<br /><br /> Crea una biblioteca de importación (.lib) si no se especifica un archivo de exportación (.exp) en la línea de comandos. Vincula la biblioteca de importación con aplicaciones que llaman al archivo DLL.<br /><br /> Interpreta [/fe (nombre del archivo exe)](fe-name-exe-file.md) como nombre de un archivo dll en lugar de un archivo. exe. De forma predeterminada, el nombre del programa se convierte en *basename*. dll en lugar de en *basename*. exe.<br /><br /> Implica **/MT** a menos que se especifique explícitamente **/MD**.|
|**/LDd**|Crea un archivo DLL de depuración. Define `_MT` y `_DEBUG`.|

Para obtener más información sobre las bibliotecas en tiempo de ejecución de C y las bibliotecas que se utilizan al compilar con [/CLR (compilación de Common Language Runtime)](clr-common-language-runtime-compilation.md), vea características de la [biblioteca CRT](../../c-runtime-library/crt-library-features.md).

Todos los módulos pasados a una invocación determinada del enlazador deben haberse compilado con la misma opción del compilador de la biblioteca en tiempo de ejecución (**/MD**, **/MT**, **/LD**).

Para obtener más información sobre cómo usar las versiones de depuración de las bibliotecas en tiempo de ejecución, vea [referencia de la biblioteca en tiempo de ejecución de C](../../c-runtime-library/c-run-time-library-reference.md).

Para obtener más información sobre los archivos dll, vea [crear archivos dll de C/C++ en Visual Studio](../dlls-in-visual-cpp.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la **Configuration Properties**página de propiedades de generación de código de  >  **C/C++ y**propiedades de configuración  >  **Code Generation** .

1. Modifique la propiedad **biblioteca en tiempo de ejecución** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
