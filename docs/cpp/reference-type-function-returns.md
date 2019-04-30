---
title: Valores devueltos de función de tipo de referencia
ms.date: 11/04/2016
helpviewer_keywords:
- function return types [C++], reference type
- data types [C++], function return types
- functions [C++], return types
ms.assetid: 5b73be1d-2dc7-41df-ab0a-adcba36f2ad1
ms.openlocfilehash: a2d7fa9ddbc1d4a2f922b5a20930e150ae991f38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403443"
---
# <a name="reference-type-function-returns"></a>Valores devueltos de función de tipo de referencia

Las funciones se pueden declarar para que devuelvan un tipo de referencia. Hay dos motivos para realizar este tipo de declaración:

- La información que se va a devolver es un objeto tan grande que devolver una referencia es más eficaz que devolver una copia.

- El tipo de la función debe ser un valor L.

- El objeto al que se hace referencia no saldrá del ámbito cuando la función devuelva un valor.

Al igual que puede ser más eficaz pasar objetos grandes *a* funciones por referencia, también puede ser más eficaz devolver objetos grandes *desde* funciones por referencia. El protocolo de devolución de referencias elimina la necesidad de copiar el objeto en una ubicación temporal antes de que se devuelva.

Los tipos de valor devuelto de las referencias también pueden ser útiles cuando la función se debe evaluar como un valor L. La mayoría de los operadores sobrecargados pertenecen a esta categoría, especialmente el operador de asignación. Operadores sobrecargados se explican en [operadores sobrecargados](../cpp/operator-overloading.md).

## <a name="example"></a>Ejemplo

Considere el ejemplo `Point`:

```cpp
// refType_function_returns.cpp
// compile with: /EHsc

#include <iostream>
using namespace std;

class Point
{
public:
// Define "accessor" functions as
//  reference types.
unsigned& x();
unsigned& y();
private:
// Note that these are declared at class scope:
unsigned obj_x;
unsigned obj_y;
};

unsigned& Point :: x()
{
return obj_x;
}
unsigned& Point :: y()
{
return obj_y;
}

int main()
{
Point ThePoint;
// Use x() and y() as l-values.
ThePoint.x() = 7;
ThePoint.y() = 9;

// Use x() and y() as r-values.
cout << "x = " << ThePoint.x() << "\n"
<< "y = " << ThePoint.y() << "\n";
}
```

## <a name="output"></a>Salida

```Output
x = 7
y = 9
```

Observe que las funciones `x` e `y` se declaran de forma que devuelvan referencias. Estas funciones se pueden utilizar en cada lado de una instrucción de asignación.

Tenga en cuenta también que en main, el objeto ThePoint permanece en el ámbito y, por tanto, sus miembros de referencia continúan activos y se puede obtener acceso a ellos de forma segura.

Las declaraciones de tipos de referencia deben contener inicializadores excepto en los casos siguientes:

- Explícita **extern** declaración

- Declaración de un miembro de clase

- Declaración dentro de una clase

- Declaración de un argumento a una función o el tipo de valor devuelto de una función

## <a name="caution-returning-address-of-local"></a>Precaución sobre devolución de dirección

Si se declara un objeto en el ámbito local, ese objeto se destruirá cuando la función devuelva un valor. Si la función devuelve una referencia a ese objeto, esa referencia probablemente provocará una infracción de acceso en tiempo de ejecución si el llamador intenta usar la referencia nula.

```cpp
// C4172 means Don’t do this!!!
Foo& GetFoo()
{
    Foo f;
    ...
    return f;
} // f is destroyed here
```

El compilador emite una advertencia en este caso: `warning C4172: returning address of local variable or temporary`. Es posible que, en programas simples y en ocasiones, no se produzca ninguna infracción de acceso si el llamador tiene acceso a la referencia antes de que se sobrescriba la ubicación de memoria. Es simplemente una cuestión de suerte, así que haga caso a la advertencia.

## <a name="see-also"></a>Vea también

[Referencias](../cpp/references-cpp.md)