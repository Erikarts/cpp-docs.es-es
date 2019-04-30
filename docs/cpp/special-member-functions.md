---
title: Funciones miembro especiales
ms.date: 12/06/2016
helpviewer_keywords:
- special member functions [C++]
- constructors [C++]
- destructors [C++]
- copy operators [C++]
- move operators [C++]
- assignment operators [C++]
ms.assetid: 017d6817-b012-44f0-b153-f3076c251ea7
ms.openlocfilehash: 3b26628fd18749bd19819fe787888fd3264a79d1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330985"
---
# <a name="special-member-functions"></a>Funciones miembro especiales

El *funciones miembro especiales* es de clase (o struct) las funciones miembro que, en algunos casos, el compilador genera automáticamente para usted. Estas funciones son la [constructor predeterminado](constructors-cpp.md#default_constructors), el [destructor](destructors-cpp.md), [constructor de copias y el operador de asignación de copia](copy-constructors-and-copy-assignment-operators-cpp.md)y el [constructor de movimiento y operador de asignación de movimiento](move-constructors-and-move-assignment-operators-cpp.md). Si la clase no define una o varias de las funciones miembro especiales, el compilador implícitamente puede declarar y definir las funciones que se usan. Se llama a las implementaciones generadas por el compilador la *predeterminada* funciones miembro especiales. El compilador no genera funciones si no son necesarios.

Puede declarar explícitamente una función miembro especial de forma predeterminada mediante el uso de la **= default** palabra clave. Esto hace que el compilador definir la función solo si es necesario, de la misma manera que si la función no se declaró en absoluto.

En algunos casos, el compilador puede generar *eliminado* funciones miembro especiales, lo que no están definidos y, por tanto, no puede llamar. Esto puede ocurrir en casos donde una llamada a una función miembro especial determinado en una clase no tiene sentido, tiene otras propiedades de la clase. Para evitar explícitamente que la generación automática de una función miembro especial, puede declararlo como eliminadas mediante el uso de la **= delete** palabra clave.

El compilador genera un *constructor predeterminado*, un constructor que no toma ningún argumento, solo cuando no se ha declarado ningún otro constructor. Si se ha declarado únicamente un constructor que toma parámetros, el código que intenta llamar a un constructor predeterminado, el compilador generar un mensaje de error. El constructor predeterminado generado por el compilador realiza simple member-wise [inicialización predeterminada](initializers.md#default_initialization) del objeto. Inicialización predeterminada deja todas las variables miembro en un estado indeterminado.

El destructor predeterminado realiza automáticamente miembro a miembro destrucción del objeto. Es virtual solo si un destructor de clase base es virtual.

La copia de forma predeterminada y la construcción de movimiento y las operaciones de asignación miembro a miembro del patrón de bits de realizar copia o mueve de miembros de datos no estáticos. Mover las operaciones solo se generan cuando no se declaran ningún destructor u operaciones de mover o copiar. Un constructor de copias predeterminado solo se genera cuando no se declara ningún constructor de copias. Se eliminó implícitamente si se declara una operación de movimiento. Un operador de asignación de copia predeterminado se genera solo cuando no se declara explícitamente ningún operador de asignación de copia. Se eliminó implícitamente si se declara una operación de movimiento.

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](cpp-language-reference.md)