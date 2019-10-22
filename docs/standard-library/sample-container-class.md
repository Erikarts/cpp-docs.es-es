---
title: Sample Container (Clase)
ms.date: 11/04/2016
helpviewer_keywords:
- container classes [C++]
ms.assetid: 5b1451f2-c708-45da-bbf0-9e42fd687a1a
ms.openlocfilehash: 404e372e65af8b93ae4f6f2827a73ef64336690a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688974"
---
# <a name="sample-container-class"></a>Sample Container (Clase)

> [!NOTE]
> Este tema se encuentra en la C++ documentación de Microsoft como un ejemplo no funcional de contenedores usados en C++ la biblioteca estándar. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).

Describe un objeto que controla una secuencia de elementos de longitud variable, normalmente de tipo `Ty`. La secuencia se almacena de diferentes maneras, dependiendo del contenedor real.

Un constructor de contenedor o una función miembro puede encontrar la ocasión de llamar al constructor **Ty**(**const Ty&** ) o la función **Ty::operator=** (**const Ty&** ). Si esta llamada inicia una excepción, el objeto contenedor está obligado a mantener su integridad y reiniciar cualquier excepción que detecte. Puede intercambiar, asignar, borrar o destruir un objeto contenedor de forma segura después de que inicie una de estas excepciones. Pero en general, no hay otra forma de predecir el estado de la secuencia controlada por el objeto contenedor.

Algunas advertencias adicionales:

- Si el `~Ty` de la expresión produce una excepción, el estado resultante del objeto contenedor no está definido.

- Si el contenedor almacena un objeto de asignador *al*, y *al* produce una excepción distinta de como resultado de una llamada a `al.allocate`, el estado resultante del objeto contenedor no está definido.

- Si el contenedor almacena un objeto de función *comp*, para determinar cómo ordenar la secuencia controlada, y *comp* inicia una excepción de cualquier tipo, el estado resultante del objeto contenedor no está definido.

Las clases de contenedor definidas por la biblioteca estándar de C++ cumplen varios requisitos adicionales, como se describe en los párrafos siguientes.

La [lista](../standard-library/list-class.md) de plantillas de clase de contenedor proporciona un comportamiento determinista y útil, incluso en presencia de las excepciones descritas anteriormente. Por ejemplo, si se inicia una excepción durante la inserción de uno o más elementos, el contenedor permanece inalterado y se reinicia la excepción.

Para *todas* las clases de contenedor definidas C++ por la biblioteca estándar, si se produce una excepción durante las llamadas a las siguientes funciones miembro, `insert`, `push_back` o `push_front`, el contenedor se deja sin modificar y se vuelve a producir la excepción.

Para *todas* las clases de contenedor definidas C++ por la biblioteca estándar, no se produce ninguna excepción durante las llamadas a las siguientes funciones miembro: `pop_back` `pop_front`.

la función miembro [erase](../standard-library/container-class-erase.md) inicia una excepción solo si una operación de copia (construcción de asignación o copia) inicia una excepción.

Además, no se inicia ninguna excepción durante la copia de un iterador devuelto por una función miembro.

La función miembro [swap](../standard-library/container-class-swap.md) hace promesas adicionales para *todas* las clases de contenedor definidas por la biblioteca estándar de C++:

- La función miembro inicia una excepción solo si el contenedor almacena un objeto de asignador al, y `al` inicia una excepción cuando se copia.

- Las referencias, los punteros y los iteradores que designan elementos de las secuencias controladas que se intercambia siguen siendo válidos.

Un objeto de una clase de contenedor definida por la biblioteca estándar de C++ asigna y libera almacenamiento de la secuencia que controla a través de un objeto almacenado de tipo `Alloc`, que normalmente es un parámetro de plantilla. Este tipo de objeto de asignador debe tener la misma interfaz externa que un objeto de clase `allocator<Ty>`. En concreto, `Alloc` debe ser del mismo tipo que `Alloc::rebind<value_type>::other`

Para *todas* las clases de contenedor C++ definidas por la biblioteca estándar, la función miembro `Alloc get_allocator const;` devuelve una copia del objeto de asignador almacenado. Tenga en cuenta que el objeto de asignador almacenado *no* se copia cuando se asigna el objeto contenedor. Todos los constructores inicializan el valor almacenado en `allocator`, en `Alloc` si el constructor no contiene ningún parámetro de asignador.

Según el estándar de C++, una clase de contenedor definida por la biblioteca estándar de C++ puede asumir que:

- Todos los objetos de la clase `Alloc` se comparan igual.

- El tipo `Alloc::const_pointer` es igual que `const Ty *`.

- El tipo `Alloc::const_reference` es igual que `const Ty&`.

- El tipo `Alloc::pointer` es igual que `Ty *`.

- El tipo `Alloc::reference` es igual que `Ty&`.

Pero en esta implementación, los contenedores no hacen estas suposiciones tan simples. Por tanto, funcionan correctamente con objetos de asignador que son más ambiciosos:

- No es necesario que todos los objetos de la clase `Alloc` se comparen igual. (Puede mantener varios grupos de almacenamiento).

- No es necesario que el tipo `Alloc::const_pointer` sea el mismo que el `const Ty *`. (Un puntero const puede ser una clase).

- No es necesario que el tipo `Alloc::pointer` sea el mismo que el `Ty *`. (Un puntero puede ser una clase).

## <a name="requirements"></a>Requisitos

**Encabezado**: \<contenedor de ejemplo>

## <a name="see-also"></a>Vea también

[\<sample container>](../standard-library/sample-container.md)
