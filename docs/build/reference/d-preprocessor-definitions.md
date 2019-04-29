---
title: /D (Definiciones de preprocesador)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.PreprocessorDefinitions
- VC.Project.VCCLCompilerTool.PreprocessorDefinitions
- /d
helpviewer_keywords:
- preprocessor definition symbols
- constants, defining
- macros, compiling
- /D compiler option [C++]
- -D compiler option [C++]
- D compiler option [C++]
ms.assetid: b53fdda7-8da1-474f-8811-ba7cdcc66dba
ms.openlocfilehash: 18bbdb980c63b3c04b432602afb2402c5e2c42e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293971"
---
# <a name="d-preprocessor-definitions"></a>/D (Definiciones de preprocesador)

Define un símbolo de preprocesamiento para un archivo de código fuente.

## <a name="syntax"></a>Sintaxis

```
/Dname[= | # [{string | number}] ]
```

## <a name="remarks"></a>Comentarios

Puede usar este símbolo junto con `#if` o `#ifdef` para compilar condicionalmente archivos de código fuente. La definición del símbolo se mantiene vigente hasta que se vuelve a definir en el código o se anula en el código mediante la directiva `#undef`.

**/D** tiene el mismo efecto que la `#define` la directiva al principio de un archivo de código fuente, salvo que **/D** quita las comillas en la línea de comandos y `#define` conserva.

De forma predeterminada, el valor asociado a un símbolo es 1. Por ejemplo, **/D** `name` es equivalente a **/D**`name`**= 1**. En el ejemplo al final de este artículo, la definición de **prueba** se muestra para imprimir `1`.

Compilación con **/D** `name` **=** hace que el símbolo no tienen ningún valor asociado. Aunque el símbolo aún se pueda utilizar para compilar código condicionalmente, no se evalúa como ningún valor. En el ejemplo, si se compila con **/DTEST =**, se produce un error. Este comportamiento es similar al uso de `#define` con o sin un valor.

Este comando define el símbolo DEBUG en TEST.c:

**PRUEBA DE /DDEBUG CL. C**

Este comando quita todas las apariciones de la palabra clave `__far` en TEST.c:

**CL /D__far=  TEST.C**

El **CL** variable de entorno no se puede establecer en una cadena que contiene el signo igual. Para usar **/D** junto con el **CL** entorno variable, debe especificar el signo de número en lugar del signo igual:

```
SET CL=/DTEST#0
```

Al definir un símbolo de preprocesamiento en el símbolo del sistema, tenga en cuenta las reglas de análisis del shell y del compilador. Por ejemplo, para definir un símbolo de preprocesamiento de signo de porcentaje (%) en el programa, especifique los caracteres de signo de dos por ciento (%) en el símbolo del sistema: Si especifica solo una, se genera un error de análisis.

```
CL /DTEST=%% TEST.C
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. En el panel izquierdo, seleccione **propiedades de configuración**, **C o C++**, **preprocesador**.

1. En el panel derecho, en la columna derecha de la **definiciones del preprocesador** propiedad, abra el menú desplegable y elija **editar**.

1. En el **definiciones del preprocesador** cuadro de diálogo, agregar (uno por línea), modificar o eliminar una o varias definiciones. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>.

## <a name="example"></a>Ejemplo

```
// cpp_D_compiler_option.cpp
// compile with: /DTEST
#include <stdio.h>

int main( )
{
    #ifdef TEST
        printf_s("TEST defined %d\n", TEST);
    #else
        printf_s("TEST not defined\n");
    #endif
}
```

```Output
TEST defined 1
```

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[/U, /u (Anular la definición de símbolos)](u-u-undefine-symbols.md)<br/>
[#undef (directiva) (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br/>
[#define (directiva) (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)
