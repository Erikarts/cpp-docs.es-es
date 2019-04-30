---
title: basic_ostream (Clase)
ms.date: 03/27/2019
f1_keywords:
- ostream/std::basic_ostream
- ostream/std::basic_ostream::flush
- ostream/std::basic_ostream::put
- ostream/std::basic_ostream::seekp
- ostream/std::basic_ostream::sentry
- ostream/std::basic_ostream::swap
- ostream/std::basic_ostream::tellp
- ostream/std::basic_ostream::write
helpviewer_keywords:
- std::basic_ostream [C++]
- std::basic_ostream [C++], flush
- std::basic_ostream [C++], put
- std::basic_ostream [C++], seekp
- std::basic_ostream [C++], sentry
- std::basic_ostream [C++], swap
- std::basic_ostream [C++], tellp
- std::basic_ostream [C++], write
ms.assetid: 5baadc65-b662-4fab-8c9f-94457c58cda1
ms.openlocfilehash: 64a32513e9dc151e64fccdb0ef678a75588f0a41
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371665"
---
# <a name="basicostream-class"></a>basic_ostream (Clase)

Esta clase de plantilla describe un objeto que controla la inserción de elementos y objetos codificados en un búfer de secuencia con elementos de tipo `Elem`, también conocida como [char_type](../standard-library/basic-ios-class.md#char_type), cuyos rasgos de caracteres están determinados por la clase `Tr`, también conocida como [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ostream : virtual public basic_ios<Elem, Tr>
```

### <a name="parameters"></a>Parámetros

*Elem*<br/>
Objeto `char_type`.

*Tr*<br/>
El carácter `traits_type`.

## <a name="remarks"></a>Comentarios

La mayoría de las funciones miembro que sobrecargan [operator<<](#basic_ostream_operator_lt_lt) son funciones de salida con formato. Siguen el patrón:

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{try
{<convert and insert elements
    accumulate flags in state> }
    catch (...)
{try
{setstate(badbit);

}
    catch (...)
{}
    if ((exceptions()& badbit) != 0)
    throw; }}
width(0);
// Except for operator<<(Elem)
setstate(state);

return (*this);
```

Otras dos funciones miembro son funciones de salida sin formato. Siguen el patrón:

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (!ok)
    state |= badbit;
else
{try
{<obtain and insert elements
    accumulate flags in state> }
    catch (...)
{try
{setstate(badbit);

}
    catch (...)
{}
    if ((exceptions()& badbit) != 0)
    throw; }}
setstate(state);

return (*this);
```

Ambos grupos de funciones llaman a [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**) si encuentran un error al insertar elementos.

Un objeto de clase basic_istream\< **Elem**, **Tr**> solo almacena un objeto base público virtual de clase [basic_ios](../standard-library/basic-ios-class.md)**\<Elem**, **Tr>**.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [basic_ofstream (Clase)](../standard-library/basic-ofstream-class.md) para obtener más información sobre los flujos de salida.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_ostream](#basic_ostream)|Construye un objeto `basic_ostream`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[flush](#flush)|Vacía el búfer.|
|[put](#put)|Coloca un carácter en una secuencia.|
|[seekp](#seekp)|Restablece la posición en el flujo de salida.|
|[sentry](#sentry)|La clase anidada describe un objeto cuya declaración estructura las funciones de salida con y sin formato.|
|[swap](#swap)|Cambia los valores de este objeto `basic_ostream` por los del objeto `basic_ostream` proporcionado.|
|[tellp](#tellp)|Notifica la posición en el flujo de salida.|
|[write](#write)|Coloca los caracteres en una secuencia.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator=](#op_eq)|Asigna el valor del parámetro de objeto `basic_ostream` a este objeto.|
|[operator<<](#basic_ostream_operator_lt_lt)|Escribe en la secuencia.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<ostream>

**Espacio de nombres:** std

## <a name="basic_ostream"></a>  basic_ostream::basic_ostream

Construye un objeto `basic_ostream`.

```cpp
explicit basic_ostream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_ostream(basic_ostream&& right);
```

### <a name="parameters"></a>Parámetros

*strbuf*<br/>
Objeto de tipo [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*<br/>
**True** si se trata de un flujo estándar; de lo contrario, **false**.

*right*<br/>
Referencia a un valor R a un objeto de tipo `basic_ostream`.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa la clase base al llamar a [init](../standard-library/basic-ios-class.md#init)(`strbuf`). El segundo constructor inicializa la clase base al llamar a [basic_ios::move](../standard-library/basic-ios-class.md#move)`(right)`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) para obtener más información sobre los flujos de salida.

## <a name="flush"></a>  basic_ostream::flush

Vacía el búfer.

```cpp
basic_ostream<Elem, Tr>& flush();
```

### <a name="return-value"></a>Valor devuelto

Referencia al objeto basic_ostream.

### <a name="remarks"></a>Comentarios

Si [rdbuf](../standard-library/basic-ios-class.md#rdbuf) no es un puntero nulo, la función llama a **rdbuf->**[pubsync](../standard-library/basic-streambuf-class.md#pubsync). Si eso devuelve -1, la función llama a [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**). Devuelve **\*this**.

### <a name="example"></a>Ejemplo

```cpp
// basic_ostream_flush.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "test";
   cout.flush();
}
```

```Output
test
```

## <a name="basic_ostream_operator_lt_lt"></a>  basic_ostream::operator&lt;&lt;

Escribe en la secuencia.

```cpp
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& (* Pfn)(basic_ostream<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(
    ios_base& (* Pfn)(ios_base&));

basic_ostream<Elem, Tr>& operator<<(
    basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
basic_ostream<Elem, Tr>& operator<<(bool val);
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int __w64  val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long __w64  val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```

### <a name="parameters"></a>Parámetros

*Pfn*<br/>
Puntero de función.

*strbuf*<br/>
Puntero a un objeto `stream_buf` .

*val*<br/>
Elemento que se va a escribir en el flujo.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto basic_ostream.

### <a name="remarks"></a>Comentarios

El \<ostream > encabezado también define varios operadores de inserción globales. Para obtener más información, consulte [operador <<](../standard-library/ostream-operators.md#op_lt_lt).

La primera función miembro garantiza que una expresión de formato `ostr << endl` llamadas [endl](../standard-library/ostream-functions.md#endl)**(ostr)** y, a continuación, devuelve  **\*esto**. Las funciones segunda y tercera garantizan que los demás manipuladores, como [hex](../standard-library/ios-functions.md#hex), se comporten de forma similar. Las funciones restantes son todas funciones de salida con formato.

La función

```cpp
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```

extrae elementos de *strbuf*si *strbuf* no es un puntero nulo y se insertan. La extracción se detiene al final del archivo o si una extracción inicia una excepción (que se vuelve a iniciar). También se detiene, sin extraer el elemento en cuestión, si se produce un error en una inserción. Si la función no inserta ningún elemento, o si una extracción inicia una excepción, la función llama a [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). En cualquier caso, la función devuelve **\*this**.

La función

```cpp
basic_ostream<Elem, Tr>& operator<<(bool val);
```

Convierte `_Val` en un campo booleano y se inserta mediante una llamada a [use_facet](../standard-library/basic-filebuf-class.md#open)**< num_put\<Elem, OutIt >**`(`[getloc](../standard-library/ios-base-class.md#getloc)). [put](#put)(**OutIt**([rdbuf](../standard-library/basic-ios-class.md#rdbuf)), **\*this**, `getloc`, **val**). En este caso, `OutIt` se define como [ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md)**\<Elem, Tr >**. La función devuelve **\*this**.

Las funciones

```cpp
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```

cada convert *val* a un valor numérico del campo y lo insertan al llamar a **use_facet < num_put\<Elem, OutIt >**(`getloc`). **put**(**OutIt**(`rdbuf`), **\*this**, `getloc`, **val**). Aquí, **OutIt** se define como **ostreambuf_iterator\<Elem, Tr>**. La función devuelve **\*this**.

Las funciones

```cpp
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```

cada convert *val* a un valor numérico del campo y lo insertan al llamar a **use_facet < num_put\<Elem, OutIt >**(`getloc`)**. Coloque**(**OutIt**(`rdbuf`),  **\*esto**, `getloc`, **val**). Aquí, **OutIt** se define como **ostreambuf_iterator\<Elem, Tr>**. La función devuelve **\*this**.

### <a name="example"></a>Ejemplo

```cpp
// basic_ostream_op_write.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_ostream<char, char_traits<char> >& somefunc(basic_ostream<char, char_traits<char> > &i)
{
    if (i == cout)
    {
        i << "i is cout" << endl;
    }
    return i;
}

class CTxtStreambuf : public basic_streambuf< char, char_traits< char > >
{
public:
    CTxtStreambuf(char *_pszText)
    {
        pszText = _pszText;
        setg(pszText, pszText, pszText + strlen(pszText));
    };
    char *pszText;
};

int main()
{
    cout << somefunc;
    cout << 21 << endl;

    hex2(cout);
    cout << 21 << endl;

    CTxtStreambuf f("text in streambuf");
    cout << &f << endl;
}
```

## <a name="op_eq"></a>  basic_ostream::operator=

Asigna valores del parámetro de objeto `basic_ostream` proporcionado a este objeto.

```cpp
basic_ostream& operator=(basic_ostream&& right);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
Referencia `rvalue` a un objeto `basic_ostream`.

### <a name="remarks"></a>Comentarios

El operador miembro llama a swap `(right)`.

## <a name="put"></a>  basic_ostream::put

Coloca un carácter en una secuencia.

```cpp
basic_ostream<Elem, Tr>& put(char_type _Ch);
```

### <a name="parameters"></a>Parámetros

*_Ch*<br/>
Un carácter.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto basic_ostream.

### <a name="remarks"></a>Comentarios

La función de salida sin formato inserta el elemento *_Ch*. Devuelve **\*this**.

### <a name="example"></a>Ejemplo

```cpp
// basic_ostream_put.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout.put( 'v' );
   cout << endl;
   wcout.put( L'l' );
}
```

```Output
v
l
```

## <a name="seekp"></a>  basic_ostream::seekp

Restablece la posición en el flujo de salida.

```cpp
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```

### <a name="parameters"></a>Parámetros

*_Pos*<br/>
Posición en el flujo.

*_Off*<br/>
El desplazamiento relativo a *_Way*.

*_Way*<br/>
Una de las enumeraciones [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir).

### <a name="return-value"></a>Valor devuelto

Referencia al objeto basic_ostream.

### <a name="remarks"></a>Comentarios

Si [producirá un error en](../standard-library/basic-ios-class.md#fail) es **false**, las llamadas a funciones miembro primera **newpos =** [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)(*_Pos*), para algunos `pos_type` objeto temporal `newpos`. Si `fail` es false, la segunda función llama a **newpos = rdbuf - >** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(*_Off, _Way*). En cualquier caso, si (`off_type`)**newpos ==** (`off_type`)(-1) (se produce un error en la operación de posicionamiento), la función llama a **istr.**[setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). Ambas funciones devuelven **\*this**.

### <a name="example"></a>Ejemplo

```cpp
// basic_ostream_seekp.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main()
{
    using namespace std;
    ofstream x("basic_ostream_seekp.txt");
    streamoff i = x.tellp();
    cout << i << endl;
    x << "testing";
    i = x.tellp();
    cout << i << endl;
    x.seekp(2);   // Put char in third char position in file
    x << " ";

    x.seekp(2, ios::end);   // Put char two after end of file
    x << "z";
}
```

```Output
0
7
```

## <a name="sentry"></a>  basic_ostream::sentry

La clase anidada describe un objeto cuya declaración estructura las funciones de salida con y sin formato.

class sentry { public: explicit sentry(basic_ostream\<Elem, Tr>& _Ostr); operator bool() const; ~sentry(); };

### <a name="remarks"></a>Comentarios

La clase anidada describe un objeto cuya declaración estructura las funciones de salida con y sin formato. Si **ostr.**[good](../standard-library/basic-ios-class.md#good) es **True** y **ostr.**[tie](../standard-library/basic-ios-class.md#tie) no es un puntero nulo, el constructor llama a **ostr.tie->**[flush](#flush). El constructor almacena el valor devuelto por `ostr.good` en `status`. Una llamada posterior a `operator bool` devuelve este valor almacenado.

Si `uncaught_exception` devuelve **False** y [flags](../standard-library/ios-base-class.md#flags) **&** [unitbuf](../standard-library/ios-functions.md#unitbuf) es distinto de cero, el destructor llama a [flush](#flush).

## <a name="swap"></a>  basic_ostream::swap

Cambia los valores de este objeto `basic_ostream` por los del objeto `basic_ostream` proporcionado.

```cpp
void swap(basic_ostream& right);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
Referencia a un objeto `basic_ostream`.

### <a name="remarks"></a>Comentarios

La función miembro llama a [basic_ios:: swap](../standard-library/basic-ios-class.md#swap) `(right)` para intercambiar el contenido de este objeto para el contenido de *derecho*.

## <a name="tellp"></a>  basic_ostream::tellp

Notifica la posición en el flujo de salida.

```cpp
pos_type tellp();
```

### <a name="return-value"></a>Valor devuelto

Posición en el flujo de salida.

### <a name="remarks"></a>Comentarios

Si [fail](../standard-library/basic-ios-class.md#fail) es **False**, la función miembro devuelve [rdbuf](../standard-library/basic-ios-class.md#rdbuf)**->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`, **in**). De lo contrario, devuelve `pos_type`(-1).

### <a name="example"></a>Ejemplo

Vea [seekp](#seekp) para obtener un ejemplo de uso de `tellp`.

## <a name="write"></a>  basic_ostream::write

Coloca caracteres en un flujo.

```cpp
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```

### <a name="parameters"></a>Parámetros

*count*<br/>
Recuento de caracteres que se van a colocar en el flujo.

*str*<br/>
Caracteres que se van a colocar en el flujo.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto basic_ostream.

### <a name="remarks"></a>Comentarios

El [función de salida sin formato](../standard-library/basic-ostream-class.md) inserta la secuencia de *recuento* elementos, empezando por *str*.

### <a name="example"></a>Ejemplo

Vea [streamsize](../standard-library/ios-typedefs.md#streamsize) para obtener un ejemplo de uso de `write`.

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>
