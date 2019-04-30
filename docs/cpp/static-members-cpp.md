---
title: Miembros estáticos (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- class members [C++], static
- instance constructors, static members
- class members [C++], shared
- members [C++], static data members
- static members [C++], data members
- static data members [C++]
- data members [C++], static data members
- class instances [C++], shared members
- instance constructors, shared members
- class instances [C++], static members
ms.assetid: 9cc8cf0f-d74c-46f2-8e83-42d4e42c8370
ms.openlocfilehash: 708f78c09db263584d478d16863999d4428e4891
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266951"
---
# <a name="static-members-c"></a>Miembros estáticos (C++)

Las clases pueden contener datos de miembro y funciones miembro estáticos. Cuando se declara un miembro de datos como **estático**, solo una copia de los datos se mantiene para todos los objetos de la clase.

Los miembros de datos estáticos no forman parte de los objetos de un tipo de clase determinado. Por tanto, la declaración de un miembro de datos estático no se considera una definición. El miembro de datos se declara en el ámbito de la clase, pero la definición se realiza en el ámbito de archivo. Estos miembros estáticos tienen vinculación externa. Esto se ilustra en el siguiente ejemplo:

```cpp
// static_data_members.cpp
class BufferedOutput
{
public:
   // Return number of bytes written by any object of this class.
   short BytesWritten()
   {
      return bytecount;
   }

   // Reset the counter.
   static void ResetCount()
   {
      bytecount = 0;
   }

   // Static member declaration.
   static long bytecount;
};

// Define bytecount in file scope.
long BufferedOutput::bytecount;

int main()
{
}
```

En el código anterior, el miembro `bytecount` se declara en la clase `BufferedOutput`, pero debe definirse fuera de la declaración de clase.

Se puede hacer referencia a miembros de datos estáticos sin hacer referencia a un objeto de tipo de clase. El número de bytes escritos mediante objetos de `BufferedOutput` puede obtenerse de la manera siguiente:

```cpp
long nBytes = BufferedOutput::bytecount;
```

Para que el miembro estático exista, no es necesario que exista ningún objeto del tipo de clase. Los miembros estáticos también se pueden acceder mediante la selección de miembro (**.** y **->**) operadores. Por ejemplo:

```cpp
BufferedOutput Console;

long nBytes = Console.bytecount;
```

En el caso anterior, la referencia al objeto (`Console`) no se evalúa; el valor devuelto es el del objeto estático `bytecount`.

Los miembros de datos estáticos están sujetos a las reglas de acceso a miembros de clase, por lo que el acceso privado a miembros de datos estáticos solo se permite para las funciones miembro de clase y los elementos friend. Estas reglas se describen en [Control de acceso de miembro](../cpp/member-access-control-cpp.md). La excepción es que los miembros de datos estáticos se deben definir en el ámbito de archivo, independientemente de sus restricciones de acceso. Si el miembro de datos se va a inicializar explícitamente, se debe proporcionar un inicializador con la definición.

El nombre de clase no califica el tipo de un miembro estático. Por lo tanto, el tipo de `BufferedOutput::bytecount` es **largo**.

## <a name="see-also"></a>Vea también

[Clases y structs](../cpp/classes-and-structs-cpp.md)