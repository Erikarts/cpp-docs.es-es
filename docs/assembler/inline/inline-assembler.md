---
title: Ensamblador insertado
ms.date: 08/30/2018
helpviewer_keywords:
- assembler [C++]
- assembler [C++], inline
- assembly language [C++], inline
- inline assembler [C++]
- inline assembly [C++]
ms.assetid: 7e13f18f-3628-4306-8b81-4a6d09c043fe
ms.openlocfilehash: d36c4d83a1fbf5d7ad718a7caf1dccb8f6745676
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169376"
---
# <a name="inline-assembler"></a>Ensamblador insertado

**Específicos de Microsoft**

El lenguaje de ensamblado sirve para muchos propósitos, como mejorar la velocidad del programa, reducir la memoria necesaria y supervisar el hardware. Puede utilizar el ensamblador alineado para incrustar instrucciones de lenguaje de ensamblado directamente en los programas de origen C y C++ sin realizar pasos adicionales de ensamblado y vínculo. El ensamblador alineado se compila en el compilador, por lo que no es necesario un ensamblador independiente como Microsoft Macro Assembler (MASM).

> [!NOTE]
>  Los programas con código ensamblador alineado no son totalmente portables a otras plataformas de hardware. Si está diseñando para la portabilidad, evite utilizar el ensamblador alineado.

El ensamblado alineado no se admite en los procesadores ARM y x64.  En los temas siguientes se explica cómo usar el ensamblador alineado de Visual C/C++ con procesadores x86:

- [Información general del ensamblador insertado](../../assembler/inline/inline-assembler-overview.md)

- [Ventajas del ensamblador insertado](../../assembler/inline/advantages-of-inline-assembly.md)

- [__asm](../../assembler/inline/asm.md)

- [Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)

- [Uso de C o C++ en bloques __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)

- [Uso y conservación de registros en un ensamblado insertado](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md)

- [Salto a etiquetas en un ensamblado insertado](../../assembler/inline/jumping-to-labels-in-inline-assembly.md)

- [Llamada a funciones C en el ensamblado insertado](../../assembler/inline/calling-c-functions-in-inline-assembly.md)

- [Llamada a funciones C++ en el ensamblado insertado](../../assembler/inline/calling-cpp-functions-in-inline-assembly.md)

- [Definición de bloques __asm como macros de C](../../assembler/inline/defining-asm-blocks-as-c-macros.md)

- [Optimización de un ensamblado insertado](../../assembler/inline/optimizing-inline-assembly.md)

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Intrínsecos del compilador y lenguaje ensamblador](../../intrinsics/compiler-intrinsics-and-assembly-language.md)<br/>
[Referencia del lenguaje C++](../../cpp/cpp-language-reference.md)<br/>
