---
title: num_put (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_put
- locale/std::num_put::char_type
- locale/std::num_put::iter_type
- locale/std::num_put::do_put
- locale/std::num_put::put
helpviewer_keywords:
- std::num_put [C++]
- std::num_put [C++], char_type
- std::num_put [C++], iter_type
- std::num_put [C++], do_put
- std::num_put [C++], put
ms.assetid: 36c5bffc-8283-4201-8ed4-78c4d81f8a17
ms.openlocfilehash: 49d76c5d553054934907cd2ddc0b7fd1f8b1e998
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687636"
---
# <a name="num_put-class"></a>num_put (Clase)

Una plantilla de clase que describe un objeto que puede actuar como una faceta de configuración regional para controlar las conversiones de valores numéricos en secuencias de tipo `CharType`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class num_put : public locale::facet;
```

### <a name="parameters"></a>Parámetros

@No__t_1 *CharType*
Tipo usado dentro de un programa para codificar los caracteres de una configuración regional.

@No__t_1 *OutputIterator*
Tipo de iterador en el que las funciones numeric put escriben sus resultados.

## <a name="remarks"></a>Comentarios

Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[num_put](#num_put)|Constructor para los objetos de tipo `num_put`.|

### <a name="typedefs"></a>Definiciones de tipo

|Nombre de tipo|Descripción|
|-|-|
|[char_type](#char_type)|Tipo que se usa para describir un carácter empleado por una configuración regional.|
|[iter_type](#iter_type)|Tipo que describe un iterador de salida.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[do_put](#do_put)|Función virtual a la que se llama a para convertir un número en una secuencia de `CharType` que representa el número con formato para una configuración regional especificada.|
|[put](#put)|Convierte un número en una secuencia de `CharType` que representa el número con formato para una configuración regional especificada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="char_type"></a> num_put::char_type

Tipo que se usa para describir un carácter empleado por una configuración regional.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `CharType`.

## <a name="do_put"></a> num_put::do_put

Función virtual a la que se llama a para convertir un número en una secuencia de `CharType` que representa el número con formato para una configuración regional especificada.

```cpp
virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const long long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const unsigned long long val) const;
```

### <a name="parameters"></a>Parámetros

*siguiente* \
Un iterador que se dirige al primer elemento de la cadena insertada.

@No__t_1 *_Iosbase*
Ha especificado la secuencia que contiene la configuración regional con la faceta numpunct usada para puntuar la salida y marcas para aplicar formato a la salida.

@No__t_1 *_Fill*
Un carácter que se usa para el espaciado.

\ *Val*
El número o tipo booleano del que se va a obtener la salida.

### <a name="return-value"></a>Valor devuelto

Un iterador de salida que se dirige a la posición siguiente del último elemento que se ha producido.

### <a name="remarks"></a>Comentarios

La primera función miembro virtual protegida genera elementos secuenciales a partir de la *siguiente* para generar un campo de salida de entero a partir del valor de *Val*. La función devuelve un iterador que designa el lugar siguiente para insertar un elemento más allá del campo de salida numérico entero que se ha generado.

El campo de salida entero se genera mediante las mismas reglas utilizadas por las funciones de impresión para generar una serie de elementos **Char** en un archivo. Se supone que cada elemento char de este tipo se asigna a un elemento equivalente de tipo `CharType` mediante una asignación simple, uno a uno. Sin embargo, cuando una función de impresión rellena un campo con espacios o con el dígito 0, en su lugar `do_put` usa `fill`. La especificación de conversión de impresión equivalente se determina de la manera siguiente:

- Si **iosbase**. [flags](../standard-library/ios-base-class.md#flags)  &  `ios_base::basefield`  ==  `ios_base::`[Oct](../standard-library/ios-functions.md#oct), la especificación de conversión es `lo`.

- Si **iosbase. flags**  & **ios_base:: basefield**  ==  `ios_base::`[Hex](../standard-library/ios-functions.md#hex), la especificación de conversión se `lx`.

- De otro modo, la especificación de conversión es `ld`.

Si **iosbase**. [width](../standard-library/ios-base-class.md#width) es distinto de cero, se antepone un ancho de campo de este valor. Entonces, la función llama a **iosbase**. **width**(0) para restablecer el ancho de campo a cero.

El relleno solo se produce si el número mínimo de elementos *N* necesarios para especificar el campo de salida es inferior a **iosbase**. [width](../standard-library/ios-base-class.md#width). Dicho relleno consta de una secuencia de *N*  -  copias de**ancho** de **relleno**. Después, el relleno se produce de la manera siguiente:

- Si **iosbase**. **flags**  &  `ios_base::adjustfield`  ==  `ios_base::`[izquierda](../standard-library/ios-functions.md#left), se antepone la marca **-** . (El relleno se produce después del texto generado).

- Si **iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[internal](../standard-library/ios-functions.md#internal), se antepone la marca **0**. (Para un campo de salida numérico, el relleno se produce donde las funciones de impresión rellenan con 0).

- De otro modo, no se antepone ninguna marca adicional. (El relleno se produce antes de la secuencia generada).

Por último:

- Si **iosbase**. **flags** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) es distinto de cero, se antepone la marca **+** a la especificación de conversión.

- Si **iosbase**. **flags** & **ios_base::** [showbase](../standard-library/ios-functions.md#showbase) es distinto de cero, se antepone la marca **#** a la especificación de conversión.

El formato de un campo de salida numérico entero se determina por la [faceta de configuración regional](../standard-library/locale-class.md#facet_class)**fac** que se devuelve mediante la llamada a [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). De manera específica:

- **fac**. [grouping](../standard-library/numpunct-class.md#grouping) determina cómo se agrupan los dígitos a la izquierda de cualquier separador decimal

- **fac**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) determina la secuencia que separa grupos de dígitos a la izquierda de cualquier separador decimal

Si no se impone ninguna restricción de agrupación mediante **fac**. **grouping** (su primer elemento tiene el valor CHAR_MAX), entonces ninguna instancia de **fac**. `thousands_sep` se generan en el campo de salida. De otro modo, los separadores se insertan después de que se produzca la conversión de impresión.

La segunda función miembro virtual protegida:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    unsigned long val) const;
```

