---
title: protected (C++)
ms.date: 11/04/2016
f1_keywords:
- protected_cpp
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
ms.openlocfilehash: 1cbe88a80b83caa78972d1e2799c1e0d87d1cb0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244533"
---
# <a name="protected-c"></a>protected (C++)

## <a name="syntax"></a>Sintaxis

```
protected:
   [member-list]
protected base-class
```

## <a name="remarks"></a>Comentarios

El **protegido** palabra clave especifica el acceso a los miembros de clase en el *lista de miembros* hasta el especificador de acceso siguiente (**pública** o **privada**) o el final de la definición de clase. Miembros de clase declarados como **protegido** puede usarse únicamente por lo siguiente:

- Funciones miembro de la clase que declaró originalmente estos miembros.

- Objetos friend de la clase que declaró originalmente estos miembros.

- Clases derivadas con acceso público o protegido desde la clase que declaró originalmente estos miembros.

- Clases directas derivadas de forma privada que también tienen acceso privado a miembros protegidos.

Cuando precede al nombre de una clase base, el **protegido** palabra clave especifica que los miembros públicos y protegidos de la clase base son miembros protegidos de sus clases derivadas.

Los miembros protegidos no son tan privados como **privada** miembros, que son accesibles sólo a los miembros de la clase en el que se declaran, pero no son tan públicos como **pública** miembros, que son accesibles en cualquier función.

Los miembros protegidos que también se declaran como **estático** son accesibles para cualquier función miembro o friend de una clase derivada. Los miembros protegidos que no se declaran como **estático** son accesibles a sus amigos y funciones de miembro en una clase derivada solo a través de un puntero para hacer referencia a, o un objeto de la clase derivada.

Para obtener información relacionada, consulte [friend](../cpp/friend-cpp.md), [pública](../cpp/public-cpp.md), [privada](../cpp/private-cpp.md)y en la tabla de acceso a miembros [controlar el acceso a los miembros de clase](member-access-control-cpp.md) .

## <a name="clr-specific"></a>Específicos de /clr

En los tipos CLR, C++, obtener acceso a las palabras clave de especificador (**pública**, **privada**, y **protegido**) pueden afectar a la visibilidad de tipos y métodos con respecto a los ensamblados. Para obtener más información, consulte [Control de acceso de miembro](member-access-control-cpp.md).

> [!NOTE]
>  Los archivos compilados con [/LN](../build/reference/ln-create-msil-module.md) no se ven afectados por este comportamiento. En este caso, todas las clases administradas (ya sean públicas o privadas) estarán visibles.

## <a name="end-clr-specific"></a>Específicos de END /clr

## <a name="example"></a>Ejemplo

```cpp
// keyword_protected.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class X {
public:
   void setProtMemb( int i ) { m_protMemb = i; }
   void Display() { cout << m_protMemb << endl; }
protected:
   int  m_protMemb;
   void Protfunc() { cout << "\nAccess allowed\n"; }
} x;

class Y : public X {
public:
   void useProtfunc() { Protfunc(); }
} y;

int main() {
   // x.m_protMemb;         error, m_protMemb is protected
   x.setProtMemb( 0 );   // OK, uses public access function
   x.Display();
   y.setProtMemb( 5 );   // OK, uses public access function
   y.Display();
   // x.Protfunc();         error, Protfunc() is protected
   y.useProtfunc();      // OK, uses public access function
                        // in derived class
}
```

## <a name="see-also"></a>Vea también

[Controlar el acceso a los miembros de clase](member-access-control-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)