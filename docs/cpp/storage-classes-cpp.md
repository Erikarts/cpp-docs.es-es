---
title: Clases de almacenamiento (C++)
description: En C++, las palabras clave static, extern y thread_local especifican la duración, la vinculación y la ubicación de la memoria de una variable o función.
ms.date: 12/11/2019
f1_keywords:
- thread_local_cpp
- extern_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: ab00a5c64a32dc1dab5fef4bc15b722587bc2d6b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856912"
---
# <a name="storage-classes"></a>Clases de almacenamiento

Una *clase de almacenamiento* en el contexto C++ de las declaraciones de variable es un especificador de tipo que rige la duración, la vinculación y la ubicación de la memoria de los objetos. Un objeto determinado puede tener solo una clase de almacenamiento. Las variables definidas dentro de un bloque tienen almacenamiento automático, a menos que se especifique lo contrario mediante los especificadores **extern**, **static**o **thread_local** . Las variables y objetos automáticos no tienen ninguna vinculación; no son visibles para código fuera del bloque. La memoria se asigna automáticamente cuando la ejecución entra en el bloque y se anula la asignación cuando se sale del bloque.

**Notas**

1. La palabra clave [mutable](../cpp/mutable-data-members-cpp.md) puede considerarse un especificador de clase de almacenamiento. Sin embargo, solo está disponible en la lista de miembros de una definición de clase.

1. **Visual Studio 2010 y versiones posteriores:** La palabra clave **auto** ya no es C++ un especificador de clase de almacenamiento y la palabra clave **Register** está en desuso. **Visual Studio 2017 versión 15,7 y versiones posteriores:** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)): la palabra clave **Register** se quita C++ del idioma.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="static"></a>estático

La palabra clave **static** se puede usar para declarar variables y funciones en el ámbito global, el ámbito de espacio de nombres y el ámbito de clase. También se pueden declarar variables estáticas en el ámbito local.

Duración estática significa que el objeto o la variable se asignan cuando se inicia el programa y se desasignan cuando finaliza el programa. Vinculación externa significa que el nombre de la variable puede verse desde fuera del archivo en el que se declara la variable. A la inversa, la vinculación interna significa que el nombre no es visible fuera del archivo en el que se declara la variable. De forma predeterminada, una variable o un objeto que se defina en el espacio de nombres global tiene duración estática y vinculación externa. La palabra clave **static** se puede usar en las siguientes situaciones.

1. Cuando se declara una variable o función en el ámbito de archivo (ámbito global o de espacio de nombres), la palabra clave **static** especifica que la variable o la función tiene vinculación interna. Cuando se declara una variable, la variable tiene duración estática y el compilador la inicializa como 0, a menos que se especifique otro valor.

1. Cuando se declara una variable en una función, la palabra clave **static** especifica que la variable mantiene su estado entre las llamadas a esa función.

1. Cuando se declara un miembro de datos en una declaración de clase, la palabra clave **static** especifica que todas las instancias de la clase comparten una copia del miembro. Un miembro de datos estático se debe definir en el ámbito de archivo. Un miembro de datos entero que se declara como **const static** puede tener un inicializador.

1. Cuando se declara una función miembro en una declaración de clase, la palabra clave **static** especifica que todas las instancias de la clase comparten la función. Una función miembro estática no puede tener acceso a un miembro de instancia porque la función no tiene un puntero **this** implícito. Para tener acceso a un miembro de instancia, declare la función con un parámetro que sea un puntero o referencia de instancia.

1. No puede declarar los miembros de una unión como estáticos. Sin embargo, una Unión anónima declarada globalmente debe declararse explícitamente como **static**.

Este ejemplo muestra cómo una variable declarada **static** en una función conserva su estado entre las llamadas a esa función.

```cpp
// static1.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
void showstat( int curr ) {
   static int nStatic;    // Value of nStatic is retained
                          // between each function call
   nStatic += curr;
   cout << "nStatic is " << nStatic << endl;
}

int main() {
   for ( int i = 0; i < 5; i++ )
      showstat( i );
}
```

```Output
nStatic is 0
nStatic is 1
nStatic is 3
nStatic is 6
nStatic is 10
```

En este ejemplo se muestra el uso de **static** en una clase.

```cpp
// static2.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class CMyClass {
public:
   static int m_i;
};

int CMyClass::m_i = 0;
CMyClass myObject1;
CMyClass myObject2;

int main() {
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject1.m_i = 1;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject2.m_i = 2;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   CMyClass::m_i = 3;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;
}
```

```Output
0
0
1
1
2
2
3
3
```

En este ejemplo se muestra una variable local declarada como **static** en una función miembro. La variable estática está disponible para el programa completo; todas las instancias del tipo comparten la misma copia de la variable estática.

```cpp
// static3.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
struct C {
   void Test(int value) {
      static int var = 0;
      if (var == value)
         cout << "var == value" << endl;
      else
         cout << "var != value" << endl;

      var = value;
   }
};

int main() {
   C c1;
   C c2;
   c1.Test(100);
   c2.Test(100);
}
```

```Output
var != value
var == value
```

A partir de C ++ 11, se garantiza que la inicialización de la variable local estática sea segura para subprocesos. Esta característica se denomina a veces *estáticas mágicas*. Sin embargo, en una aplicación con subprocesamiento múltiple todas las asignaciones posteriores deben estar sincronizadas. La característica de inicialización estática segura para subprocesos se puede deshabilitar mediante la marca [/Zc: threadSafeInit-](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) para evitar la realización de una dependencia en CRT.

## <a name="extern"></a>externas

