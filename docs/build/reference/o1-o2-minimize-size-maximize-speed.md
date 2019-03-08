---
title: /O1, /O2 (Minimizar tamaño, maximizar velocidad)
ms.date: 09/25/2017
f1_keywords:
- /o2
- /o1
helpviewer_keywords:
- maximize speed compiler option [C++]
- minimize size compiler option [C++]
- -O2 compiler option [C++]
- fast code
- small code
- O2 compiler option [C++]
- /O2 compiler option [C++]
- -O1 compiler option [C++]
- O1 compiler option [C++]
- /O1 compiler option [C++]
ms.assetid: 2d1423f5-53d9-44da-8908-b33a351656c2
ms.openlocfilehash: 8074d4308974673c18dffb45ae580d43f3a377b3
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415555"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1, /O2 (Minimizar tamaño, maximizar velocidad)

Selecciona un conjunto predefinido de opciones que afectan al tamaño y la velocidad del código generado.

## <a name="syntax"></a>Sintaxis

> / / O2 O1

## <a name="remarks"></a>Comentarios

El **/O1** y **/O2** opciones del compilador son una forma rápida para establecer varias opciones de optimización específicas a la vez. El **/O1** opción establece las opciones de optimización individual que crea el código más pequeño en la mayoría de los casos. El **/O2** opción establece las opciones que crea el código más rápido en la mayoría de los casos. El **/O2** es la opción predeterminada para las compilaciones de versión. Esta tabla muestran las opciones específicas que se establezcan en **/O1** y **/O2**:

|Opción|Equivalente a|
|------------|-------------------|
|**/ O1** (minimizar tamaño)|[/Og](../../build/reference/og-global-optimizations.md) [/Os](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/Ob2](../../build/reference/ob-inline-function-expansion.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|
|**/ O2** (maximizar velocidad)|[/Og](../../build/reference/og-global-optimizations.md) [/Oi](../../build/reference/oi-generate-intrinsic-functions.md) [/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/Ob2](../../build/reference/ob-inline-function-expansion.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|

**/ O1** y **/O2** son mutuamente excluyentes.

> [!NOTE]
> **x86 específico** estas opciones implican el uso de la omisión de puntero de marco ([/Oy](../../build/reference/oy-frame-pointer-omission.md)) opción.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. En **propiedades de configuración**, abra **C o C++** y, a continuación, elija el **optimización** página de propiedades.

1. Modificar el **optimización** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Vea también

[/O (Opciones) (Optimizar código)](../../build/reference/o-options-optimize-code.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[/EH (Modelo de control de excepciones)](../../build/reference/eh-exception-handling-model.md)
