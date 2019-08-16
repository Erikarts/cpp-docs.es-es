---
title: __restrict
ms.date: 10/10/2018
f1_keywords:
- __restrict_cpp
- __restrict
- _restrict
helpviewer_keywords:
- __restrict keyword [C++]
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
ms.openlocfilehash: 76cdf9424e6eab33a3a92b3f98d9c2b0b04ff667
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183757"
---
# <a name="restrict"></a>__restrict

Al igual que el **__declspec ( [restringir](../cpp/restrict.md) )** modificador, el **__restrict** palabra clave indica que un símbolo no tiene un alias en el ámbito actual. El **__restrict** palabra clave difiere el `__declspec ( restrict )` modificador de las maneras siguientes:

- El **__restrict** palabra clave sólo es válido en variables, y `__declspec ( restrict )` solo es válido en declaraciones de función y definiciones.

- **__restrict** es similar a **restringir** de la especificación C99, pero **__restrict** puede usarse en C++ o programas de C.

- Cuando **__restrict** es utilizado, el compilador no propagará la propiedad sin alias de una variable. Es decir, si asigna un **__restrict** variable para que no es **__restrict** variable, el compilador permitirá la variable para tener un alias que no es __restrict. Esto es diferente del comportamiento de la **restringir** palabra clave de la especificación C99.

Normalmente, si se modifica el comportamiento de una función completa, es mejor usar `__declspec ( restrict )` que la palabra clave.

Para ofrecer compatibilidad con versiones anteriores, **_restrict** es un sinónimo de **__restrict** a menos que la opción de compilador [/Za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) es especificado.

En Visual Studio 2015 y versiones posteriores, **__restrict** puede usarse en C++ referencias.

> [!NOTE]
>  Cuando se utiliza en una variable que tiene también la [volátil](../cpp/volatile-cpp.md) palabra clave, **volátil** tendrá prioridad.

## <a name="example"></a>Ejemplo

```cpp
// __restrict_keyword.c
// compile with: /LD
// In the following function, declare a and b as disjoint arrays
// but do not have same assurance for c and d.
void sum2(int n, int * __restrict a, int * __restrict b,
          int * c, int * d) {
   int i;
   for (i = 0; i < n; i++) {
      a[i] = b[i] + c[i];
      c[i] = b[i] + d[i];
    }
}

// By marking union members as __restrict, tell compiler that
// only z.x or z.y will be accessed in any given scope.
union z {
   int * __restrict x;
   double * __restrict y;
};
```

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)