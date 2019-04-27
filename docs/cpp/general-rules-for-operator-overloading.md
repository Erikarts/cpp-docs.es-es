---
title: Reglas generales para la sobrecarga de operadores
ms.date: 11/04/2016
helpviewer_keywords:
- operator overloading [C++], rules
ms.assetid: eb2b3754-35f7-4832-b1da-c502893dc0c7
ms.openlocfilehash: 1eceb26a244bc6dd2d5243e54f5e3b8391d88ed1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153767"
---
# <a name="general-rules-for-operator-overloading"></a>Reglas generales para la sobrecarga de operadores

Las reglas siguientes restringen la forma en que se implementan los operadores sobrecargados. Sin embargo, no se aplican a la [nueva](../cpp/new-operator-cpp.md) y [eliminar](../cpp/delete-operator-cpp.md) operadores, que se tratan por separado.

- No se puede definir nuevos operadores, tales como **.**.

- No se puede volver a definir el significado de los operadores cuando se aplican a los tipos de datos integrados.

- Los operadores sobrecargados deben ser una función miembro de clase no estática o una función global. Una función global que necesita acceso a miembros de clase privados o protegidos se debe declarar como friend de esa clase. Una función global debe tomar al menos un argumento que sea de clase o de tipo enumerado, o que sea una referencia a una clase o a un tipo enumerado. Por ejemplo:

    ```cpp
    // rules_for_operator_overloading.cpp
    class Point
    {
    public:
        Point operator<( Point & );  // Declare a member operator
                                     //  overload.
        // Declare addition operators.
        friend Point operator+( Point&, int );
        friend Point operator+( int, Point& );
    };

    int main()
    {
    }
    ```

   En el ejemplo de código anterior se declara el operador "menos que" como función miembro; sin embargo, los operadores de suma se declaran como funciones globales con acceso de confianza. Observe que se puede proporcionar más de una implementación para un operador determinado. En el caso del operador de suma anterior, las dos implementaciones se proporcionan para facilitar la propiedad conmutativa. Es igual que es probable que esa operadores que agregan un `Point` a un `Point`, **int** a un `Point`, y así sucesivamente, podría implementarse.

- Los operadores obedecen a la prioridad, la agrupación y el número de operandos dictados por su uso típico con los tipos integrados. Por lo tanto, no hay ninguna manera de expresar el concepto "sumar 2 y 3 para un objeto de tipo `Point`," espera 2 que se agregarán a la *x* coordenadas y 3 para agregarse a la *y* coordinar.

- Los operadores unarios declarados como funciones miembro no toman ningún argumento; si se declaran como funciones globales, toman un argumento.

- Los operadores binarios declarados como funciones miembro toman un argumento; si se declaran como funciones globales, toman dos argumentos.

- Si un operador puede usarse como unario o un operador binario (__&__, __*__, __+__, y __-__), puede sobrecargar cada uso por separado.

- Los operadores sobrecargados no pueden tener argumentos predeterminados.

- Todos los operadores sobrecargados, excepto asignación (**operador =**) heredan las clases derivadas.

- El primer argumento para los operadores sobrecargados de función miembro siempre es del tipo de clase del objeto para el que se invoca el operador (la clase en la que se declara el operador o una clase derivada de ella). No se proporciona ninguna conversión para el primer argumento.

Observe que el significado de cualquiera de los operadores se puede cambiar por completo. Esto incluye el significado de la dirección del (**&**), asignación (**=**) y los operadores de llamada de función. Además, las identidades en las que se puede confiar para los tipos integrados pueden cambiarse mediante la sobrecarga de operadores. Por ejemplo, las cuatro instrucciones siguientes suelen ser equivalentes cuando se evalúan completamente:

```cpp
var = var + 1;
var += 1;
var++;
++var;
```

No se puede confiar en esta identidad para los tipos de clase que sobrecargan operadores. Además, algunos requisitos implícitos en el uso de estos operadores para los tipos básicos se relajan para los operadores sobrecargados. Por ejemplo, el operador de suma y asignación, **+=**, requiere que el operando izquierdo sea un valor l cuando se aplica a los tipos básicos; no hay ningún requisito de este tipo cuando se sobrecarga el operador.

> [!NOTE]
> Por coherencia, a menudo es mejor seguir el modelo de los tipos integrados al definir operadores sobrecargados. Si la semántica de un operador sobrecargado difiere mucho de su significado en otros contextos, puede ser más confusa que útil.

## <a name="see-also"></a>Vea también

[Sobrecarga de operadores](../cpp/operator-overloading.md)