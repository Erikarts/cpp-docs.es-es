---
title: Operadores de &lt;regex&gt;
ms.date: 11/04/2016
f1_keywords:
- regex/std::operator!=
- regex/std::operator>
- regex/std::operator>=
- regex/std::operator<
- regex/std::operator<=
- regex/std::operator==
- regex/std::operator<<
ms.assetid: ec623e65-c186-491f-aa18-6b12b47e1127
ms.openlocfilehash: 829b4cf50b02db0a88d61a8801c1e21ddb470344
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460133"
---
# <a name="ltregexgt-operators"></a>Operadores de &lt;regex&gt;

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|[operator&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|

## <a name="op_neq"></a> operator!=

Comparación de desigualdad para varios objetos.

```cpp
template <class BidIt>
bool operator!=(const sub_match<BidIt>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator!=(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator!=(const sub_match<BidIt>& left,
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>
bool operator!=(const typename iterator_traits<BidIt>::value_type *left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator!=(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type *right);

template <class BidIt>
bool operator!=(const typename iterator_traits<BidIt>::value_type& left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator!=(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type& right);

template <class BidIt, class Alloc>
bool operator!=(const match_results<BidIt, Alloc>& left,
    const match_results<BidIt, Alloc>& right);
```

### <a name="parameters"></a>Parámetros

*BidIt*\
Tipo de iterador.

*IOtraits*\
La clase de características de cadena.

*Alloc*\
Clase de asignador.

*salido*\
El objeto izquierdo que se compara.

*correcta*\
El objeto derecho que se compara.

### <a name="remarks"></a>Comentarios

Cada operador de la plantilla devuelve `!(left == right)`.

### <a name="example"></a>Ejemplo

```cpp
// std__regex__operator_ne.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::cmatch::string_type Mystr;
int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "match == " << mr.str() << std::endl;
    std::cout << "sub == " << sub << std::endl;
    std::cout << std::endl;

    std::cout << "match != match == " << std::boolalpha
        << (mr != mr) << std::endl;
    std::cout << "sub != sub == " << std::boolalpha
        << (sub != sub) << std::endl;

    std::cout << "string(\"aab\") != sub == " << std::boolalpha
        << (Mystr("aab") != sub) << std::endl;
    std::cout << "sub != string(\"aab\") == " << std::boolalpha
        << (sub != Mystr("aab")) << std::endl;

    std::cout << "\"aab\" != sub == " << std::boolalpha
        << ("aab" != sub) << std::endl;
    std::cout << "sub != \"aab\" == " << std::boolalpha
        << (sub != "aab") << std::endl;

    std::cout << "'a' != sub == " << std::boolalpha
        << ('a' != sub) << std::endl;
    std::cout << "sub != 'a' == " << std::boolalpha
        << (sub != 'a') << std::endl;

    return (0);
    }
```

```Output
match == caaa
sub == aaa

match != match == false
sub != sub == false
string("aab") != sub == true
sub != string("aab") == true
"aab" != sub == true
sub != "aab" == true
'a' != sub == true
sub != 'a' == true
```

## <a name="op_lt"></a> operator&lt;

Comparación menor que para varios objetos.

```cpp
template <class BidIt>
bool operator<(const sub_match<BidIt>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator<(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator<(const sub_match<BidIt>& left,
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>
bool operator<(const typename iterator_traits<BidIt>::value_type *left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator<(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type *right);

template <class BidIt>
bool operator<(const typename iterator_traits<BidIt>::value_type& left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator<(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type& right);
```

### <a name="parameters"></a>Parámetros

*BidIt*\
Tipo de iterador.

*IOtraits*\
La clase de características de cadena.

*Alloc*\
Clase de asignador.

*salido*\
El objeto izquierdo que se compara.

*correcta*\
El objeto derecho que se compara.

### <a name="remarks"></a>Comentarios

Cada operador de plantilla convierte sus argumentos en un tipo de cadena y devuelve true solo si el valor convertido de *left* se compara menor que el valor convertido de *right*.

### <a name="example"></a>Ejemplo

```cpp
// std__regex__operator_lt.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::cmatch::string_type Mystr;
int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "sub == " << sub << std::endl;
    std::cout << std::endl;

    std::cout << "sub < sub == " << std::boolalpha
        << (sub < sub) << std::endl;

    std::cout << "string(\"aab\") < sub == " << std::boolalpha
        << (Mystr("aab") < sub) << std::endl;
    std::cout << "sub < string(\"aab\") == " << std::boolalpha
        << (sub < Mystr("aab")) << std::endl;

    std::cout << "\"aab\" < sub == " << std::boolalpha
        << ("aab" < sub) << std::endl;
    std::cout << "sub < \"aab\" == " << std::boolalpha
        << (sub < "aab") << std::endl;

    std::cout << "'a' < sub == " << std::boolalpha
        << ('a' < sub) << std::endl;
    std::cout << "sub < 'a' == " << std::boolalpha
        << (sub < 'a') << std::endl;

    return (0);
    }
```

```Output
sub == aaa

sub < sub == false
string("aab") < sub == false
sub < string("aab") == true
"aab" < sub == false
sub < "aab" == true
'a' < sub == true
sub < 'a' == false
```

## <a name="op_lt_lt"></a> operator&lt;&lt;

Inserta un sub_match en una secuencia.

```cpp
template <class Elem, class IOtraits, class Alloc, class BidIt>
basic_ostream<Elem, IOtraits>& operator<<(basic_ostream<Elem, IOtraits>& os,
    const sub_match<BidIt>& right);
```

### <a name="parameters"></a>Parámetros

*Elem*\
El tipo de elemento.

*IOtraits*\
La clase de características de cadena.

*Alloc*\
Clase de asignador.

*BidIt*\
Tipo de iterador.

*operativos*\
Secuencia de salida.

*correcta*\
Objeto que se va a insertar.

### <a name="remarks"></a>Comentarios

El operador de la plantilla devuelve `os << right.str()`.

### <a name="example"></a>Ejemplo

```cpp
// std__regex__operator_ins.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[0];
    std::cout << "whole match: " << sub << std::endl;

    return (0);
    }
```

```Output
whole match: caaa
```

## <a name="op_lt_eq"></a> operator&lt;=

Comparación menor o igual que para varios objetos.

```cpp
template <class BidIt>
bool operator<=(const sub_match<BidIt>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator<=(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator<=(const sub_match<BidIt>& left,
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>
bool operator<=(const typename iterator_traits<BidIt>::value_type *left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator<=(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type *right);

template <class BidIt>
bool operator<=(const typename iterator_traits<BidIt>::value_type& left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator<=(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type& right);
```

### <a name="parameters"></a>Parámetros

*BidIt*\
Tipo de iterador.

*IOtraits*\
La clase de características de cadena.

*Alloc*\
Clase de asignador.

*salido*\
El objeto izquierdo que se compara.

*correcta*\
El objeto derecho que se compara.

### <a name="remarks"></a>Comentarios

Cada operador de la plantilla devuelve `!(right < left)`.

### <a name="example"></a>Ejemplo

```cpp
// std__regex__operator_le.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::cmatch::string_type Mystr;
int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "sub == " << sub << std::endl;
    std::cout << std::endl;

    std::cout << "sub <= sub == " << std::boolalpha
        << (sub <= sub) << std::endl;

    std::cout << "string(\"aab\") <= sub == " << std::boolalpha
        << (Mystr("aab") <= sub) << std::endl;
    std::cout << "sub <= string(\"aab\") == " << std::boolalpha
        << (sub <= Mystr("aab")) << std::endl;

    std::cout << "\"aab\" <= sub == " << std::boolalpha
        << ("aab" <= sub) << std::endl;
    std::cout << "sub <= \"aab\" == " << std::boolalpha
        << (sub <= "aab") << std::endl;

    std::cout << "'a' <= sub == " << std::boolalpha
        << ('a' <= sub) << std::endl;
    std::cout << "sub <= 'a' == " << std::boolalpha
        << (sub <= 'a') << std::endl;

    return (0);
    }
```

```Output
sub == aaa

sub <= sub == true
string("aab") <= sub == false
sub <= string("aab") == true
"aab" <= sub == false
sub <= "aab" == true
'a' <= sub == true
sub <= 'a' == false
```

## <a name="op_eq_eq"></a>  operator==

Comparación de igualdad para varios objetos.

```cpp
template <class BidIt>
bool operator==(const sub_match<BidIt>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator==(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator==(const sub_match<BidIt>& left,
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>
bool operator==(const typename iterator_traits<BidIt>::value_type* left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator==(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type* right);

template <class BidIt>
bool operator==(const typename iterator_traits<BidIt>::value_type& left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator==(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type& right);

template <class BidIt, class Alloc>
bool operator==(const match_results<BidIt, Alloc>& left,
    const match_results<BidIt, Alloc>& right);
```

### <a name="parameters"></a>Parámetros

*BidIt*\
Tipo de iterador.

*IOtraits*\
La clase de características de cadena.

*Alloc*\
Clase de asignador.

*salido*\
El objeto izquierdo que se compara.

*correcta*\
El objeto derecho que se compara.

### <a name="remarks"></a>Comentarios

Cada operador de la plantilla convierte cada uno de sus argumentos a un tipo de cadena y devuelve el resultado de realizar una comparación de igualdad de los objetos convertidos.

Cuando un operador de plantilla convierte sus argumentos a un tipo de cadena, usa la primera de las siguientes transformaciones que se aplica:

los argumentos cuyos tipos sean una especialización de clase de plantilla `match_results` o `sub_match` se convierten mediante una llamada a la función miembro `str`;

los argumentos cuyos tipos sean una especialización de la clase de plantilla `basic_string` no se cambian;

todos los demás tipos de argumento se convierten pasando el valor del argumento al constructor para una especialización adecuada de la clase de plantilla `basic_string`.

### <a name="example"></a>Ejemplo

```cpp
// std__regex__operator_eq.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::cmatch::string_type Mystr;
int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "match == " << mr.str() << std::endl;
    std::cout << "sub == " << sub << std::endl;
    std::cout << std::endl;

    std::cout << "match == match == " << std::boolalpha
        << (mr == mr) << std::endl;
    std::cout << "sub == sub == " << std::boolalpha
        << (sub == sub) << std::endl;

    std::cout << "string(\"aab\") == sub == " << std::boolalpha
        << (Mystr("aab") == sub) << std::endl;
    std::cout << "sub == string(\"aab\") == " << std::boolalpha
        << (sub == Mystr("aab")) << std::endl;

    std::cout << "\"aab\" == sub == " << std::boolalpha
        << ("aab" == sub) << std::endl;
    std::cout << "sub == \"aab\" == " << std::boolalpha
        << (sub == "aab") << std::endl;

    std::cout << "'a' == sub == " << std::boolalpha
        << ('a' == sub) << std::endl;
    std::cout << "sub == 'a' == " << std::boolalpha
        << (sub == 'a') << std::endl;

    return (0);
    }
```

```Output
match == caaa
sub == aaa

match == match == true
sub == sub == true
string("aab") == sub == false
sub == string("aab") == false
"aab" == sub == false
sub == "aab" == false
'a' == sub == false
sub == 'a' == false
```

## <a name="op_gt"></a> operator&gt;

Comparación mayor que para varios objetos.

```cpp
template <class BidIt>
bool operator>(const sub_match<BidIt>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator>(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator>(const sub_match<BidIt>& left,
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>
bool operator>(const typename iterator_traits<BidIt>::value_type *left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator>(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type *right);

template <class BidIt>
bool operator>(const typename iterator_traits<BidIt>::value_type& left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator>(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type& right);
```

### <a name="parameters"></a>Parámetros

*BidIt*\
Tipo de iterador.

*IOtraits*\
La clase de características de cadena.

*Alloc*\
Clase de asignador.

*salido*\
El objeto izquierdo que se compara.

*correcta*\
El objeto derecho que se compara.

### <a name="remarks"></a>Comentarios

Cada operador de la plantilla devuelve `right < left`.

### <a name="example"></a>Ejemplo

```cpp
// std__regex__operator_gt.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::cmatch::string_type Mystr;
int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "sub == " << sub << std::endl;
    std::cout << std::endl;

    std::cout << "sub > sub == " << std::boolalpha
        << (sub > sub) << std::endl;

    std::cout << "string(\"aab\") > sub == " << std::boolalpha
        << (Mystr("aab") > sub) << std::endl;
    std::cout << "sub > string(\"aab\") == " << std::boolalpha
        << (sub > Mystr("aab")) << std::endl;

    std::cout << "\"aab\" > sub == " << std::boolalpha
        << ("aab" > sub) << std::endl;
    std::cout << "sub > \"aab\" == " << std::boolalpha
        << (sub > "aab") << std::endl;

    std::cout << "'a' > sub == " << std::boolalpha
        << ('a' > sub) << std::endl;
    std::cout << "sub > 'a' == " << std::boolalpha
        << (sub > 'a') << std::endl;

    return (0);
    }
```

```Output
sub == aaa

sub > sub == false
string("aab") > sub == true
sub > string("aab") == false
"aab" > sub == true
sub > "aab" == false
'a' > sub == false
sub > 'a' == true
```

## <a name="op_gt_eq"></a> operator&gt;=

Comparación mayor o igual que para varios objetos.

```cpp
template <class BidIt>
bool operator>=(const sub_match<BidIt>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator>=(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator>=(const sub_match<BidIt>& left,
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>
bool operator>=(const typename iterator_traits<BidIt>::value_type *left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator>=(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type *right);

template <class BidIt>
bool operator>=(const typename iterator_traits<BidIt>::value_type& left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator>=(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type& right);
```

### <a name="parameters"></a>Parámetros

*BidIt*\
Tipo de iterador.

*IOtraits*\
La clase de características de cadena.

*Alloc*\
Clase de asignador.

*salido*\
El objeto izquierdo que se compara.

*correcta*\
El objeto derecho que se compara.

### <a name="remarks"></a>Comentarios

Cada operador de la plantilla devuelve `!(left < right)`.

### <a name="example"></a>Ejemplo

```cpp
// std__regex__operator_ge.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::cmatch::string_type Mystr;
int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "sub == " << sub << std::endl;
    std::cout << std::endl;

    std::cout << "sub >= sub == " << std::boolalpha
        << (sub >= sub) << std::endl;

    std::cout << "string(\"aab\") >= sub == " << std::boolalpha
        << (Mystr("aab") >= sub) << std::endl;
    std::cout << "sub >= string(\"aab\") == " << std::boolalpha
        << (sub >= Mystr("aab")) << std::endl;

    std::cout << "\"aab\" >= sub == " << std::boolalpha
        << ("aab" >= sub) << std::endl;
    std::cout << "sub >= \"aab\" == " << std::boolalpha
        << (sub >= "aab") << std::endl;

    std::cout << "'a' >= sub == " << std::boolalpha
        << ('a' >= sub) << std::endl;
    std::cout << "sub >= 'a' == " << std::boolalpha
        << (sub >= 'a') << std::endl;

    return (0);
    }
```

```Output
sub == aaa

sub >= sub == true
string("aab") >= sub == true
sub >= string("aab") == false
"aab" >= sub == true
sub >= "aab" == false
'a' >= sub == false
sub >= 'a' == true
```

## <a name="see-also"></a>Vea también

[\<regex>](../standard-library/regex.md)\
[Clase regex_constants](../standard-library/regex-constants-class.md)\
[Clase regex_error](../standard-library/regex-error-class.md)\
[\<funciones regex >](../standard-library/regex-functions.md)\
[Clase regex_iterator](../standard-library/regex-iterator-class.md)\
[Clase regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[Clase regex_traits](../standard-library/regex-traits-class.md)\
[Definiciones de tipo \<regex>](../standard-library/regex-typedefs.md)
