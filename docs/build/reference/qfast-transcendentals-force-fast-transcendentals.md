---
title: /Qfast_transcendentals (Force Fast Transcendentals)
ms.date: 11/04/2016
f1_keywords:
- /Qfast_transcendentals
helpviewer_keywords:
- /Qfast_transcendentals
- Force Fast Transcendentals
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
ms.openlocfilehash: 512e658cf546e77bff6d58465932d2f830541521
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666133"
---
# <a name="qfasttranscendentals-force-fast-transcendentals"></a>/Qfast_transcendentals (Force Fast Transcendentals)

Genera código alineado para las funciones transcendentales.

## <a name="syntax"></a>Sintaxis

```
/Qfast_transcendentals
```

## <a name="remarks"></a>Comentarios

Esta opción del compilador fuerza las funciones transcendentales a convertirse en código insertado para mejorar la velocidad de ejecución. Esta opción tiene un efecto solo cuando se emparejan con **/fp: excepto** o **/fp: precisa**. Generar código en línea para las funciones transcendentales ya es el comportamiento predeterminado en **/fp: Fast**.

Esta opción no es compatible con **/fp: strict**. Consulte [/fp (Especificar comportamiento de punto flotante)](../../build/reference/fp-specify-floating-point-behavior.md) para obtener más información acerca de las opciones del compilador de punto de flotante.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/Q (Opciones) (Operaciones de bajo nivel)](../../build/reference/q-options-low-level-operations.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)