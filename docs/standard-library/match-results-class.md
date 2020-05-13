---
title: match_results (Clase)
ms.date: 09/10/2018
f1_keywords:
- regex/std::match_results
helpviewer_keywords:
- match_results class
ms.assetid: b504fdca-e5dd-429d-9960-6e27c9167fa6
ms.openlocfilehash: 31154a38f8bbcb879fd871f1eb1bf5a4b15af79b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371018"
---
# <a name="match_results-class"></a>match_results (Clase)

Contiene una secuencia de subcoincidencias.

## <a name="syntax"></a>Sintaxis

```cpp
template <class BidIt, class Alloc>
class match_results
```

## <a name="parameters"></a>Parámetros

*BidIt*\
El tipo de iterador para subcoincidencias.

*Alloc*\
El tipo de un asignador para administrar el almacenamiento.

## <a name="remarks"></a>Observaciones

La plantilla de clase describe un objeto que controla una `sub_match<BidIt>` secuencia no modificable de elementos de tipo generados por una búsqueda de expresiones regulares. Cada elemento apunta a la subsecuencia que coincide con el grupo de capturas que corresponde a ese elemento.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[match_results](#match_results)|Construye el objeto.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[allocator_type](#allocator_type)|El tipo de un asignador para administrar el almacenamiento.|
|[char_type](#char_type)|El tipo de un elemento.|
|[const_iterator](#const_iterator)|El tipo de iterador constante para subcoincidencias.|
|[const_reference](#const_reference)|Tipo de una referencia const a un elemento.|
|[difference_type](#difference_type)|El tipo de diferencia de un iterador.|
|[Iterador](#iterator)|El tipo de iterador para subcoincidencias.|
|[Referencia](#reference)|El tipo de una referencia a un elemento.|
|[size_type](#size_type)|El tipo de recuento de subcoincidencias.|
|[string_type](#string_type)|El tipo de una cadena.|
|[value_type](#value_type)|El tipo de una subcoincidencia.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Comenzar](#begin)|Indica el principio de la secuencia de subcoincidencia.|
|[Vacío](#empty)|Comprueba que no haya subcoincidencias.|
|[Final](#end)|Designa el final de la secuencia de subcoincidencia.|
|[Formato](#format)|Subcoincidencias de formato.|
|[get_allocator](#get_allocator)|Devuelve el asignador almacenado.|
|[length](#length)|Devuelve la longitud de una subcoincidencia.|
|[max_size](#max_size)|Obtiene el número máximo de subcoincidencias.|
|[Posición](#position)|Permite obtener el desplazamiento inicial de un subgrupo.|
|[Prefijo](#prefix)|Obtiene la secuencia antes de la primera subcoincidencia.|
|[Tamaño](#size)|Número de recuentos de subcoincidencias.|
|[Str](#str)|Devuelve una subcoincidencia.|
|[suffix](#suffix)|Obtiene la secuencia después de la última subcoincidencia.|
|[swap](#swap)|Intercambia dos objetos match_results.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operador](#op_eq)|Copiar un objeto match_results.|
|[Operador\[\]](#op_at)|Permite acceder a un subobjeto.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<regex>

**Espacio de nombres:** std

## <a name="example"></a>Ejemplo

```cpp
// std__regex__match_results.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::cout << "prefix: matched == " << std::boolalpha
        << mr.prefix().matched
        << ", value == " << mr.prefix() << std::endl;
    std::cout << "whole match: " << mr.length() << " chars, value == "
        << mr.str() << std::endl;
    std::cout << "suffix: matched == " << std::boolalpha
        << mr.suffix().matched
        << ", value == " << mr.suffix() << std::endl;
    std::cout << std::endl;

    std::string fmt("\"c(a*)|(b)\" matched \"$&\"\n"
        "\"(a*)\" matched \"$1\"\n"
        "\"(b)\" matched \"$2\"\n");
    std::cout << mr.format(fmt) << std::endl;
    std::cout << std::endl;

    // index through submatches
    for (size_t n = 0; n < mr.size(); ++n)
    {
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha
            << mr[n].matched <<
            " at position " << mr.position(n) << std::endl;
        std::cout << "  " << mr.length(n)
            << " chars, value == " << mr[n] << std::endl;
    }
    std::cout << std::endl;

    // iterate through submatches
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)
    {
        std::cout << "next submatch: matched == " << std::boolalpha
            << it->matched << std::endl;
        std::cout << "  " << it->length()
            << " chars, value == " << *it << std::endl;
    }
    std::cout << std::endl;

    // other members
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;

    std::cmatch::allocator_type al = mr.get_allocator();
    std::cmatch::string_type str = std::string("x");
    std::cmatch::size_type maxsiz = mr.max_size();
    std::cmatch::char_type ch = 'x';
    std::cmatch::difference_type dif = mr.begin() - mr.end();
    std::cmatch::const_iterator cit = mr.begin();
    std::cmatch::value_type val = *cit;
    std::cmatch::const_reference cref = val;
    std::cmatch::reference ref = val;

    maxsiz = maxsiz;  // to quiet "unused" warnings
    if (ref == cref)
        ch = ch;
    dif = dif;

    return (0);
}
```

```Output
prefix: matched == true, value == x
whole match: 4 chars, value == caaa
suffix: matched == true, value == y

"c(a*)|(b)" matched "caaa"
"(a*)" matched "aaa"
"(b)" matched ""

submatch[0]: matched == true at position 1
  4 chars, value == caaa
submatch[1]: matched == true at position 2
  3 chars, value == aaa
submatch[2]: matched == false at position 6
  0 chars, value ==

next submatch: matched == true
  4 chars, value == caaa
next submatch: matched == true
  3 chars, value == aaa
next submatch: matched == false
  0 chars, value ==

empty == false
```

## <a name="match_resultsallocator_type"></a><a name="allocator_type"></a>match_results::allocator_type

El tipo de un asignador para administrar el almacenamiento.

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Observaciones

Typedef es un sinónimo del argumento de plantilla *Alloc*.

## <a name="match_resultsbegin"></a><a name="begin"></a>match_results::comenzar

Indica el principio de la secuencia de subcoincidencia.

```cpp
const_iterator begin() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador de acceso aleatorio que apunta al primer elemento de la secuencia (o más allá del final de una secuencia vacía).

## <a name="match_resultschar_type"></a><a name="char_type"></a>match_results::char_type

El tipo de un elemento.

```cpp
typedef typename iterator_traits<BidIt>::value_type char_type;
```

### <a name="remarks"></a>Observaciones

La definición de tipo es un sinónimo del tipo `iterator_traits<BidIt>::value_type`, que es el tipo de elemento de la secuencia de caracteres que se busca.

## <a name="match_resultsconst_iterator"></a><a name="const_iterator"></a>match_results::const_iterator

El tipo de iterador constante para subcoincidencias.

```cpp
typedef T0 const_iterator;
```

### <a name="remarks"></a>Observaciones

La definición de tipo describe un objeto que puede actuar como un iterador de acceso aleatorio para la secuencia controlada.

## <a name="match_resultsconst_reference"></a><a name="const_reference"></a>match_results::const_reference

Tipo de una referencia const a un elemento.

```cpp
typedef const typename Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Observaciones

La definición de tipo describe un objeto que puede actuar como referencia constante a un elemento de la secuencia controlada.

## <a name="match_resultsdifference_type"></a><a name="difference_type"></a>match_results::difference_type

El tipo de diferencia de un iterador.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Observaciones

La definición de tipo es un sinónimo del tipo `iterator_traits<BidIt>::difference_type`; describe un objeto que puede representar la diferencia entre dos iteradores que apuntan a elementos de la secuencia controlada.

## <a name="match_resultsempty"></a><a name="empty"></a>match_results::vacío

Comprueba que no haya subcoincidencias.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve true solo si hay error en la búsqueda de expresión regular.

## <a name="match_resultsend"></a><a name="end"></a>match_results::fin

Designa el final de la secuencia de subcoincidencia.

```cpp
const_iterator end() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador que apunta inmediatamente después del final de la secuencia.

## <a name="match_resultsformat"></a><a name="format"></a>match_results::formato

Subcoincidencias de formato.

```cpp
template <class OutIt>
OutIt format(OutIt out,
    const string_type& fmt, match_flag_type flags = format_default) const;

string_type format(const string_type& fmt, match_flag_type flags = format_default) const;
```

### <a name="parameters"></a>Parámetros

*OutIt*\
Tipo de iterador de salida.

*hacia fuera*\
Flujo de salida donde se va a escribir.

*Fmt*\
Formato de cadena.

*Banderas*\
Marcas de formato.

### <a name="remarks"></a>Observaciones

Cada función miembro genera texto con formato bajo el control del formato *fmt*. La primera función miembro escribe el texto con formato en la secuencia definida por su argumento *out* y devuelve *out*. La segunda función miembro devuelve un objeto de cadena que contiene una copia del texto con formato.

Para generar texto con formato El texto literal de la cadena de formato se copia normalmente en la secuencia de destino. Cada secuencia de escape de la cadena de formato se reemplaza por el texto que representa. Las marcas de formato pasadas a la función controlan los detalles de copiar y reemplazar.

## <a name="match_resultsget_allocator"></a><a name="get_allocator"></a>match_results::get_allocator

Devuelve el asignador almacenado.

```cpp
allocator_type get_allocator() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve una copia del objeto de asignador usado por `*this` para asignar sus objetos `sub_match`.

## <a name="match_resultsiterator"></a><a name="iterator"></a>match_results::iterator

El tipo de iterador para subcoincidencias.

```cpp
typedef const_iterator iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto que puede actuar como un iterador de acceso aleatorio de la secuencia controlada.

## <a name="match_resultslength"></a><a name="length"></a>match_results::longitud

Devuelve la longitud de una subcoincidencia.

```cpp
difference_type length(size_type sub = 0) const;
```

### <a name="parameters"></a>Parámetros

*Sub*\
El índice de la subcoincidencia.

### <a name="remarks"></a>Observaciones

La función miembro devuelve `(*this)[sub].length()`.

## <a name="match_resultsmatch_results"></a><a name="match_results"></a>match_results::match_results

Construye el objeto.

```cpp
explicit match_results(const Alloc& alloc = Alloc());

match_results(const match_results& right);
```

### <a name="parameters"></a>Parámetros

*Alloc*\
Objeto de asignador que se va a almacenar.

*Correcto*\
Objeto match_results que se va a copiar.

### <a name="remarks"></a>Observaciones

El primer constructor construye un objeto `match_results` que no contiene subcoincidencias. El segundo constructor `match_results` construye un objeto que es una copia de *right*.

## <a name="match_resultsmax_size"></a><a name="max_size"></a>match_results::max_size

Obtiene el número máximo de subcoincidencias.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve la longitud de la secuencia más larga que puede controlar el objeto.

## <a name="match_resultsoperator"></a><a name="op_eq"></a>match_results::operador ?

Copiar un objeto match_results.

```cpp
match_results& operator=(const match_results& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Objeto match_results que se va a copiar.

### <a name="remarks"></a>Observaciones

El operador miembro reemplaza la `*this` secuencia controlada por una copia de la secuencia controlada por *right*.

## <a name="match_resultsoperator"></a><a name="op_at"></a>match_results::operador[]

Permite acceder a un subobjeto.

```cpp
const_reference operator[](size_type n) const;
```

### <a name="parameters"></a>Parámetros

*N*\
Índice de la subcoincidencia.

### <a name="remarks"></a>Observaciones

La función miembro devuelve una referencia al elemento *n* de `sub_match` la `size() <= n` secuencia controlada, o una referencia a un objeto vacío si o si el grupo de captura *n* no formaba parte de la coincidencia.

## <a name="match_resultsposition"></a><a name="position"></a>match_results::position

Permite obtener el desplazamiento inicial de un subgrupo.

```cpp
difference_type position(size_type sub = 0) const;
```

### <a name="parameters"></a>Parámetros

*Sub*\
Índice de la subcoincidencia.

### <a name="remarks"></a>Observaciones

La función miembro devuelve `std::distance(prefix().first, (*this)[sub].first)`; es decir, la distancia desde el primer carácter de la secuencia de destino hasta el primer carácter de la subcoincidencia señalado por el elemento `n` de la secuencia controlada.

## <a name="match_resultsprefix"></a><a name="prefix"></a>match_results::prefix

Obtiene la secuencia antes de la primera subcoincidencia.

```cpp
const_reference prefix() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve una referencia a un objeto del tipo `sub_match<BidIt>` que apunta a la secuencia de caracteres que comienza en el inicio de la secuencia de destino y terminan en `(*this)[0].first`; es decir, señala el texto que precede a la subsecuencia coincidente.

## <a name="match_resultsreference"></a><a name="reference"></a>match_results::referencia

El tipo de una referencia a un elemento.

```cpp
typedef const_reference reference;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del tipo `const_reference`.

## <a name="match_resultssize"></a><a name="size"></a>match_results::tamaño

Número de recuentos de subcoincidencias.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve uno más que el número de grupos de captura en la expresión regular que se usó para la búsqueda o cero si no se hizo ninguna búsqueda.

## <a name="match_resultssize_type"></a><a name="size_type"></a>match_results::size_type

El tipo de recuento de subcoincidencias.

```cpp
typedef typename Alloc::size_type size_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del tipo `Alloc::size_type`.

## <a name="match_resultsstr"></a><a name="str"></a>match_results::str

Devuelve una subcoincidencia.

```cpp
string_type str(size_type sub = 0) const;
```

### <a name="parameters"></a>Parámetros

*Sub*\
Índice de la subcoincidencia.

### <a name="remarks"></a>Observaciones

La función miembro devuelve `string_type((*this)[sub])`.

## <a name="match_resultsstring_type"></a><a name="string_type"></a>match_results::string_type

El tipo de una cadena.

```cpp
typedef basic_string<char_type> string_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del tipo `basic_string<char_type>`.

## <a name="match_resultssuffix"></a><a name="suffix"></a>match_results::suffix

Obtiene la secuencia después de la última subcoincidencia.

```cpp
const_reference suffix() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve una referencia a un objeto del tipo `sub_match<BidIt>` que apunta a la secuencia de caracteres que comienza en `(*this)[size() - 1].second` y termina al final de la secuencia de destino; es decir, señala el texto que sigue a la subsecuencia coincidente.

## <a name="match_resultsswap"></a><a name="swap"></a>match_results::swap

Intercambia dos objetos match_results.

```cpp
void swap(const match_results& right) throw();
```

### <a name="parameters"></a>Parámetros

*Correcto*\
El objeto match_results con el que se intercambia.

### <a name="remarks"></a>Observaciones

La función miembro intercambia el contenido `*this` de y *right* en tiempo constante y no produce excepciones.

## <a name="match_resultsvalue_type"></a><a name="value_type"></a>match_results::value_type

El tipo de una subcoincidencia.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>Observaciones

La definición de tipo es un sinónimo del tipo `sub_match<BidIt>`.

## <a name="see-also"></a>Consulte también

[\<regex>](../standard-library/regex.md)
