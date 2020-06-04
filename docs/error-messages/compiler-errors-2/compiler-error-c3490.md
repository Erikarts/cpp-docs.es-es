---
title: Error del compilador C3490
ms.date: 11/04/2016
f1_keywords:
- C3490
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
ms.openlocfilehash: 940eae39222548ec74bda8ccb38e669748ffa74f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738406"
---
# <a name="compiler-error-c3490"></a>Error del compilador C3490

'var' no se puede modificar porque se está accediendo a través de un objeto const.

Una expresión lambda que se declara en un método `const` no puede modificar los datos de miembro no mutable.

### <a name="to-correct-this-error"></a>Para corregir este error

- Elimine el modificador `const` de la declaración del método.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3490 porque modifica la variable miembro `_i` en un método `const` :

```cpp
// C3490a.cpp
// compile with: /c

class C
{
   void f() const
   {
      auto x = [=]() { _i = 20; }; // C3490
   }

   int _i;
};
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se resuelve C3490 quitando el modificador `const` de la declaración del método:

```cpp
// C3490b.cpp
// compile with: /c

class C
{
   void f()
   {
      auto x = [=]() { _i = 20; };
   }

   int _i;
};
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)
