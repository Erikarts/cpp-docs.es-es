---
title: /arch (x64)
ms.date: 11/04/2016
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
ms.openlocfilehash: ac34a18efbf31787889cc4fe31ebd3d8473df0eb
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421866"
---
# <a name="arch-x64"></a>/arch (x64)

Especifica la arquitectura para la generación de código en x64. Consulte también [/arch (x86)](../../build/reference/arch-x86.md) y [/arch (ARM)](../../build/reference/arch-arm.md).

## <a name="syntax"></a>Sintaxis

```
/arch:[AVX|AVX2]
```

## <a name="arguments"></a>Argumentos

**/arch:AVX**<br/>
Habilita el uso de instrucciones de Extensiones de vector avanzadas de Intel.

**/arch:AVX2**<br/>
Habilita el uso de instrucciones de Extensiones de vector avanzadas 2 (AVX2) de Intel.

## <a name="remarks"></a>Comentarios

**/ arch** solo afecta a la generación de código para las funciones nativas. Cuando usas [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) para compilar, **/arch** no tiene ningún efecto sobre la generación de código para las funciones administradas.

El `__AVX__` se define el símbolo de preprocesador cuando la **/arch: AVX** se especificó la opción del compilador. El `__AVX2__` se define el símbolo de preprocesador cuando la **/arch: avx2** se especificó la opción del compilador. Para obtener más información, consulta [Predefined Macros](../../preprocessor/predefined-macros.md). El **/arch: avx2** opción se introdujo en Visual Studio 2013 Update 2, versión 12.0.34567.1.

### <a name="to-set-the-archavx-or-archavx2-compiler-option-in-visual-studio"></a>Para establecer la opción del compilador /arch:AVX o /arch:AVX2 en Visual Studio

1. Abra el **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración**, **C o C++** carpeta.

1. Seleccione el **generación de código** página de propiedades.

1. En el **Habilitar conjunto de instrucciones mejorado** lista desplegable, seleccione **extensiones de Vector avanzadas (/ arch: AVX)** o **extensiones de Vector avanzadas 2 (/ arch: AVX2)**.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Vea también

[/arch (Arquitectura de CPU mínima)](../../build/reference/arch-minimum-cpu-architecture.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
