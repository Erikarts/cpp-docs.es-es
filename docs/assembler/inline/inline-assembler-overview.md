---
title: Información general de ensamblador alineado
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembler
- __asm keyword [C++], invoking inline assembler
- invoking inline assembler
- inline assembly, inline assembler
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
ms.openlocfilehash: 6233e07e115c21a0a173f094079dc9c1753533b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169402"
---
# <a name="inline-assembler-overview"></a>Información general de ensamblador alineado

**Específicos de Microsoft**

El ensamblador alineado permite incrustar instrucciones de lenguaje de ensamblado directamente en los programas de origen de C y C++ sin realizar pasos adicionales de ensamblado y vinculación. El ensamblador alineado se compila en el compilador; por lo tanto, no se necesita un ensamblador independiente como Microsoft Macro Assembler (MASM).

Dado que el ensamblador alineado no requiere pasos de ensamblado y vínculo independientes y de vínculo, es más aconsejable que un ensamblador independiente. El código de ensamblado alineado puede utilizar cualquier nombre de variable o de función de C o C++ que esté en el ámbito, por lo que resulta fácil integrarlo con el código C o C++ del programa. Y, dado que el código de ensamblado se puede combinar con instrucciones de C o C++, puede realizar tareas complicadas o imposibles solo en C o C++.

La palabra clave [__asm](../../assembler/inline/asm.md) invoca el ensamblador alineado y puede aparecer siempre que una instrucción C++ C o sea legal. No puede aparecer por sí sola. Debe ir seguida de una instrucción de ensamblado, un grupo de instrucciones entre llaves o, como mínimo, un par de llaves vacío. El término "bloque `__asm`" aquí hace referencia a cualquier instrucción o grupo de instrucciones, incluido o no entre llaves.

El código siguiente es un bloque `__asm` simple incluido entre llaves. (El código es una secuencia de prólogo de función personalizada).

```cpp
// asm_overview.cpp
// processor: x86
void __declspec(naked) main()
{
    // Naked functions must provide their own prolog...
    __asm {
        push ebp
        mov ebp, esp
        sub esp, __LOCAL_SIZE
    }

    // ... and epilog
    __asm {
        pop ebp
        ret
    }
}
```

Como alternativa, puede colocar `__asm` delante de cada instrucción de ensamblado:

```cpp
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

Dado que la palabra clave `__asm` es un separador de la instrucción, también puede colocar las instrucciones de ensamblado en la misma línea:

```cpp
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Ensamblador insertado](../../assembler/inline/inline-assembler.md)<br/>
