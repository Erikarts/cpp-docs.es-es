---
title: Llamada de función (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C++ functions
- functions [C++], calling
- operator overloading [C++], function calls
- function overloading [C++], function-call operator
- function calls, operator
- operators [C++], overloading
- operator overloading [C++], examples
- function call operator ()
ms.assetid: 5094254a-045b-46f7-8653-69bc91e80dce
ms.openlocfilehash: 6c7326b0f9c9592cb2b3be973a5ba1747a2015a0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179814"
---
# <a name="function-call-c"></a>Llamada de función (C++)

El operador de llamada a función, invocado mediante paréntesis, es un operador binario.

## <a name="syntax"></a>Sintaxis

```
primary-expression ( expression-list )
```

## <a name="remarks"></a>Observaciones

En este contexto, `primary-expression` es el primer operando, y `expression-list` (una lista de argumentos que posiblemente esté vacía) es el segundo operando. El operador de llamada a función se utiliza para las operaciones que requieren varios parámetros. Esto funciona porque `expression-list` es una lista en lugar de un solo operando. El operador de llamada a función debe ser una función miembro no estática.

El operador de llamada a función, cuando está sobrecargado, no modifica la forma de llamar a las funciones; en su lugar, modifica cómo debe interpretarse el operador cuando se aplica a objetos de un tipo de clase especificado. Por ejemplo, el código siguiente normalmente no tendría sentido:

```cpp
Point pt;
pt( 3, 2 );
```

Pero, con un operador sobrecargado de llamada a función adecuado, esta sintaxis se puede usar para desplazar 3 unidades la coordenada `x` y 2 unidades la coordenada `y`. En el código siguiente se muestra esa definición:

```cpp
// function_call.cpp
class Point
{
public:
    Point() { _x = _y = 0; }
    Point &operator()( int dx, int dy )
        { _x += dx; _y += dy; return *this; }
private:
    int _x, _y;
};

int main()
{
   Point pt;
   pt( 3, 2 );
}
```

Tenga en cuenta que el operador de llamada a función se aplica al nombre de un objeto, no al nombre de una función.

También puede sobrecargar el operador de llamada de función mediante un puntero a una función (en lugar de a la función en sí).

```cpp
typedef void(*ptf)();
void func()
{
}
struct S
{
   operator ptf()
   {
      return func;
   }
};

int main()
{
   S s;
   s();//operates as s.operator ptf()()
}
```

## <a name="see-also"></a>Consulte también

[Sobrecarga de operadores](../cpp/operator-overloading.md)
