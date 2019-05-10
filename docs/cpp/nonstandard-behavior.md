---
title: Comportamiento no estándar
ms.date: 05/06/2019
helpviewer_keywords:
- compatibility and compliance, nonstandard behavior
- Microsoft-specific, compiler behavior
- nonstandard behavior, compliance and compatibility
ms.assetid: a57dea27-dc79-4f64-8a83-017e84841773
ms.openlocfilehash: 82c5faae68f9da747017119d76578cc88163d8bb
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222031"
---
# <a name="nonstandard-behavior"></a>Comportamiento no estándar

Las siguientes secciones enumeran algunos de los lugares donde la implementación de Microsoft C++ no cumple con los C++ estándar. Los números de sección que se indican a continuación se refieren a los números de sección del estándar de C++ 11 (ISO/IEC 14882:2011(E)).

La lista de los límites del compilador que difieren de los definidos en el estándar de C++ se proporciona [límites del compilador](../cpp/compiler-limits.md).

## <a name="covariant-return-types"></a>Tipos de valor devueltos de covariante

Las clases base virtuales no se admiten como tipos de valor devueltos de covariante cuando la función virtual tiene un número variable de argumentos. Esto no cumple con el párrafo 7 de la sección 10.3 de la especificación ISO de C++. El ejemplo siguiente no se compila, error del compilador [C2688](../error-messages/compiler-errors-2/compiler-error-c2688.md)

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

Microsoft C++ compilador no admite actualmente nombres no dependientes al analizar una plantilla inicialmente. Esto no cumple con la sección 14.6.3 de la especificación ISO de C++. Esto puede hacer que se vean las sobrecargas declaradas después de la plantilla (pero antes de que se creen instancias de la plantilla).

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

Para obtener más información sobre las especificaciones de excepciones, vea [las especificaciones de excepción](../cpp/exception-specifications-throw-cpp.md).

## <a name="chartraitseof"></a>char_traits::eof()

El C++ estándar de Estados que [char_traits:: EOF](../standard-library/char-traits-struct.md#eof) no debe corresponder a una `char_type` valor. Microsoft C++ compilador exige esta restricción de tipo **char**, pero no para el tipo **wchar_t**. Esto no cumple con el requisito indicado en la tabla 62 de la sección 12.1.1 de la especificación ISO de C++. En el ejemplo siguiente se muestra esto.

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

El estándar de C++ (sección 1.8, párrafo 6) requiere que los objetos de C++ completos tengan ubicaciones de almacenamiento únicas. Sin embargo con Microsoft C++, hay casos en los que tipos sin miembros de datos compartirán una ubicación de almacenamiento con otros tipos durante la vigencia del objeto.