---
title: /cgthreads (Subprocesos de generación de código)
ms.date: 11/04/2016
f1_keywords:
- /cgthreads
helpviewer_keywords:
- /cgthreads compiler option (C++)
- -cgthreads compiler option (C++)
- cgthreads compiler option (C++)
- cgthreads
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
ms.openlocfilehash: df353eb255c731478863ed6088cafa1cc38053fb
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807434"
---
# <a name="cgthreads-code-generation-threads"></a>/cgthreads (Subprocesos de generación de código)

Establece el número de subprocesos de cl.exe que se deben usar para la optimización y la generación de código.

## <a name="syntax"></a>Sintaxis

```
/cgthreads[1-8]
```

## <a name="arguments"></a>Argumentos

*number*<br/>
El número máximo de subprocesos que debe usar cl.exe, en un intervalo de 1 a 8.

## <a name="remarks"></a>Comentarios

El **/cgthreads** opción especifica el número máximo de subprocesos cl.exe utiliza en paralelo para la optimización y el código de las fases de generación de la compilación. Tenga en cuenta que no puede haber ningún espacio entre **/cgthreads** y `number` argumento. De forma predeterminada, cl.exe utiliza cuatro subprocesos, como si **/cgthreads4** se han especificado. Si hay más núcleos de procesador disponibles, al aumentar el valor `number`, se pueden mejorar los tiempos de compilación. Esta opción es especialmente útil cuando se combina con [/GL (Whole Program Optimization)](gl-whole-program-optimization.md).

Se pueden especificar varios niveles de paralelismo para una compilación. El modificador de msbuild.exe **/maxcpucount** especifica el número de procesos de MSBuild que se pueden ejecutar en paralelo. El [/MP (compilar con varios procesos)](mp-build-with-multiple-processes.md) marca de compilador especifica el número de procesos de cl.exe que compilan simultáneamente los archivos de origen. El **/cgthreads** opción especifica el número de subprocesos utilizados por cada proceso de cl.exe. Dado que el procesador no puede ejecutar al mismo tiempo más subprocesos que núcleos de procesador hay, no resulta útil especificar valores mayores en todas estas opciones a la vez, y puede ser contraproducente. Para obtener más información sobre cómo compilar proyectos en paralelo, vea [compilar varios proyectos en paralelo](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración**, **C o C++** carpeta.

1. Seleccione el **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad incluir **/cgthreads**`N`, donde `N` es un valor comprendido entre 1 y 8 y, a continuación, seleccione **Aceptar**.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
