---
title: Error del compilador C2217
ms.date: 11/04/2016
f1_keywords:
- C2217
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
ms.openlocfilehash: f178f969afa189910c9d23d70226ecc6c15876a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353545"
---
# <a name="compiler-error-c2217"></a>Error del compilador C2217

'atributo1' requiere 'attribute2'

El primer atributo de la función requiere que el segundo atributo.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Interrumpir (`__interrupt`) función declarada como `near`. Interrumpir las funciones deben ser `far`.

1. Interrumpir la función declarada con `__stdcall`, o `__fastcall`. Funciones de interrupción debe usar C++ convenciones de llamada.

## <a name="example"></a>Ejemplo

C2217 también puede producirse si intenta enlazar a un delegado a una función CLR que toma un número variable de argumentos. Si la función también tiene la sobrecarga de matriz param e, use en su lugar. El ejemplo siguiente genera el error C2217.

```
// C2217.cpp
// compile with: /clr
using namespace System;
delegate void MyDel(String^, Object^, Object^, ...);   // C2217
delegate void MyDel2(String ^, array<Object ^> ^);   // OK

int main() {
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);
   array<Object ^ > ^ x = gcnew array<Object ^>(2);
   x[0] = safe_cast<Object^>(0);
   x[1] = safe_cast<Object^>(1);

   // wl("{0}, {1}", 0, 1);
   wl("{0}, {1}", x);
}
```