---
title: Flujos de entrada
ms.date: 11/04/2016
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- input streams
- input stream objects
ms.assetid: f14d8954-8f8c-4c3c-8b99-14ddb3683f94
ms.openlocfilehash: 0f56f5ffc8e61c0881eddbbd65e1c431b9219674
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404928"
---
# <a name="input-streams"></a>Flujos de entrada

Un objeto de flujo de entrada es un origen de bytes. Las tres clases más importantes de flujos de entrada son [istream](../standard-library/basic-istream-class.md), [ifstream](../standard-library/basic-ifstream-class.md) e [istringstream](../standard-library/basic-istringstream-class.md).

La clase `istream` se usa para la entrada secuencial de modo de texto. Puede configurar los objetos de la clase `istream` para el funcionamiento almacenado o no en búfer. Todas las funciones de la clase base, `ios`, se incluyen en `istream`. Rara vez se construyen objetos a partir de la clase `istream`. En su lugar, generalmente se usa el objeto `cin` predefinido, que en realidad es un objeto de clase [ostream](../standard-library/basic-ostream-class.md). En algunos casos, puede asignar `cin` a otros objetos de flujo después del inicio del programa.

La clase `ifstream` admite la entrada de archivo de disco. Si necesita un archivo de disco de solo entrada, construya un objeto de clase `ifstream`. Puede especificar datos binarios o de modo de texto. Si especifica un nombre de archivo en el constructor, ese archivo se abre automáticamente cuando el objeto se construye. De otro modo, puede usar la función `open` después de invocar el constructor predeterminado. Muchas opciones de formato y funciones miembro se aplican a objetos `ifstream`. Todas las funciones de las clases base `ios` y `istream` se incluyen en `ifstream`.

Al igual que la función de biblioteca `sscanf_s`, la clase `istringstream` admite la entrada desde cadenas en memoria. Para extraer datos de una matriz de caracteres que tiene un terminador nulo, asigne e inicialice la cadena y, después, construya un objeto de clase `istringstream`.

## <a name="in-this-section"></a>En esta sección

[Construir objetos de flujo de entrada](../standard-library/constructing-input-stream-objects.md)

[Usar operadores de extracción](../standard-library/using-extraction-operators.md)

[Comprobar errores de extracción](../standard-library/testing-for-extraction-errors.md)

[Manipuladores de flujos de entrada](../standard-library/input-stream-manipulators.md)

[Funciones miembro de flujo de entrada](../standard-library/input-stream-member-functions.md)

[Sobrecargar el operador >> para las clases propias](../standard-library/overloading-the-input-operator-for-your-own-classes.md)

## <a name="see-also"></a>Vea también

[Programación con iostream](../standard-library/iostream-programming.md)<br/>
