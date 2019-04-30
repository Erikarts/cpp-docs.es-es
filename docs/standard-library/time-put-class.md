---
title: time_put (Clase)
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put
- locale/std::time_put::char_type
- locale/std::time_put::iter_type
- locale/std::time_put::do_put
- locale/std::time_put::put
helpviewer_keywords:
- std::time_put [C++]
- std::time_put [C++], char_type
- std::time_put [C++], iter_type
- std::time_put [C++], do_put
- std::time_put [C++], put
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
ms.openlocfilehash: b9c6f8db26cdc67d3a1bc752b9b5eb31f7dc220b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411934"
---
# <a name="timeput-class"></a>time_put (Clase)

La clase de plantilla describe un objeto que puede actuar como una faceta de la configuración regional para controlar las conversiones de valores de hora en secuencias de tipo `CharType`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class time_put : public locale::facet;
```

### <a name="parameters"></a>Parámetros

*CharType*<br/>
Tipo usado dentro de un programa para codificar caracteres.

*OutputIterator*<br/>
El tipo de iterador en el que las funciones time put escriben sus resultados.

## <a name="remarks"></a>Comentarios

Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[time_put](#time_put)|Constructor para los objetos de tipo `time_put`.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[char_type](#char_type)|Tipo que se usa para describir un carácter empleado por una configuración regional.|
|[iter_type](#iter_type)|Tipo que describe un iterador de salida.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[do_put](#do_put)|Una función virtual que genera información de hora y fecha como una secuencia de `CharType`s.|
|[put](#put)|Genera información de hora y fecha como una secuencia de `CharType`s.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="char_type"></a>  time_put::char_type

Tipo que se usa para describir un carácter empleado por una configuración regional.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `CharType`.

## <a name="do_put"></a>  time_put::do_put

Una función virtual que genera información de hora y fecha como una secuencia de `CharType`s.

```cpp
virtual iter_type do_put(
    iter_type next,
    ios_base& _Iosbase,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;
```

### <a name="parameters"></a>Parámetros

*next*<br/>
Un iterador de salida en el que se va a insertar la secuencia de caracteres que representan la fecha y la hora.

*_Iosbase*<br/>
Sin usar.

*_Pt*<br/>
La información de fecha y hora que se va a representar.

*_Fmt*<br/>
El formato de la salida. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.

*_Mod*<br/>
Un modificador para el formato. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.

### <a name="return-value"></a>Valor devuelto

Un iterador a la primera posición después del último elemento insertado.

### <a name="remarks"></a>Comentarios

La función miembro virtual protegida genera elementos secuenciales, empezando por `next` de valores de hora almacenados en el objeto \* `_Pt`, del tipo `tm`. La función devuelve un iterador que designa el lugar siguiente para insertar un elemento más allá de la salida generada.

El resultado generado por las mismas reglas usadas por `strftime`, con un último argumento de *_Pt*, para generar una serie de **char** elementos en una matriz. Cada uno de estos **char** elemento se supone que se asigna a un elemento equivalente de tipo `CharType` mediante una asignación simple, uno a uno. Si *_Mod* es igual a cero, el formato eficaz es "%F", donde F es reemplazado por *_Fmt*. En caso contrario, el formato eficaz es "% MF", donde M es reemplazado por *_Mod*.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [put](#put), que llama a `do_put`.

## <a name="iter_type"></a>  time_put::iter_type

Tipo que describe un iterador de salida.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `OutputIterator`.

## <a name="put"></a>  time_put::put

Genera información de hora y fecha como una secuencia de `CharType`s.

```cpp
iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;

iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parámetros

*next*<br/>
Un iterador de salida en el que se va a insertar la secuencia de caracteres que representan la fecha y la hora.

*_Iosbase*<br/>
Sin usar.

*_Fill*<br/>
El carácter de tipo `CharType` usado para el espaciado.

*_Pt*<br/>
La información de fecha y hora que se va a representar.

*_Fmt*<br/>
El formato de la salida. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.

*_Mod*<br/>
Un modificador para el formato. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.

*first*<br/>
El principio de la cadena de formato para la salida. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.

*last*<br/>
El final de la cadena de formato para la salida. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.

### <a name="return-value"></a>Valor devuelto

Un iterador a la primera posición después del último elemento insertado.

### <a name="remarks"></a>Comentarios

La primera función miembro devuelve [do_put](#do_put)(`next`, `_Iosbase`, `_Fill`, `_Pt`, `_Fmt`, `_Mod`). La segunda función miembro copia en \* `next` ++ cualquier elemento en el intervalo [ `first`, `last`) que no sea un porcentaje (%). Para un porcentaje seguido de un carácter *C* en el intervalo [ `first`, `last`), la función evalúa en su lugar `next` = `do_put`( `next`, `_Iosbase`, `_Fill`, `_Pt`, *C*, 0) y omite *C*. Pero si *C* es un carácter calificador del conjunto EOQ#, seguido por un carácter `C2` en el intervalo [ `first`, `last`), la función evalúa en su lugar `next` = `do_put`( `next`, `_Iosbase`, `_Fill`, `_Pt`, `C2`, *C*) y omite `C2`.

### <a name="example"></a>Ejemplo

```cpp
// time_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   t.tm_hour = 5;
   t.tm_min = 30;
   t.tm_sec = 40;
   t.tm_year = 00;
   t.tm_mday = 4;
   t.tm_mon = 6;

   pszPutI.imbue( loc );
   char *pattern = "x: %X %x";
   use_facet <time_put <char> >
   (loc).put(basic_ostream<char>::_Iter(pszPutI.rdbuf( )),
          pszPutI, ' ', &t, pattern, pattern+strlen(pattern));

      cout << "num_put( ) = " << pszPutI.rdbuf( )->str( ) << endl;

      char strftimebuf[255];
      strftime(&strftimebuf[0], 255, pattern, &t);
      cout << "strftime( ) = " << &strftimebuf[0] << endl;
}
```

```Output
num_put( ) = x: 05:30:40 07/04/00
strftime( ) = x: 05:30:40 07/04/00
```

## <a name="time_put"></a>  time_put::time_put

Constructor para los objetos de tipo `time_put`.

```cpp
explicit time_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parámetros

*_Refs*<br/>
Valor entero que se usa para especificar el tipo de administración de memoria del objeto.

### <a name="remarks"></a>Comentarios

Los valores posibles de la *_Refs* parámetro y su importancia son:

- 0: La vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.

- 1: La duración del objeto debe administrarse manualmente.

- \> 1: Estos valores no están definidos.

El constructor inicializa su objeto base con [Locale:: Facet](../standard-library/locale-class.md#facet_class)(*_Refs*).

## <a name="see-also"></a>Vea también

[\<locale>](../standard-library/locale.md)<br/>
[time_base (Clase)](../standard-library/time-base-class.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
