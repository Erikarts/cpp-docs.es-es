---
title: Error del compilador C2143
ms.date: 11/04/2016
f1_keywords:
- C2143
helpviewer_keywords:
- C2143
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
ms.openlocfilehash: ed4bc7eea85e5263d59817082caed99bde3d75d5
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520119"
---
# <a name="compiler-error-c2143"></a>Error del compilador C2143

error de sintaxis: falta 'token1' delante de 'token2'

El compilador esperaba un token específico (es decir, un elemento del lenguaje que no sea espacio en blanco) y encontró otro token en su lugar.

Compruebe el [referencia del lenguaje C++](../../cpp/cpp-language-reference.md) para determinar dónde se encuentra código sintácticamente incorrecto. Dado que el compilador puede notificar este error después de que encuentre la línea que causa el problema, compruebe varias líneas de código que preceden el error.

C2143 puede producirse en diversas situaciones.

Puede producirse cuando un operador que se puede calificar un nombre (`::`, `->`, y `.`) debe ir seguido por la palabra clave `template`, como en este ejemplo:

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143
    {
    };
};
```

De forma predeterminada, C++ supone que `Ty::PutFuncType` no es una plantilla; por lo tanto, la siguiente `<` se interpreta como un menor-que el inicio de sesión.  Debe indicar al compilador explícitamente que `PutFuncType` es una plantilla para que pueda analizar correctamente el corchete angular de cierre. Para corregir este error, utilice el `template` palabra clave en nombre del tipo dependientes, como se muestra aquí:

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct
    {
    };
};
```

C2143 puede producirse cuando **/CLR** se usa y un `using` directiva tiene un error de sintaxis:

```cpp
// C2143a.cpp
// compile with: /clr /c
using namespace System.Reflection;   // C2143
using namespace System::Reflection;
```

También puede producirse cuando intenta compilar un archivo de código fuente mediante la sintaxis de CLR sin usar también **/CLR**:

```cpp
// C2143b.cpp
ref struct A {   // C2143 error compile with /clr
   void Test() {}
};

int main() {
   A a;
   a.Test();
}
```

El primer carácter que no sean espacios en blanco que sigue un `if` instrucción debe ser un paréntesis izquierdo. El compilador no puede traducir nada más:

```cpp
// C2143c.cpp
int main() {
   int j = 0;

   // OK
   if (j < 25)
      ;

   if (j < 25)   // C2143
}
```

C2143 puede producirse cuando falta una llave de cierre, un paréntesis o un punto y coma en la línea donde se detectó el error o en una de las líneas justo encima de:

```cpp
// C2143d.cpp
// compile with: /c
class X {
   int member1;
   int member2   // C2143
} x;
```

O bien, cuando hay una etiqueta no válida en una declaración de clase:

```cpp
// C2143e.cpp
class X {
   int member;
} x;

class + {};   // C2143 + is an invalid tag name
class ValidName {};   // OK
```

O bien, si una etiqueta no está conectada a una instrucción. Si se debe colocar una etiqueta por sí mismo, por ejemplo, al final de una instrucción compuesta, adjuntarla a una instrucción null:

```cpp
// C2143f.cpp
// compile with: /c
void func1() {
   // OK
   end1:
      ;

   end2:   // C2143
}
```

El error puede producirse cuando se realiza una llamada sin calificar a un tipo en la biblioteca estándar de C++:

```cpp
// C2143g.cpp
// compile with: /EHsc /c
#include <vector>
static vector<char> bad;   // C2143
static std::vector<char> good;   // OK
```

O si hay una falta `typename` palabra clave:

```cpp
// C2143h.cpp
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};
template <typename T>
X<T>::Y X<T>::memFunc() {   // C2143
// try the following line instead
// typename X<T>::Y X<T>::memFunc() {
   return Y();
}
```

O bien, si se intenta definir una instancia explícita:

```cpp
// C2143i.cpp
// compile with: /EHsc /c
// template definition
template <class T>
void PrintType(T i, T j) {}

template void PrintType(float i, float j){}   // C2143
template void PrintType(float i, float j);   // OK
```

En un programa C, las variables deben declararse al principio de la función y no puede declararse después de la función ejecuta las instrucciones de declaración no.

```C
// C2143j.c
int main()
{
    int i = 0;
    i++;
    int j = 0; // C2143
}
```
