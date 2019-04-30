---
title: Operadores &lt;new&gt;
ms.date: 11/04/2016
f1_keywords:
- new/std::operator delete
- new/std::operator new
ms.assetid: d1af4b56-9a95-4c65-ab01-bf43e982c7bd
ms.openlocfilehash: 87f7b6cfd6a06ab03b27ebe6aa4dd41b0b900673
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223693"
---
# <a name="ltnewgt-operators"></a>Operadores &lt;new&gt;

||||
|-|-|-|
|[operator delete](#op_delete)|[operator delete[]](#op_delete_arr)|[operator new](#op_new)|
|[operator new[]](#op_new_arr)|

## <a name="op_delete"></a> operator delete

Función a la que llama una expresión delete para cancelar la asignación de almacenamiento para objetos individuales.

```cpp
void operator delete(void* ptr) throw();

void operator delete(void *,
    void*) throw();

void operator delete(void* ptr,
    const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parámetros

*ptr*<br/>
El puntero cuyo valor se va a representar como no válido mediante la eliminación.

### <a name="remarks"></a>Comentarios

La primera función se llama mediante una expresión delete para representar el valor de *ptr* no válido. El programa puede definir una función con esta firma de función que reemplaza la versión predeterminada definida por la Biblioteca estándar de C++. El comportamiento necesario es aceptar un valor de *ptr* que es null o que se devolvió mediante una llamada anterior a [new (operador)](../standard-library/new-operators.md#op_new)(**size_t**).

El comportamiento predeterminado para un valor null de *ptr* es no hacer nada. Cualquier otro valor de *ptr* debe ser un valor devuelto anteriormente por una llamada como se describió anteriormente. El comportamiento predeterminado para dicho valor no NULL de *ptr* consiste en recuperar el almacenamiento asignado por la llamada anterior. No se especifica bajo qué condiciones parte o todo el almacenamiento recuperado se asigna mediante una llamada subsiguiente a `operator new`(**size_t**), o a cualquiera de `calloc`( **size_t**), `malloc`( **size_t**), o `realloc`( **void**<strong>\*</strong>, **size_t**).

La segunda función se llama mediante una expresión delete de colocación correspondiente a una expresión new del formulario **new**( **std::size_t**). No hace nada.

La tercera función se llama mediante una expresión delete de colocación correspondiente a una expresión new del formulario **new**( **std::size_t**, **conststd::nothrow_t&**). El programa puede definir una función con esta firma de función que reemplaza la versión predeterminada definida por la Biblioteca estándar de C++. El comportamiento necesario es aceptar un valor de `ptr` que es NULL o que se ha devuelto mediante una llamada previa a `operator new`( **size_t**). El comportamiento predeterminado consiste en evaluar **eliminar**(`ptr`).

### <a name="example"></a>Ejemplo

Consulte [new (operador)](../standard-library/new-operators.md#op_new) para obtener un ejemplo que usan **operador delete**.

## <a name="op_delete_arr"></a> operator delete[]

Función a la que llama una expresión delete para cancelar la asignación de almacenamiento para una matriz de objetos.

```cpp
void operator delete[](void* ptr) throw();

void operator delete[](void *,
    void*) throw();

void operator delete[](void* ptr,
    const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parámetros

*ptr*<br/>
El puntero cuyo valor se va a representar como no válido mediante la eliminación.

### <a name="remarks"></a>Comentarios

La primera función se llama mediante un `delete[]` expresión para representar el valor de *ptr* no válido. La función se puede reemplazar porque el programa puede definir una función con esta firma de función que reemplaza la versión predeterminada definida por la Biblioteca estándar de C++. El comportamiento necesario es aceptar un valor de *ptr* que es null o que se devolvió mediante una llamada anterior a [new (operador)&#91;&#93;](../standard-library/new-operators.md#op_new_arr)(**size_t**). El comportamiento predeterminado para un valor null de *ptr* es no hacer nada. Cualquier otro valor de *ptr* debe ser un valor devuelto anteriormente por una llamada como se describió anteriormente. El comportamiento predeterminado para este tipo en un valor distinto de null de *ptr* consiste en recuperar el almacenamiento asignado por la llamada anterior. No se especifica bajo qué condiciones parte o todo el almacenamiento recuperado se asigna mediante una llamada subsiguiente a [new (operador)](../standard-library/new-operators.md#op_new)(**size_t**), o a cualquiera de `calloc`(**size_t**), `malloc`(**size_t**), o `realloc`( **void**<strong>\*</strong>, **size_t**) .

La segunda función llama a una selección de ubicación `delete[]` expresión correspondiente a un `new[]` expresión de formato `new[]`(**std:: size_t**). No hace nada.

La tercera función se llama mediante una expresión delete de colocación correspondiente a una expresión `new[]` del formulario `new[]`( **std::size_t**, **const std::nothrow_t&**). El programa puede definir una función con esta firma de función que reemplaza la versión predeterminada definida por la Biblioteca estándar de C++. El comportamiento necesario es aceptar un valor de *ptr* que es null o que se devolvió mediante una llamada anterior al operador `new[]`(**size_t**). El comportamiento predeterminado es evaluar `delete[]`( `ptr`).

### <a name="example"></a>Ejemplo

Vea [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr) para obtener ejemplos del uso de `operator delete[]`.

## <a name="op_new"></a> operator new

La función a la que llama una expresión new para asignar el almacenamiento a objetos individuales.

```cpp
void* operator new(std::size_t count) throw(bad_alloc);

void* operator new(std::size_t count,
    const std::nothrow_t&) throw();

void* operator new(std::size_t count,
    void* ptr) throw();
```

### <a name="parameters"></a>Parámetros

*count*<br/>
El número de bytes de almacenamiento que se va a asignar.

*ptr*<br/>
El puntero que se va a devolver.

### <a name="return-value"></a>Valor devuelto

Un puntero a la dirección de bytes más baja del almacenamiento recién asignado. O *ptr*.

### <a name="remarks"></a>Comentarios

La primera función se llama mediante una expresión new para asignar `count` bytes de almacenamiento correctamente alineados para representar cualquier objeto de ese tamaño. El programa puede definir una función alternativa con esta firma de función que reemplaza la versión predeterminada definida por la Biblioteca estándar de C++ y así es reemplazable.

El comportamiento necesario es devolver un puntero no NULL solo si el almacenamiento puede asignarse como se ha solicitado. Cada asignación produce un puntero al almacenamiento separado de cualquier otro almacenamiento asignado. El orden y la contigüidad del almacenamiento asignado mediante llamadas sucesivas no se especifica. El valor inicial almacenado no se especifica. El puntero devuelto señala al inicio (dirección de bytes más baja) del almacenamiento asignado. Si count es cero, el valor devuelto no equivale a ningún otro valor devuelto por la función.

El comportamiento predeterminado es ejecutar un bucle. Dentro del bucle, la función primero intenta asignar el almacenamiento solicitado. No se especifica si el intento implica una llamada a `malloc`( **size_t**). Si el intento se realiza correctamente, la función devuelve un puntero al almacenamiento asignado. De otro modo, la función llama al [controlador nuevo](../standard-library/new-typedefs.md#new_handler) designado. Si la función a la que se ha llamado se devuelve, el bucle se repite. El bucle finaliza cuando se realiza correctamente un intento de asignar el almacenamiento solicitado o cuando una función a la que se ha llamado no se devuelve.

El comportamiento necesario de un controlador nuevo es realizar una de las siguientes operaciones:

- Hacer que más almacenamiento esté disponible para su asignación y, después, devolverlo.

- Llamar a **anular** o **salir**(`int`).

- Producir un objeto de tipo **bad_alloc.**

El comportamiento predeterminado de un [controlador nuevo](../standard-library/new-typedefs.md#new_handler) es producir un objeto de tipo `bad_alloc`. Un puntero NULL designa el controlador nuevo predeterminado.

El orden y la contigüidad del almacenamiento asignado mediante llamadas sucesivas a `operator new`(**size_t**) se especifica, como son los valores iniciales almacenados allí.

La segunda función se llama mediante una expresión new de colocación para asignar `count` bytes de almacenamiento correctamente alineados para representar cualquier objeto de ese tamaño. El programa puede definir una función alternativa con esta firma de función que reemplaza la versión predeterminada definida por la Biblioteca estándar de C++ y así es reemplazable.

El comportamiento predeterminado es devolver `operator new`(`count`) si esa función se realiza correctamente. De lo contrario, devuelve un puntero NULL.

La tercera función se llama mediante una expresión **new** de colocación, o el formulario **new** (*args*) T. Aquí, *args* consta de un puntero de objeto único. Esto puede ser útil para crear un objeto en una dirección conocida. La función devuelve *ptr*.

Para liberar almacenamiento asignado por **new (operador)**, llame a [operador delete](../standard-library/new-operators.md#op_delete).

Para obtener información sobre iniciar o no iniciar el comportamiento de new, vea [Operadores new y delete](../cpp/new-and-delete-operators.md).

### <a name="example"></a>Ejemplo

```cpp
// new_op_new.cpp
// compile with: /EHsc
#include<new>
#include<iostream>

using namespace std;

class MyClass
{
public:
   MyClass( )
   {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass( )
   {
      imember = 0; cout << "Destructing MyClass." << this << endl;
   };
   int imember;
};

int main( )
{
   // The first form of new delete
   MyClass* fPtr = new MyClass;
   delete fPtr;

   // The second form of new delete
   MyClass* fPtr2 = new( nothrow ) MyClass;
   delete fPtr2;

   // The third form of new delete
   char x[sizeof( MyClass )];
   MyClass* fPtr3 = new( &x[0] ) MyClass;
   fPtr3 -> ~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;
}
```

## <a name="op_new_arr"></a> operator new[]

La función de asignación a la que llama una expresión new para asignar el almacenamiento para una matriz de objetos.

```cpp
void* operator new[](std::size_t count) throw(std::bad_alloc);

void* operator new[](std::size_t count,
    const std::nothrow_t&) throw();

void* operator new[](std::size_t count,
    void* ptr) throw();
```

### <a name="parameters"></a>Parámetros

*count*<br/>
El número de bytes de almacenamiento que se va a asignar para el objeto de matriz.

*ptr*<br/>
El puntero que se va a devolver.

### <a name="return-value"></a>Valor devuelto

Un puntero a la dirección de bytes más baja del almacenamiento recién asignado. O *ptr*.

### <a name="remarks"></a>Comentarios

La primera función se llama mediante una expresión `new[]` para asignar `count` bytes de almacenamiento correctamente alineados para representar cualquier objeto de matriz de ese tamaño o de un tamaño menor. El programa puede definir una función con esta firma de función que reemplaza la versión predeterminada definida por la Biblioteca estándar de C++. El comportamiento necesario es el mismo que para [new (operador)](../standard-library/new-operators.md#op_new)(**size_t**). El comportamiento predeterminado es devolver `operator new`( `count`).

La segunda función se llama mediante una expresión `new[]` de colocación para asignar `count` bytes de almacenamiento correctamente alineados para representar cualquier objeto de matriz de ese tamaño. El programa puede definir una función con esta firma de función que reemplaza la versión predeterminada definida por la Biblioteca estándar de C++. El comportamiento predeterminado es devolver **operatornew**(`count`) si esa función se realiza correctamente. De lo contrario, devuelve un puntero NULL.

La tercera función se llama mediante una expresión `new[]` de colocación, o el formulario **new** ( *args*) **T**[ **N**]. Aquí, *args* consta de un puntero de objeto único. La función devuelve `ptr`.

Para liberar almacenamiento asignado por `operator new[]`, llame a [operator delete&#91;&#93;](../standard-library/new-operators.md#op_delete_arr).

Para obtener información sobre iniciar o no iniciar el comportamiento de new, vea [Operadores new y delete](../cpp/new-and-delete-operators.md).

### <a name="example"></a>Ejemplo

```cpp
// new_op_alloc.cpp
// compile with: /EHsc
#include <new>
#include <iostream>

using namespace std;

class MyClass {
public:
   MyClass() {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass() {
      imember = 0; cout << "Destructing MyClass." << this << endl;
      };
   int imember;
};

int main() {
   // The first form of new delete
   MyClass* fPtr = new MyClass[2];
   delete[ ] fPtr;

   // The second form of new delete
   char x[2 * sizeof( MyClass ) + sizeof(int)];

   MyClass* fPtr2 = new( &x[0] ) MyClass[2];
   fPtr2[1].~MyClass();
   fPtr2[0].~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;

   // The third form of new delete
   MyClass* fPtr3 = new( nothrow ) MyClass[2];
   delete[ ] fPtr3;
}
```

## <a name="see-also"></a>Vea también

[\<new>](../standard-library/new.md)<br/>
