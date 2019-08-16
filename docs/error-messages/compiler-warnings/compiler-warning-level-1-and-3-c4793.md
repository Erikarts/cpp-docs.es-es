---
title: Advertencia del compilador (niveles 1 y 3) C4793
ms.date: 11/04/2016
f1_keywords:
- C4793
helpviewer_keywords:
- C6634
- C6635
- C6640
- C6630
- C6639
- C6636
- C6638
- C6631
- C6637
- C4793
ms.assetid: 819ada53-1d9c-49b8-a629-baf8c12314e6
ms.openlocfilehash: e7ca3b10e09b0d6818fbc7f5607ebc9c95c7f15c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280547"
---
# <a name="compiler-warning-level-1-and-3-c4793"></a>Advertencia del compilador (niveles 1 y 3) C4793

> '*función*': función se compila como código nativo: '*motivo*'

## <a name="remarks"></a>Comentarios

El compilador no puede compilar *función* en código administrado, aunque el [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) se especificó la opción del compilador. En su lugar, el compilador emite la advertencia C4793 y un mensaje explicativo a continuación y, a continuación, compila *función* en código nativo. El mensaje de continuación contiene la *motivo* texto que explica por qué *función* no se puede compilar para `MSIL`.

Se trata de una advertencia de nivel 1 al especificar el **/CLR: pure** opción del compilador.  El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

En la tabla siguiente se enumera todos los mensajes de continuación posibles.

|Mensaje de motivo|Comentarios|
|--------------------|-------------|
|Tipos de datos alineados no se admiten en código administrado|El CLR debe ser capaz de asignar los datos según sea necesario, que podría no ser posible si los datos están alineados con declaraciones como [__m128](../../cpp/m128.md) o [alinear](../../cpp/align-cpp.md).|
|Las funciones que usan '__ImageBase' no se admiten en código administrado|`__ImageBase` es un símbolo de vinculador especial que se utiliza normalmente solo mediante código nativo de bajo nivel para cargar un archivo DLL.|
|varargs no son compatibles con el ' / clr' opción del compilador|Las funciones nativas no pueden llamar a funciones administradas que tienen [listas de argumentos variables](../../cpp/functions-with-variable-argument-lists-cpp.md) (varargs) porque las funciones tienen requisitos de diseño de pila diferente. Sin embargo, si especifica la **/CLR: pure** opción del compilador, los argumentos de variable se admiten listas porque el ensamblado puede contener solo funciones administradas. Para obtener más información, consulte [código puro y comprobable (C++ / c++ / CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).|
|El CLR de 64 bits no admite datos declarados con el modificador __ptr32|Un puntero debe ser el mismo tamaño que un puntero nativo en la plataforma actual. Para obtener más información, consulte [__ptr32, \__ptr64](../../cpp/ptr32-ptr64.md).|
|El CLR de 32 bits no admite datos declarados con el modificador __ptr64|Un puntero debe ser el mismo tamaño que un puntero nativo en la plataforma actual. Para obtener más información, consulte [__ptr32, \__ptr64](../../cpp/ptr32-ptr64.md).|
|No se admiten uno o varios intrínsecos en código administrado|El nombre de la función intrínseca no está disponible en el momento en que se emite el mensaje. Sin embargo, un valor intrínseco que hace que este mensaje normalmente representa una instrucción máquina de bajo nivel.|
|Ensamblado nativo alineado ('__asm') no se admite en código administrado|[Código de ensamblado alineado](../../assembler/inline/asm.md) puede contener arbitraria de código nativa, que no se pueden administrar.|
|Un código thunk de función virtual de __clrcall no se debe compilar como nativos|No[__clrcall](../../cpp/clrcall.md) código thunk de función virtual debe usar una dirección no administrada.|
|Una función mediante '_setjmp' se debe compilar como nativos|El CLR debe ser capaz de controlar la ejecución del programa. Sin embargo, el [setjmp](../../cpp/using-setjmp-longjmp.md) función omite la ejecución de programa normal por guardar y restaurar la información de bajo nivel, como registros y el estado de ejecución.|

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4793.

```cpp
// C4793.cpp
// compile with: /c /clr /W3
// processor: x86
int asmfunc(void) {   // C4793, compiled as unmanaged, native code
   __asm {
      mov eax, 0
   }
}
```

```Output
warning C4793: 'asmfunc' : function is compiled as native code:
        Inline native assembly ('__asm') is not supported in managed code
```

El ejemplo siguiente genera C4793.

```cpp
// C4793_b.cpp
// compile with: /c /clr /W3
#include <setjmp.h>
jmp_buf test_buf;

void f() {
   setjmp(test_buf);   // C4793 warning
}
```

```Output
warning C4793: 'f' : function is compiled as native code:
        A function using '_setjmp' must be compiled as native
```