---
title: Comportamiento no estándar
ms.date: 05/06/2019
helpviewer_keywords:
- compatibility and compliance, nonstandard behavior
- Microsoft-specific, compiler behavior
- nonstandard behavior, compliance and compatibility
ms.assetid: a57dea27-dc79-4f64-8a83-017e84841773
ms.openlocfilehash: d3bb4ca843833cfe9e027f694f25c989895487bb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161040"
---
# <a name="nonstandard-behavior"></a>Comportamiento no estándar

En las secciones siguientes se enumeran algunos de los lugares en los C++ que la implementación de Microsoft C++ de no cumple con el estándar. Los números de sección que se indican a continuación se refieren a los números de sección del estándar de C++ 11 (ISO/IEC 14882:2011(E)).

La lista de límites del compilador que difieren C++ de los definidos en el estándar se proporciona en los [límites del compilador](../cpp/compiler-limits.md).

## <a name="covariant-return-types"></a>Tipos de valor devueltos de covariante

Las clases base virtuales no se admiten como tipos de valor devueltos de covariante cuando la función virtual tiene un número variable de argumentos. Esto no cumple con el párrafo 7 de la sección 10.3 de la especificación ISO de C++. El ejemplo siguiente no se compila y se produce el error del compilador [C2688](../error-messages/compiler-errors-2/compiler-error-c2688.md)

```cpp
// CovariantReturn.cpp
class A
{
   virtual A* f(int c, ...);   // remove ...
};

class B : virtual A
{
   B* f(int c, ...);   // C2688 remove ...
};
```

## <a name="binding-nondependent-names-in-templates"></a>Enlazar nombres no dependientes en plantillas

El compilador de Microsoft C++ no admite actualmente el enlace de nombres no dependientes cuando se analiza inicialmente una plantilla. Esto no cumple con la sección 14.6.3 de la especificación ISO de C++. Esto puede hacer que se vean las sobrecargas declaradas después de la plantilla (pero antes de que se creen instancias de la plantilla).

```cpp
#include <iostream>
using namespace std;

namespace N {
   void f(int) { cout << "f(int)" << endl;}
}

template <class T> void g(T) {
    N::f('a');   // calls f(char), should call f(int)
}

namespace N {
    void f(char) { cout << "f(char)" << endl;}
}

int main() {
    g('c');
}
// Output: f(char)
```

## <a name="function-exception-specifiers"></a>Especificadores de excepciones de funciones

Los especificadores de excepciones de funciones distintos de `throw()` se analizan pero no se usan. Esto no cumple con la sección 15.4 de la especificación ISO de C++. Por ejemplo:

```cpp
void f() throw(int); // parsed but not used
void g() throw();    // parsed and used
```

Para obtener más información sobre las especificaciones de excepción, vea [Especificaciones de excepciones](../cpp/exception-specifications-throw-cpp.md).

## <a name="char_traitseof"></a>char_traits::eof()

Los C++ Estados estándar que [char_traits:: EOF](../standard-library/char-traits-struct.md#eof) no deben corresponder a un valor de `char_type` válido. El compilador de Microsoft C++ aplica esta restricción para el tipo **Char**, pero no para el tipo **wchar_t**. Esto no cumple con el requisito indicado en la tabla 62 de la sección 12.1.1 de la especificación ISO de C++. En el ejemplo siguiente se muestra esto.

```cpp
#include <iostream>

int main()
{
    using namespace std;

    char_traits<char>::int_type int2 = char_traits<char>::eof();
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;

    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;
}
```

## <a name="storage-location-of-objects"></a>Ubicación de almacenamiento de objetos

El estándar de C++ (sección 1.8, párrafo 6) requiere que los objetos de C++ completos tengan ubicaciones de almacenamiento únicas. Sin embargo, C++con Microsoft, hay casos en los que los tipos sin miembros de datos compartirán una ubicación de almacenamiento con otros tipos mientras dure el objeto.
