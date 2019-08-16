---
title: fpos (Clase)
ms.date: 03/27/2019
f1_keywords:
- iosfwd/std::fpos
- iosfwd/std::fpos::seekpos
- iosfwd/std::fpos::state
- iosfwd/std::fpos::operator streamoff
helpviewer_keywords:
- std::fpos [C++]
- std::fpos [C++], seekpos
- std::fpos [C++], state
ms.assetid: ffd0827c-fa34-47f4-b10e-5cb707fcde47
ms.openlocfilehash: 60d7d00e6b9426df9b3086d9b82deaf1fdd1463c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454147"
---
# <a name="fpos-class"></a>fpos (Clase)

La clase de plantilla describe un objeto que puede almacenar toda la información necesaria para restaurar un indicador de posición de archivo arbitraria en cualquier flujo. Un objeto de clase fpos\< **St**> almacena de forma efectiva objetos de al menos dos miembros:

- Un desplazamiento de bytes del tipo [streamoff](../standard-library/ios-typedefs.md#streamoff).

- Un estado de conversión, para su uso por parte de un objeto de la `St`clase basic_filebuf `mbstate_t`, de tipo, normalmente.

También puede almacenar una posición de archivo arbitraria, para su uso por un objeto de clase [basic_filebuf](../standard-library/basic-filebuf-class.md), del tipo `fpos_t`. Sin embargo, en un entorno con limitación de tamaño del archivo, puede que `streamoff` y `fpos_t` se usen a veces indistintamente. Para un entorno sin flujos que tengan una codificación dependiente del estado, `mbstate_t` puede en realidad estar sin usar. Por lo tanto, el número de objetos miembro almacenados puede variar.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Statetype>
class fpos
```

### <a name="parameters"></a>Parámetros

*Statetype*\
Información de estado.

### <a name="constructors"></a>Constructores

|Constructor|DESCRIPCIÓN|
|-|-|
|[fpos](#fpos)|Crea un objeto que contiene información sobre una posición (desplazamiento) en un flujo.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
|-|-|
|[seekpos](#seekpos)|Se usa de forma interna solo en la biblioteca estándar de C++. No llame este método desde el código.|
|[state](#state)|Establece o devuelve el estado de la conversión.|

### <a name="operators"></a>Operadores

|Operador|DESCRIPCIÓN|
|-|-|
|[operator!=](#op_neq)|Indicadores de posición de archivo de las pruebas para desigualdad.|
|[operator+](#op_add)|Incrementa un indicador de posición de archivo.|
|[operator+=](#op_add_eq)|Incrementa un indicador de posición de archivo.|
|[operator-](#operator-)|Disminuye un indicador de posición de archivo.|
|[operator-=](#operator-_eq)|Disminuye un indicador de posición de archivo.|
|[operator==](#op_eq_eq)|Indicadores de posición de archivo de las pruebas para igualdad.|
|[operador streamoff](#op_streamoff)|Convierte objetos de tipo `fpos` a objetos de tipo `streamoff`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<ios>

**Espacio de nombres:** std

## <a name="fpos"></a>  fpos::fpos

Crea un objeto que contiene información sobre una posición (desplazamiento) en un flujo.

```cpp
fpos(streamoff _Off = 0);

fpos(Statetype _State, fpos_t _Filepos);
```

### <a name="parameters"></a>Parámetros

*_Off*\
El desplazamiento en el flujo.

*_State*\
El estado inicial del objeto `fpos`.

*_Filepos*\
El desplazamiento en el flujo.

### <a name="remarks"></a>Comentarios

El primer constructor almacena el desplazamiento *_Off*, con respecto al principio del archivo y en el estado de conversión inicial (si es importante). Si *_Off* es-1, el objeto resultante representa una posición de flujo no válida.

El segundo constructor almacena un desplazamiento de cero y el objeto *_State*.

## <a name="op_neq"></a>  fpos::operator!=

Indicadores de posición de archivo de las pruebas para desigualdad.

```cpp
bool operator!=(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parámetros

*correcta*\
El indicador de posición de archivo con el que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**True** si los indicadores de posición de archivo no son iguales; en caso contrario, **False**.

### <a name="remarks"></a>Comentarios

La función miembro devuelve `!(*this == right)`.

### <a name="example"></a>Ejemplo

```cpp
// fpos_op_neq.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;

   fpos<int> pos1, pos2;
   ifstream file;
   char c;

   // Compare two fpos object
   if ( pos1 != pos2 )
      cout << "File position pos1 and pos2 are not equal" << endl;
   else
      cout << "File position pos1 and pos2 are equal" << endl;

   file.open( "fpos_op_neq.txt" );
   file.seekg( 0 );   // Goes to a zero-based position in the file
   pos1 = file.tellg( );
   file.get( c);
   cout << c << endl;

   // Increment pos1
   pos1 += 1;
   file.get( c );
   cout << c << endl;

   pos1 = file.tellg( ) - fpos<int>( 2);
   file.seekg( pos1 );
   file.get( c );
   cout << c << endl;

   // Increment pos1
   pos1 = pos1 + fpos<int>( 1 );
   file.get(c);
   cout << c << endl;

   pos1 -= fpos<int>( 2 );
   file.seekg( pos1 );
   file.get( c );
   cout << c << endl;

   file.close( );
}
```

## <a name="op_add"></a>  fpos::operator+

Incrementa un indicador de posición de archivo.

```cpp
fpos<Statetype> operator+(streamoff _Off) const;
```

### <a name="parameters"></a>Parámetros

*_Off*\
El desplazamiento por el que quiere incrementar el indicador de posición de archivo.

### <a name="return-value"></a>Valor devuelto

La posición en el archivo.

### <a name="remarks"></a>Comentarios

La función miembro devuelve **fpos(\*this) +=** `_Off`.

### <a name="example"></a>Ejemplo

Vea [operator!=](#op_neq) para obtener un ejemplo del uso de `operator+`.

## <a name="op_add_eq"></a>  fpos::operator+=

Incrementa un indicador de posición de archivo.

```cpp
fpos<Statetype>& operator+=(streamoff _Off);
```

### <a name="parameters"></a>Parámetros

*_Off*\
El desplazamiento por el que quiere incrementar el indicador de posición de archivo.

### <a name="return-value"></a>Valor devuelto

La posición en el archivo.

### <a name="remarks"></a>Comentarios

La función miembro agrega *_Off* al objeto miembro de desplazamiento almacenado y, a continuación, devuelve  **\*this**. Para el posicionamiento dentro de un archivo, el resultado es normalmente válido solo para flujos binarios que no tienen una codificación dependiente del estado.

### <a name="example"></a>Ejemplo

Vea [operator!=](#op_neq) para obtener un ejemplo del uso de `operator+=`.

## <a name="operator-"></a>  fpos::operator-

Disminuye un indicador de posición de archivo.

```cpp
streamoff operator-(const fpos<Statetype>& right) const;

fpos<Statetype> operator-(streamoff _Off) const;
```

### <a name="parameters"></a>Parámetros

*correcta*\
Posición de archivo.

*_Off*\
Desplazamiento del flujo.

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve `(streamoff)*this - (streamoff) right`. La segunda función miembro devuelve `fpos(*this) -= _Off`.

### <a name="example"></a>Ejemplo

Vea [operator!=](#op_neq) para obtener un ejemplo del uso de `operator-`.

## <a name="operator-_eq"></a>  fpos::operator-=

Disminuye un indicador de posición de archivo.

```cpp
fpos<Statetype>& operator-=(streamoff _Off);
```

### <a name="parameters"></a>Parámetros

*_Off*\
Desplazamiento del flujo.

### <a name="return-value"></a>Valor devuelto

La función miembro devuelve `fpos(*this) -= _Off`.

### <a name="remarks"></a>Comentarios

Para el posicionamiento dentro de un archivo, el resultado es normalmente válido solo para flujos binarios que no tienen una codificación dependiente del estado.

### <a name="example"></a>Ejemplo

Vea [operator!=](#op_neq) para obtener un ejemplo del uso de `operator-=`.

## <a name="op_eq_eq"></a>  fpos::operator==

Indicadores de posición de archivo de las pruebas para igualdad.

```cpp
bool operator==(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parámetros

*correcta*\
El indicador de posición de archivo con el que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**True** si los indicadores de posición de archivo son iguales; en caso contrario, **False**.

### <a name="remarks"></a>Comentarios

La función miembro devuelve `(streamoff)*this == (streamoff)right`.

### <a name="example"></a>Ejemplo

Vea [operator!=](#op_neq) para obtener un ejemplo del uso de `operator+=`.

## <a name="op_streamoff"></a>  fpos::operator streamoff

Convierta objetos de tipo `fpos` en objetos de tipo `streamoff`.

```cpp
operator streamoff() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el objeto miembro de desplazamiento almacenado y cualquier desplazamiento adicional almacenado como parte del objeto miembro `fpos_t`.

### <a name="example"></a>Ejemplo

```cpp
// fpos_op_streampos.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   streamoff s;
   ofstream file( "rdbuf.txt");

   fpos<mbstate_t> f = file.tellp( );
   // Is equivalent to ..
   // streampos f = file.tellp( );
   s = f;
   cout << s << endl;
}
```

```Output
0
```

## <a name="seekpos"></a>  fpos::seekpos

Este método se usa de forma interna solo en la biblioteca estándar de C++. No llame este método desde el código.

```cpp
fpos_t seekpos() const;
```

## <a name="state"></a>  fpos::state

Establece o devuelve el estado de la conversión.

```cpp
Statetype state() const;

void state(Statetype _State);
```

### <a name="parameters"></a>Parámetros

*_State*\
El nuevo estado de conversión.

### <a name="return-value"></a>Valor devuelto

El estado de conversión.

### <a name="remarks"></a>Comentarios

La primera función miembro devuelve el valor almacenado en el `St` objeto de miembro. La segunda función miembro almacena *_State* en el `St` objeto miembro.

### <a name="example"></a>Ejemplo

```cpp
// fpos_state.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main() {
   using namespace std;
   streamoff s;
   ifstream file( "fpos_state.txt" );

   fpos<mbstate_t> f = file.tellg( );
   char ch;
   while ( !file.eof( ) )
      file.get( ch );
   s = f;
   cout << f.state( ) << endl;
   f.state( 9 );
   cout << f.state( ) << endl;
}
```

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programación con iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)
