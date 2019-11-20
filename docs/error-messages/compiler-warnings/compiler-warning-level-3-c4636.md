---
title: Advertencia del compilador (nivel 3) C4636
ms.date: 11/04/2016
f1_keywords:
- C4636
helpviewer_keywords:
- C4636
ms.assetid: 59112a0f-850f-41c6-bd84-8ae8dc84706a
ms.openlocfilehash: a1ee63b813c8ef468291eea4575286f40f96ff6a
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189134"
---
# <a name="compiler-warning-level-3-c4636"></a>Advertencia del compilador (nivel 3) C4636

Comentario del documento XML aplicado a 'construcción': la etiqueta requiere que un atributo '' no esté vacío.

Una etiqueta, como `cref`, no tiene un valor.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4636.

```cpp
// C4636.cpp
// compile with: /clr /doc /W3 /c
/// <see cref=''/>
// /// <see cref='System::Exception'/>
ref struct A {   // C4636
   void f(int);
};

// OK
/// <see cref='System::Exception'/>
ref struct B {
   void f(int);
};
```