se comporta igual que la primera, excepto que reemplaza una especificación de conversión de `ld` por `lu`.

La tercera función miembro virtual protegida:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    double val) const;
```

se comporta igual que la primera, excepto que produce un campo de salida de punto flotante del valor de **val**. **fac**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) determina la secuencia que separa los dígitos enteros de los dígitos de fracción. La especificación de conversión de impresión equivalente se determina de la manera siguiente:

- Si **iosbase**. **marcas**  &  `ios_base::floatfield`  ==  `ios_base::`[fixed](../standard-library/ios-functions.md#fixed), la especificación de conversión es `lf`.

- Si **iosbase**. **flags** & **ios_base::floatfield** == `ios_base::`[scientific](../standard-library/ios-functions.md#scientific), la especificación de conversión es `le`. Si **iosbase**. **flags**  &  `ios_base::`[mayúsculas](../standard-library/ios-functions.md#uppercase) es distinto de cero, `e` se reemplaza por `E`.

- De otro modo, la especificación de conversión es **lg**. Si **iosbase**. **flags**  & **ios_base:: Uppercase** es distinto de cero, `g` se reemplaza por `G`.

Si **iosbase**. **flags** & **ios_base::fixed** es distinto de cero o si **iosbase**. [precision](../standard-library/ios-base-class.md#precision) es mayor que cero, una precisión con el valor **iosbase**. **precision** se antepone a la especificación de conversión. Cualquier relleno se comporta de la misma manera que para un campo de salida numérico entero. El carácter de relleno es **fill**. Por último:

- Si **iosbase**. **flags** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) es distinto de cero, se antepone la marca **+** a la especificación de conversión.

- Si **iosbase**. **flags** & `ios_base::`[showpoint](../standard-library/ios-functions.md#showpoint) es distinto de cero, se antepone la marca **#** a la especificación de conversión.

La cuarta función miembro virtual protegida:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

se comporta igual que la tercera, excepto que el calificador `l` en la especificación de conversión se reemplaza por `L`.

La quinta función miembro virtual protegida:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    const void* val) const;
```

