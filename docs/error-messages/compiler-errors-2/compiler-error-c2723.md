---
title: Error del compilador C2723
ms.date: 11/04/2016
f1_keywords:
- C2723
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
ms.openlocfilehash: bc07a99f12ed0e447427990969e54f7f3d3d3b7f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635400"
---
# <a name="compiler-error-c2723"></a>Error del compilador C2723

'function': el especificador 'specifier' no es válido en la definición de función

El especificador no puede aparecer con una definición de función fuera de una declaración de clase. El especificador `virtual` se puede especificar únicamente en una declaración de función miembro dentro de una declaración de clase.

El ejemplo siguiente genera el error C2723 y muestra cómo corregirlo:

```
// C2723.cpp
struct X {
   virtual void f();
   virtual void g();
};

virtual void X::f() {}   // C2723

// try the following line instead
void X::g() {}
```