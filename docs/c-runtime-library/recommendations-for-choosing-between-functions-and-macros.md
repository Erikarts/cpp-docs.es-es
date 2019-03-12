---
title: Recomendaciones para elegir entre funciones y macros
ms.date: 11/04/2016
f1_keywords:
- c.functions
helpviewer_keywords:
- functions [CRT], vs. macros
- macros, vs. functions
ms.assetid: 18a633d6-cf1c-470c-a649-fa7677473e2b
ms.openlocfilehash: 234fcd8a0439240bc7585414254c5687dcb8f21b
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749313"
---
# <a name="recommendations-for-choosing-between-functions-and-macros"></a>Recomendaciones para elegir entre funciones y macros

La mayoría de las rutinas de la biblioteca en tiempo de ejecución de Microsoft son funciones compiladas o ensambladas, aunque algunas rutinas se implementan como macros. Cuando un archivo de encabezado declara una función y una versión de macro de una rutina, la definición de macro tiene prioridad, porque siempre aparece después de la declaración de función. Cuando se invoca una rutina que se implementa como una función y como una macro, puede forzar al compilador a que utilice la versión de función de dos maneras:

- Agregar el nombre de la rutina entre paréntesis.

    ```C
    #include <ctype.h>
    a = _toupper(a);    // Use macro version of toupper.
    a = (_toupper)(a);  // Force compiler to use
                        // function version of toupper.
    ```

- "Anular la definición" de la macro con la directiva `#undef`:

    ```C
    #include <ctype.h>
    #undef _toupper
    ```

Si tiene que elegir entre una función y una implementación de la macro de una rutina de la biblioteca, tenga en cuenta las ventajas y desventajas siguientes:

- **Velocidad frente a tamaño** El principal beneficio del uso de las macros es que ofrece un tiempo de ejecución más rápido. Durante el preprocesamiento, una macro se expande (reemplazada por su definición) alineada cada vez que se utiliza. Una definición de función se produce una vez, con independencia de cuántas veces se le llame. Las macros pueden aumentar el tamaño del código, pero no tienen la sobrecarga asociada con las llamadas a funciones.

- **Evaluación de la función** Una función evalúa una dirección, pero una macro no. Por lo tanto, no se puede utilizar un nombre de macro en contextos que requieren un puntero. Por ejemplo, puede declarar un puntero a una función, pero no un puntero a una macro.

- **Comprobación de tipos** Cuando se declara una función, el compilador puede comprobar los tipos de argumentos. Como no se puede declarar una macro, el compilador no puede comprobar los tipos de argumentos de las macros, pero sí puede comprobar el número de argumentos transferidos a una macro.

## <a name="see-also"></a>Vea también

[Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)
