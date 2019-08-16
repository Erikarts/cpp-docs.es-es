---
title: Operadores de puntero a miembro:. * y -&gt;*
ms.date: 11/04/2016
f1_keywords:
- .*
- ->*
helpviewer_keywords:
- expressions [C++], pointer
- pointer-to-member operators [C++]
- .* operator
- expressions [C++], operators
- ->* operator
ms.assetid: 2632be3f-1c81-4523-b56c-982a92a68688
ms.openlocfilehash: 60dad0e3134662957ee21396d330af795e80918e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267668"
---
# <a name="pointer-to-member-operators--and--gt"></a>Operadores de puntero a miembro:. * y -&gt;*

## <a name="syntax"></a>Sintaxis

```
expression .* expression
expression ->* expression
```

## <a name="remarks"></a>Comentarios

Los operadores de puntero a miembro. * y ->\*, devolver el valor de un miembro de clase específica para el objeto especificado en el lado izquierdo de la expresión.  El lado derecho debe especificar un miembro de la clase.  En el siguiente ejemplo se muestra cómo usar estos operadores.

```cpp
// expre_Expressions_with_Pointer_Member_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

class Testpm {
public:
   void m_func1() { cout << "m_func1\n"; }
   int m_num;
};

// Define derived types pmfn and pmd.
// These types are pointers to members m_func1() and
// m_num, respectively.
void (Testpm::*pmfn)() = &Testpm::m_func1;
int Testpm::*pmd = &Testpm::m_num;

int main() {
   Testpm ATestpm;
   Testpm *pTestpm = new Testpm;

// Access the member function
   (ATestpm.*pmfn)();
   (pTestpm->*pmfn)();   // Parentheses required since * binds
                        // less tightly than the function call.

// Access the member data
   ATestpm.*pmd = 1;
   pTestpm->*pmd = 2;

   cout  << ATestpm.*pmd << endl
         << pTestpm->*pmd << endl;
   delete pTestpm;
}
```

## <a name="output"></a>Salida

```Output
m_func1
m_func1
1
2
```

En el ejemplo anterior, se utiliza un puntero a un miembro, `pmfn`, para invocar la función miembro `m_func1`. Se usa otro puntero a miembro, `pmd`, para tener acceso al miembro `m_num`.

El operador binario .* combina su primer operando, que debe ser un objeto de tipo de clase, con su segundo operando, que debe ser un tipo de puntero a miembro.

El operador binario -> * combina su primer operando, que debe ser un puntero a un objeto de tipo de clase, con su segundo operando, que debe ser un tipo de puntero a miembro.

En una expresión que contenga el operador .*, el primer operando debe ser del tipo de clase de, y ser accesible para, el puntero a miembro especificado en el segundo operando, o bien de un tipo accesible derivado inequívocamente de y accesible para esa clase.

En una expresión que contiene el-> * (operador), el primer operando debe ser del tipo "puntero al tipo de clase" del tipo especificado en el segundo operando, o debe ser de un tipo derivado inequívocamente de esa clase.

## <a name="example"></a>Ejemplo

Considere las clases y el fragmento de programa siguientes:

```cpp
// expre_Expressions_with_Pointer_Member_Operators2.cpp
// C2440 expected
class BaseClass {
public:
   BaseClass(); // Base class constructor.
   void Func1();
};

// Declare a pointer to member function Func1.
void (BaseClass::*pmfnFunc1)() = &BaseClass::Func1;

class Derived : public BaseClass {
public:
   Derived();  // Derived class constructor.
   void Func2();
};

// Declare a pointer to member function Func2.
void (Derived::*pmfnFunc2)() = &Derived::Func2;

int main() {
   BaseClass ABase;
   Derived ADerived;

   (ABase.*pmfnFunc1)();   // OK: defined for BaseClass.
   (ABase.*pmfnFunc2)();   // Error: cannot use base class to
                           // access pointers to members of
                           // derived classes.

   (ADerived.*pmfnFunc1)();   // OK: Derived is unambiguously
                              // derived from BaseClass.
   (ADerived.*pmfnFunc2)();   // OK: defined for Derived.
}
```

El resultado de la. * o ->\* operadores de puntero a miembro es un objeto o función del tipo especificado en la declaración del puntero a miembro. Por lo tanto, en el ejemplo anterior, el resultado de la expresión `ADerived.*pmfnFunc1()` es un puntero a una función que devuelve void. El resultado es un valor L si el segundo operando es un valor L.

> [!NOTE]
>  Si el resultado de uno de los operadores de puntero a miembro es una función, el resultado se puede utilizar como operando al operador de llamada a función.

## <a name="see-also"></a>Vea también

[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)