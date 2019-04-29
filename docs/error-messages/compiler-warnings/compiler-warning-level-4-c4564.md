---
title: Advertencia del compilador (nivel 4) C4564
ms.date: 11/04/2016
f1_keywords:
- C4564
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
ms.openlocfilehash: 1948bdec5367fa7943f5a0de4338fd4ecd6c6581
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220512"
---
# <a name="compiler-warning-level-4-c4564"></a>Advertencia del compilador (nivel 4) C4564

el método 'método' de la clase 'class' define el parámetro predeterminado no admitido 'parámetro'

El compilador detectó un método con uno o varios parámetros con valores predeterminados. Se omitirán los valores predeterminados para los parámetros cuando se invoca el método; especificar explícitamente los valores para esos parámetros. Si no especifica valores para esos parámetros explícitamente, el compilador de C++ generará un error.

Dado el siguiente archivo .dll creado con Visual Basic, que permite que los parámetros predeterminados en argumentos de método:

```
' C4564.vb
' compile with: vbc /t:library C4564.vb
Public class TestClass
   Public Sub MyMethod (a as Integer, _
                        Optional c as Integer=1)
   End Sub
End class
```

Y el siguiente ejemplo de C++ que utiliza la DLL creada con Visual Basic,

```
// C4564.cpp
// compile with: /clr /W4 /WX
#using <C4564.dll>

int main() {
   TestClass ^ myx = gcnew TestClass();   // C4564
   myx->MyMethod(9);
   // try the following line instead, to avoid an error
   // myx->MyMethod(9, 1);
}
```