se comporta igual que la primera, excepto que la especificación de conversión es `p` **,** además de cualquier calificador necesario para especificar el relleno.

La sexta función miembro virtual protegida:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    bool val) const;
```

se comporta igual que la primera, salvo que genera un campo de salida booleano de *Val*.

Un campo de salida booleano adopta una de dos formas. Si `iosbase.flags & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) es **false**, la función miembro devuelve `do_put(_Next, _Iosbase, _Fill, (long)val)`, que normalmente produce una secuencia generada de 0 (para **false**) o 1 (para **true**). De lo contrario, la secuencia generada es *FAC*. [falsename](../standard-library/numpunct-class.md#falsename) (para **false**) o *FAC*. [truename](../standard-library/numpunct-class.md#truename) (para **true**).

La séptima función miembro virtual protegida:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    long long val) const;
```

se comporta igual que la primera, excepto que reemplaza una especificación de conversión de `ld` por `lld`.

La octava función miembro virtual protegida:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    unsigned long long val) const;
```

se comporta igual que la primera, excepto que reemplaza una especificación de conversión de `ld` por `llu`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [put](#put), que llama a `do_put`.

## <a name="iter_type"></a> num_put::iter_type

Tipo que describe un iterador de salida.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla **OutputIterator**.

## <a name="num_put"></a> num_put::num_put

Constructor para los objetos de tipo `num_put`.

```cpp
explicit num_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parámetros

@No__t_1 *_Refs*
Valor entero que se usa para especificar el tipo de administración de memoria del objeto.

### <a name="remarks"></a>Comentarios

Los valores posibles para el parámetro *_Refs* y su importancia son:

- 0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.

- 1: la vigencia del objeto se debe administrar de manera manual.

- \> 1: estos valores no están definidos.

No es posible mostrar ejemplos directos, porque el destructor está protegido.

El constructor inicializa su objeto base con **locale::** [facet](../standard-library/locale-class.md#facet_class)(_ *Refs*).

## <a name="put"></a> num_put::put

Convierte un número en una secuencia de `CharType`s que representa el número con formato para una configuración regional especificada.

```cpp
iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Long long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Unsigned long long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;
```

### <a name="parameters"></a>Parámetros

\ de *destino*
Un iterador que se dirige al primer elemento de la cadena insertada.

@No__t_1 *_Iosbase*
Ha especificado la secuencia que contiene la configuración regional con la faceta numpunct usada para puntuar la salida y marcas para aplicar formato a la salida.

@No__t_1 *_Fill*
Un carácter que se usa para el espaciado.

\ *Val*
El número o tipo booleano del que se va a obtener la salida.

### <a name="return-value"></a>Valor devuelto

Un iterador de salida que se dirige a la posición siguiente del último elemento que se ha producido.

### <a name="remarks"></a>Comentarios

Todas las funciones miembro devuelven [do_put](#do_put)( `next`, `_Iosbase`, `_Fill`, `val`).

### <a name="example"></a>Ejemplo

```cpp
// num_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );
   basic_stringstream<char> psz2;
   ios_base::iostate st = 0;
   long double fVal;
   cout << "The thousands separator is: "
        << use_facet < numpunct <char> >(loc).thousands_sep( )
        << endl;

   psz2.imbue( loc );
   use_facet < num_put < char > >
      ( loc ).put(basic_ostream<char>::_Iter(psz2.rdbuf( ) ),
                    psz2, ' ', fVal=1000.67);

   if ( st & ios_base::failbit )
      cout << "num_put( ) FAILED" << endl;
   else
      cout << "num_put( ) = " << psz2.rdbuf( )->str( ) << endl;
}
```

```Output
The thousands separator is: .
num_put( ) = 1.000,67
```

## <a name="see-also"></a>Vea también

[\<locale>](../standard-library/locale.md)\
[facet (Clase)](../standard-library/locale-class.md#facet_class)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
