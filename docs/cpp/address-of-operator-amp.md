---
title: 'Operador Address-of: &amp;'
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- address-of operator (&)
- '& operator'
- '& operator [C++], address-of operator'
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
ms.openlocfilehash: a03a6100c372e059bd9ef2ddde0558da307923dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385029"
---
# <a name="address-of-operator-amp"></a>Operador Address-of: &amp;

## <a name="syntax"></a>Sintaxis

```
& cast-expression
```

## <a name="remarks"></a>Comentarios

El operador unario address-of (**&**) toma la dirección de su operando. El operando del operador de dirección puede ser un designador de función o un valor l que designe un objeto que no es un campo de bits.

El operador address-of solo se puede aplicar a variables con tipos fundamentales, de estructura, de clase o de unión que se declaren en el nivel de ámbito de archivo o para referencias de matriz de subíndice. En estas expresiones, se puede agregar o quitar de la expresión address-of una expresión constante que no incluya el operador address-of.

Cuando se aplica a funciones o valores L, el resultado de la expresión es un tipo de puntero (un valor R) derivado del tipo del operando. Por ejemplo, si el operando es de tipo **char**, el resultado de la expresión es de tipo puntero a **char**. El operador address-of, aplicado a **const** o **volátil** los objetos, se evalúa como `const type *` o `volatile type *`, donde **tipo** es el tipo del original objeto.

Cuando el operador address-of se aplica a un nombre completo, el resultado depende de si el *nombre calificado* especifica un miembro estático. En ese caso, el resultado es un puntero al tipo especificado en la declaración del miembro. Si el miembro no es estático, el resultado es un puntero al miembro *nombre* de la clase indicada por *qualified-class-name*. (Consulte [expresiones primarias](../cpp/primary-expressions.md) para obtener más información acerca de *qualified-class-name*.) En el fragmento de código siguiente se muestra cómo difiere el resultado, dependiendo de si el miembro es estático:

```cpp
// expre_Address_Of_Operator.cpp
// C2440 expected
class PTM {
public:
    int iValue;
    static float fValue;
};

int main() {
   int   PTM::*piValue = &PTM::iValue;  // OK: non-static
   float PTM::*pfValue = &PTM::fValue;  // C2440 error: static
   float *spfValue     = &PTM::fValue;  // OK
}
```

En este ejemplo, la expresión `&PTM::fValue` proporciona el tipo `float *` en lugar de `float PTM::*`, porque `fValue` es un miembro estático.

La dirección de una función sobrecargada se puede tomar solo cuando está claro a qué versión de la función se hace referencia. Consulte [sobrecarga de funciones](function-overloading.md) para obtener información acerca de cómo obtener la dirección de una determinada función sobrecargada.

Al aplicar el operator address-of a un tipo de referencia se obtiene el mismo resultado que al aplicar el operador al objeto al que se enlaza la referencia. Por ejemplo:

## <a name="example"></a>Ejemplo

```cpp
// expre_Address_Of_Operator2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   double d;        // Define an object of type double.
   double& rd = d;  // Define a reference to the object.

   // Obtain and compare their addresses
   if( &d == &rd )
      cout << "&d equals &rd" << endl;
}
```

## <a name="output"></a>Salida

```Output
&d equals &rd
```

En el ejemplo siguiente se usa el operator address-of para pasar un argumento de puntero a una función:

```cpp
// expre_Address_Of_Operator3.cpp
// compile with: /EHsc
// Demonstrate address-of operator &

#include <iostream>
using namespace std;

// Function argument is pointer to type int
int square( int *n ) {
   return (*n) * (*n);
}

int main() {
   int mynum = 5;
   cout << square( &mynum ) << endl;   // pass address of int
}
```

## <a name="output"></a>Salida

```Output
25
```

## <a name="see-also"></a>Vea también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Declarador de referencia a un valor L: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Operadores de direccionamiento indirecto y address-of](../c-language/indirection-and-address-of-operators.md)