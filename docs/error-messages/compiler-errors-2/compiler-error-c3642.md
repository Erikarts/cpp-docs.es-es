---
title: Error del compilador C3642
ms.date: 11/04/2016
f1_keywords:
- C3642
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
ms.openlocfilehash: d524c49075c400caa345dd26ed681734ea0cfb94
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385626"
---
# <a name="compiler-error-c3642"></a>Error del compilador C3642

' return_type/args': no se puede llamar a una función con la convención de llamada desde código nativo __clrcall

Una función marcada con el [__clrcall](../../cpp/clrcall.md) convención de llamada no se puede llamar desde código nativo (no administrado).

*return_type/args* es el nombre de la función o el tipo de la `__clrcall` función intenta llamar.  Se utiliza un tipo al que está llamando a través de un puntero de función.

Para llamar a una función administrada desde un contexto nativo, puede agregar una función de "contenedor" que llamará el `__clrcall` función. O bien, puede usar el mecanismo de cálculo de referencias de CLR; vea [Cómo: Calcular las referencias de punteros de función uso de PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md) para obtener más información.

El ejemplo siguiente genera C3642:

```
// C3642.cpp
// compile with: /clr
using namespace System;
struct S {
   void Test(String ^ s) {   // CLR type in signature, implicitly __clrcall
      Console::WriteLine(s);
   }
   void Test2(char * s) {
      Test(gcnew String(s));
   }
};

#pragma unmanaged
int main() {
   S s;
   s.Test("abc");   // C3642
   s.Test2("abc");   // OK
}
```