Los objetos y las variables declarados como **extern** declaran un objeto que se define en otra unidad de traducción o en un ámbito de inclusión como una vinculación externa. Para obtener más información, consulte las [unidades de traducción y la vinculación](program-and-linkage-cpp.md)de [extern](extern-cpp.md) .

## <a name="thread_local"></a>thread_local (C++ 11)

Una variable declarada con el especificador **thread_local** solo es accesible en el subproceso en el que se crea. La variable se crea cuando se crea el subproceso y se destruye cuando se destruye el subproceso. Cada subproceso tiene su propia copia de la variable. En Windows, **thread_local** es funcionalmente equivalente al atributo de [__declspec (subproceso)](../cpp/thread.md) específico de Microsoft.

```cpp
thread_local float f = 42.0; // Global namespace. Not implicitly static.

struct S // cannot be applied to type definition
{
    thread_local int i; // Illegal. The member must be static.
    thread_local static char buf[10]; // OK
};

void DoSomething()
{
    // Apply thread_local to a local variable.
    // Implicitly "thread_local static S my_struct".
    thread_local S my_struct;
}
```

Aspectos que se deben tener en cuenta sobre el especificador **thread_local** :

- Es posible que las variables locales de subproceso inicializadas dinámicamente en archivos dll no se inicialicen correctamente en todos los subprocesos de llamada. Para obtener más información, consulte el [subproceso](thread.md).

- El especificador de **thread_local** se puede combinar con **static** o **extern**.

- Solo puede aplicar **thread_local** a declaraciones y definiciones de datos. no se puede usar **thread_local** en declaraciones o definiciones de función.

- Solo puede especificar **thread_local** en elementos de datos con duración de almacenamiento estática. Esto incluye objetos de datos globales (tanto **estáticos** como **externos**), objetos estáticos locales y miembros de datos estáticos de clases. Cualquier variable local declarada **thread_local** es implícitamente estática Si no se proporciona ninguna otra clase de almacenamiento; en otras palabras, en el ámbito de bloque **thread_local** es equivalente a `thread_local static`.

- Debe especificar **thread_local** para la declaración y la definición de un objeto local de subproceso, ya sea que la declaración y la definición se produzcan en el mismo archivo o en archivos independientes.

En Windows, **thread_local** es funcionalmente equivalente a [__declspec (Thread)](../cpp/thread.md) , salvo que **__declspec (Thread)** se puede aplicar a una definición de tipo y es válido en código de C. Siempre que sea posible, utilice **thread_local** porque forma parte del C++ estándar y, por lo tanto, es más portátil.

##  <a name="register"></a>el

**Visual Studio 2017 versión 15,3 y posterior** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)): la palabra clave **Register** ya no es una clase de almacenamiento admitida. La palabra clave todavía está reservada en el estándar para su uso futuro.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>Ejemplo: inicialización automática frente a inicialización estática

Una variable o un objeto automático local se inicializa cada vez que el flujo de control alcanza su definición. Una variable o un objeto estático local se inicializa la primera vez que el flujo de control alcanza su definición.

Considere el ejemplo siguiente, que define una clase que registra la inicialización y la destrucción de objetos y, a continuación, define tres objetos, `I1`, `I2` e `I3`:

```cpp
// initialization_of_objects.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>
using namespace std;

// Define a class that logs initializations and destructions.
class InitDemo {
public:
    InitDemo( const char *szWhat );
    ~InitDemo();

private:
    char *szObjName;
    size_t sizeofObjName;
};

// Constructor for class InitDemo
InitDemo::InitDemo( const char *szWhat ) :
    szObjName(NULL), sizeofObjName(0) {
    if ( szWhat != 0 && strlen( szWhat ) > 0 ) {
        // Allocate storage for szObjName, then copy
        // initializer szWhat into szObjName, using
        // secured CRT functions.
        sizeofObjName = strlen( szWhat ) + 1;

        szObjName = new char[ sizeofObjName ];
        strcpy_s( szObjName, sizeofObjName, szWhat );

        cout << "Initializing: " << szObjName << "\n";
    }
    else {
        szObjName = 0;
    }
}

// Destructor for InitDemo
InitDemo::~InitDemo() {
    if( szObjName != 0 ) {
        cout << "Destroying: " << szObjName << "\n";
        delete szObjName;
    }
}

// Enter main function
int main() {
    InitDemo I1( "Auto I1" ); {
        cout << "In block.\n";
        InitDemo I2( "Auto I2" );
        static InitDemo I3( "Static I3" );
    }
    cout << "Exited block.\n";
}
```

```Output
Initializing: Auto I1
In block.
Initializing: Auto I2
Initializing: Static I3
Destroying: Auto I2
Exited block.
Destroying: Auto I1
Destroying: Static I3
```

En este ejemplo se muestra cómo y cuándo se inicializan los objetos `I1`, `I2`y `I3` y cuándo se destruyen.

Hay varios puntos que se deben tener en cuenta sobre el programa:

- En primer lugar, `I1` e `I2` se destruyen automáticamente cuando el flujo de control sale del bloque en el que están definidos.

- En segundo lugar, en C++, no es necesario declarar objetos o variables al principio de un bloque. Además, estos objetos se inicializan solo cuando el flujo de control alcanza sus definiciones. (`I2` y `I3` son ejemplos de estas definiciones). El resultado se muestra exactamente cuando se inicializan.

- Por último, las variables locales estáticas como `I3` conservan sus valores mientras dura el programa, pero se destruyen cuando el programa finaliza.

## <a name="see-also"></a>Consulte también

[Declaraciones y definiciones](../cpp/declarations-and-definitions-cpp.md)