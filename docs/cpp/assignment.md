---
title: Asignación
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
ms.openlocfilehash: 1e6d715011cfaab7e250e23a9a31bb3f0c83f36a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184344"
---
# <a name="assignment"></a>Asignación

El operador de asignación (**=**), en realidad, es un operador binario. La declaración es idéntica a cualquier otro operador binario, con las excepciones siguientes:

- Debe ser una función miembro no estática. No **operador =** se pueden declarar como una función no miembro.
- Las clases derivadas no lo heredan.
- Valor predeterminado es **operador =** función puede generarse mediante el compilador para los tipos de clase, si no existe ninguno.

El ejemplo siguiente muestra cómo declarar un operador de asignación:

```cpp
class Point
{
public:
    int _x, _y;

    // Right side of copy assignment is the argument.
    Point& operator=(const Point&);
};

// Define copy assignment operator.
Point& Point::operator=(const Point& otherPoint)
{
    _x = otherPoint._x;
    _y = otherPoint._y;

    // Assignment operator returns left side of assignment.
    return *this;
}

int main()
{
    Point pt1, pt2;
    pt1 = pt2;
}
```

El argumento proporcionado es el lado derecho de la expresión. El operador devuelve el objeto para preservar el comportamiento del operador de asignación, que devuelve el valor del lado izquierdo después de que se complete la asignación. Esto permite el encadenamiento de asignaciones, tales como:

```cpp
pt1 = pt2 = pt3;
```

El operador de asignación de copia no es debe confundirse con el constructor de copias. Esto último se llama durante la construcción de un nuevo objeto desde otra existente:

```cpp
// Copy constructor is called--not overloaded copy assignment operator!
Point pt3 = pt1;

// The previous initialization is similar to the following:
Point pt4(pt1); // Copy constructor call.
```

> [!NOTE]
> Es conveniente seguir el [regla de tres](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)) que una clase que define un operador de asignación de copia debe definir explícitamente el constructor de copia, destructor y, a partir de C ++ 11, mueven el constructor y mover la asignación de operador.

## <a name="see-also"></a>Vea también

- [Sobrecarga de operadores](../cpp/operator-overloading.md)
- [Constructores de copia y operadores de asignación de copia (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)