---
title: Error del compilador C2259
ms.date: 11/04/2016
f1_keywords:
- C2259
helpviewer_keywords:
- C2259
ms.assetid: e458236f-bdea-4786-9aa6-a98d8bffa5f4
ms.openlocfilehash: 562882f50edfe2d44ab1f08ee9dbe88fe468af63
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447385"
---
# <a name="compiler-error-c2259"></a>Error del compilador C2259

'clase' : no se puede crear una instancia de una clase abstract

El código declara una instancia de una estructura o clase abstracta.

No se puede crear instancias de una clase o estructura con una o varias funciones virtuales puras. Para crear instancias de objetos de una clase derivada, ésta deberá reemplazar a todas las funciones virtuales puras.

Para obtener más información, consulte [clases abstractas implícitamente](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Implicitly_abstract_classes).

El ejemplo siguiente genera el error C2259:

```
// C2259.cpp
// compile with: /c
class V {
public:
   void virtual func() = 0;
};
class A : public V {};
class B : public V {
public:
   void func();
};
V v;  // C2259, V is an abstract class
A a;  // C2259, A inherits func() as pure virtual
B b;  // OK, B defines func()
```

Siempre que derive de una interfaz e implemente los métodos de interfaz en la clase derivada con permisos de acceso distintos de público, podrá recibir el error C2259.  Esto ocurre porque el compilador espera que los métodos de interfaz implementados en la clase derivada tengan acceso público. Cuando se implementan las funciones miembro para una interfaz con permisos de acceso más restrictivos, el compilador no las considera como implementaciones para los métodos de interfaz definidos en la interfaz, lo que a su vez convierte a la clase derivada en una clase abstracta.

Hay dos posibles soluciones para el problema:

- Establecer los permisos de acceso como públicos para los métodos implementados.

- Usar el operador de resolución de ámbito para los métodos de interfaz implementados en la clase derivada para calificar el nombre del método implementado con el nombre de la interfaz.

Error C2259 también se puede producir como resultado del trabajo de conformidad efectuado en Visual Studio 2005, **/Zc:** está activado de manera predeterminada. En esta situación, se puede resolver compilando con C2599 **/Zc:wchar_t-**, para obtener el comportamiento de las versiones anteriores o, preferiblemente, actualizando los tipos para que sean compatibles. Para obtener más información, vea [/Zc:wchar_t (wchar_t es un tipo nativo)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

El ejemplo siguiente genera el error C2259:

```
// C2259b.cpp
// compile with: /c
#include <windows.h>

class MyClass {
public:
   // WCHAR now typedef'ed to wchar_t
   virtual void func(WCHAR*) = 0;
};

class MyClass2 : MyClass {
public:
   void func(unsigned short*);
};

MyClass2 x;   // C2259

// OK
class MyClass3 {
public:
   virtual void func(WCHAR*) = 0;
   virtual void func2(wchar_t*) = 0;
   virtual void func3(unsigned short*) = 0;
};

class MyClass4 : MyClass3 {
public:
   void func(WCHAR*) {}
   void func2(wchar_t*) {}
   void func3(unsigned short*) {}
};

MyClass4 y;
```

El ejemplo siguiente genera el error C2259:

```
// C2259c.cpp
// compile with: /clr
interface class MyInterface {
   void MyMethod();
};

ref class MyDerivedClass: public MyInterface {
private:
   // Uncomment the following line to resolve.
   // public:
   void MyMethod(){}
   // or the following line
   // void MyInterface::MyMethod() {};
};

int main() {
   MyDerivedClass^ instance = gcnew MyDerivedClass; // C2259
}
```
