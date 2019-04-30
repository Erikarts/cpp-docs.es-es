---
title: Clases abstractas (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- classes [C++], abstract
- base classes [C++], abstract classes [C++]
- abstract classes [C++]
- derived classes [C++], abstract classes [C++]
ms.assetid: f0c5975b-39de-4d68-9640-6ce57f4632e6
ms.openlocfilehash: a7b41a2cabc2cff2eca24cf50c6c30d5190d39a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385094"
---
# <a name="abstract-classes-c"></a>Clases abstractas (C++)

Las clases abstractas actúan como expresiones de conceptos generales de los que pueden derivarse clases más concretas. No se puede crear un objeto de un tipo de clase abstracta, aunque se pueden utilizar punteros y referencias a los tipos de clase abstracta.

Una clase que contiene al menos una función pura virtual se considera una clase abstracta. Las clases derivadas de la clase abstracta deben implementar la función virtual pura o deben ser también clases abstractas.

Considere el ejemplo presentado en [funciones virtuales](../cpp/virtual-functions.md). El propósito de la clase `Account` es proporcionar funcionalidad general, pero los objetos de tipo `Account` son demasiado generales para resultar útiles. Por consiguiente, `Account` es un buen candidato para una clase abstracta:

```cpp
// deriv_AbstractClasses.cpp
// compile with: /LD
class Account {
public:
   Account( double d );   // Constructor.
   virtual double GetBalance();   // Obtain balance.
   virtual void PrintBalance() = 0;   // Pure virtual function.
private:
    double _balance;
};
```

La única diferencia entre esta declaración y la anterior consiste en que `PrintBalance` se declara con el especificador puro (`= 0`).

## <a name="restrictions-on-abstract-classes"></a>Restricciones para el uso de clases abstractas

No se pueden usar clases abstractas para:

- Variables o datos de miembro

- Tipos de argumento

- Tipos de valor devuelto de función

- Tipos de conversiones explícitas

Otra restricción es que, si el constructor para una clase abstracta llama a una función virtual pura, directa o indirectamente, el resultado está sin definir. Sin embargo, los constructores y destructores para las clases abstractas pueden llamar a otras funciones miembro.

Se pueden definir funciones virtuales puras para clases abstractas, pero solo se pueden llamar directamente mediante la sintaxis:

*abstract-class-name*::*function-name*()

Esto ayuda en el diseño de las jerarquías de clase cuyas clases base incluyen destructores virtuales puros, porque los destructores de clase base siempre se llaman en el proceso de destrucción de un objeto. Considere el ejemplo siguiente:

```cpp
// Declare an abstract base class with a pure virtual destructor.
// deriv_RestrictionsonUsingAbstractClasses.cpp
class base {
public:
    base() {}
    virtual ~base()=0;
};

// Provide a definition for destructor.
base::~base() {}

class derived:public base {
public:
    derived() {}
    ~derived(){}
};

int main() {
    derived *pDerived = new derived;
    delete pDerived;
}
```

Cuando el objeto al que señala `pDerived` se elimina, se llama al destructor de clase `derived` y, después, se llama al destructor de clase `base`. La implementación vacía para la función virtual pura garantiza que al menos existe alguna implementación para la función.

> [!NOTE]
> En el ejemplo anterior, la función virtual pura `base::~base` se llama implícitamente desde `derived::~derived`. También es posible llamar a funciones virtuales puras explícitamente mediante el nombre completo de la función miembro.

## <a name="see-also"></a>Vea también

[Herencia](../cpp/inheritance-cpp.md)