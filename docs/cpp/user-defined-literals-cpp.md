---
title: Literales definidos por el usuarioC++()
description: Describe el propósito y el uso de los literales definidos por el C++usuario en el estándar.
ms.date: 02/10/2020
ms.assetid: ff4a5bec-f795-4705-a2c0-53788fd57609
ms.openlocfilehash: a6636be414fa4dc199ce10fca1b33f092492575f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2020
ms.locfileid: "79090559"
---
# <a name="user-defined-literals"></a>Literales definidos por el usuario

Hay seis categorías principales de literales en C++: entero, carácter, punto flotante, cadena, booleano y puntero. A partir C++ de 11, puede definir sus propios literales en función de estas categorías para proporcionar accesos directos sintácticos para las expresiones comunes y aumentar la seguridad de tipos. Por ejemplo, supongamos que tiene una clase `Distance`. Puede definir un literal para kilómetros y otro para millas, y animar al usuario a que sea explícito sobre las unidades de medida escribiendo: `auto d = 42.0_km` o `auto d = 42.0_mi`. No hay ninguna ventaja ni desventaja en el rendimiento de los literales definidos por el usuario; son principalmente para comodidad o para la deducción de tipos en tiempo de compilación. La biblioteca estándar tiene literales definidos por el usuario para `std::string`, para `std::complex`y para las unidades de operaciones de tiempo y duración del encabezado \<crónico >:

```cpp
Distance d = 36.0_mi + 42.0_km;         // Custom UDL (see below)
std::string str = "hello"s + "World"s;  // Standard Library <string> UDL
complex<double> num =
   (2.0 + 3.01i) * (5.0 + 4.3i);        // Standard Library <complex> UDL
auto duration = 15ms + 42h;             // Standard Library <chrono> UDLs
```

## <a name="user-defined-literal-operator-signatures"></a>Firmas de operador literal definido por el usuario

Para implementar un literal definido por el usuario, defina un **operador ""** en el ámbito del espacio de nombres con uno de los siguientes formatos:

```cpp
ReturnType operator "" _a(unsigned long long int);   // Literal operator for user-defined INTEGRAL literal
ReturnType operator "" _b(long double);              // Literal operator for user-defined FLOATING literal
ReturnType operator "" _c(char);                     // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _d(wchar_t);                  // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _e(char16_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _f(char32_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _g(const char*, size_t);      // Literal operator for user-defined STRING literal
ReturnType operator "" _h(const wchar_t*, size_t);   // Literal operator for user-defined STRING literal
ReturnType operator "" _i(const char16_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _g(const char32_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

Los nombres de operador del ejemplo anterior son marcadores de posición para cualquier nombre que proporcione; sin embargo, el carácter de subrayado inicial es necesario. (Solo se permite a la biblioteca estándar definir literales sin el carácter de subrayado). El tipo de valor devuelto es donde se personaliza la conversión u otras operaciones realizadas por el literal. Además, cualquiera de estos operadores se puede definir como `constexpr`.

## <a name="cooked-literals"></a>Literales elaborados

En el código fuente, cualquier literal, ya sea definido por el usuario o no, es esencialmente una secuencia de caracteres alfanuméricos, como `101`, o `54.7`, o `"hello"` o `true`. El compilador interpreta la secuencia como un entero, Float, const char\* cadena, etc. Un literal definido por el usuario que acepta como entrada cualquier tipo que el compilador asignado al valor literal se conoce informadamente como un *literal cocido*. Todos los operadores anteriores, excepto `_r` y `_t`, son literales elaborados. Por ejemplo, un literal `42.0_km` se enlazaría a un operador denominado _km que tuviera una firma semejante a _b y el literal `42_km` se enlazaría a un operador con una firma semejante a _a.

En el ejemplo siguiente se muestra cómo los literales definidos por el usuario pueden fomentar que los llamadores sean explícitos sobre los datos proporcionados. Para crear un `Distance`, el usuario debe especificar explícitamente kilómetros o millas mediante el literal definido por el usuario adecuado. Puede lograr el mismo resultado de otras maneras, pero los literales definidos por el usuario son menos detallados que las alternativas.

```cpp
// UDL_Distance.cpp

#include <iostream>
#include <string>

struct Distance
{
private:
    explicit Distance(long double val) : kilometers(val)
    {}

    friend Distance operator"" _km(long double val);
    friend Distance operator"" _mi(long double val);

    long double kilometers{ 0 };
public:
    const static long double km_per_mile;
    long double get_kilometers() { return kilometers; }

    Distance operator+(Distance other)
    {
        return Distance(get_kilometers() + other.get_kilometers());
    }
};

const long double Distance::km_per_mile = 1.609344L;

Distance operator"" _km(long double val)
{
    return Distance(val);
}

Distance operator"" _mi(long double val)
{
    return Distance(val * Distance::km_per_mile);
}

int main()
{
    // Must have a decimal point to bind to the operator we defined!
    Distance d{ 402.0_km }; // construct using kilometers
    std::cout << "Kilometers in d: " << d.get_kilometers() << std::endl; // 402

    Distance d2{ 402.0_mi }; // construct using miles
    std::cout << "Kilometers in d2: " << d2.get_kilometers() << std::endl;  //646.956

    // add distances constructed with different units
    Distance d3 = 36.0_mi + 42.0_km;
    std::cout << "d3 value = " << d3.get_kilometers() << std::endl; // 99.9364

    // Distance d4(90.0); // error constructor not accessible

    std::string s;
    std::getline(std::cin, s);
    return 0;
}
```

El número literal debe usar un decimal. De lo contrario, el número se interpretaría como un entero y el tipo no sería compatible con el operador. Para la entrada de punto flotante, el tipo debe ser **Long Double**y, para los tipos enteros, debe ser **de larga duración.**

## <a name="raw-literals"></a>Literales sin formato

En un literal definido por el usuario sin formato, el operador que se define acepta el literal como una secuencia de valores char. Depende de usted interpretar esa secuencia como un número o una cadena u otro tipo. En la lista de operadores mostrada anteriormente en esta página, se pueden usar `_r` y `_t` para definir literales sin formato:

```cpp
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

Los literales sin formato se pueden usar para proporcionar una interpretación personalizada de una secuencia de entrada diferente del comportamiento normal del compilador. Por ejemplo, puede definir un literal que convierta la secuencia `4.75987` en un tipo Decimal personalizado en lugar de un tipo de punto flotante de IEEE 754. Los literales sin formato, como los literales cocidos, también se pueden usar para la validación en tiempo de compilación de las secuencias de entrada.

### <a name="example-limitations-of-raw-literals"></a>Ejemplo: limitaciones de los literales sin formato

El operador literal sin formato y la plantilla de operador literal solo funcionan para literales de entero y de punto flotante definidos por el usuario, tal y como se muestra en el ejemplo siguiente:

```cpp
#include <cstddef>
#include <cstdio>

// Literal operator for user-defined INTEGRAL literal
void operator "" _dump(unsigned long long int lit)
{
    printf("operator \"\" _dump(unsigned long long int) : ===>%llu<===\n", lit);
};

// Literal operator for user-defined FLOATING literal
void operator "" _dump(long double lit)
{
    printf("operator \"\" _dump(long double)            : ===>%Lf<===\n",  lit);
};

// Literal operator for user-defined CHARACTER literal
void operator "" _dump(char lit)
{
    printf("operator \"\" _dump(char)                   : ===>%c<===\n",   lit);
};

void operator "" _dump(wchar_t lit)
{
    printf("operator \"\" _dump(wchar_t)                : ===>%d<===\n",   lit);
};

void operator "" _dump(char16_t lit)
{
    printf("operator \"\" _dump(char16_t)               : ===>%d<===\n",   lit);
};

void operator "" _dump(char32_t lit)
{
    printf("operator \"\" _dump(char32_t)               : ===>%d<===\n",   lit);
};

// Literal operator for user-defined STRING literal
void operator "" _dump(const     char* lit, size_t)
{
    printf("operator \"\" _dump(const     char*, size_t): ===>%s<===\n",   lit);
};

void operator "" _dump(const  wchar_t* lit, size_t)
{
    printf("operator \"\" _dump(const  wchar_t*, size_t): ===>%ls<===\n",  lit);
};

void operator "" _dump(const char16_t* lit, size_t)
{
    printf("operator \"\" _dump(const char16_t*, size_t):\n"                  );
};

void operator "" _dump(const char32_t* lit, size_t)
{
    printf("operator \"\" _dump(const char32_t*, size_t):\n"                  );
};

// Raw literal operator
void operator "" _dump_raw(const char* lit)
{
    printf("operator \"\" _dump_raw(const char*)        : ===>%s<===\n",   lit);
};

template<char...> void operator "" _dump_template();       // Literal operator template

int main(int argc, const char* argv[])
{
    42_dump;
    3.1415926_dump;
    3.14e+25_dump;
     'A'_dump;
    L'B'_dump;
    u'C'_dump;
    U'D'_dump;
      "Hello World"_dump;
     L"Wide String"_dump;
    u8"UTF-8 String"_dump;
     u"UTF-16 String"_dump;
     U"UTF-32 String"_dump;
    42_dump_raw;
    3.1415926_dump_raw;
    3.14e+25_dump_raw;

    // There is no raw literal operator or literal operator template support on these types:
    //  'A'_dump_raw;
    // L'B'_dump_raw;
    // u'C'_dump_raw;
    // U'D'_dump_raw;
    //   "Hello World"_dump_raw;
    //  L"Wide String"_dump_raw;
    // u8"UTF-8 String"_dump_raw;
    //  u"UTF-16 String"_dump_raw;
    //  U"UTF-32 String"_dump_raw;
}
```

```Output
operator "" _dump(unsigned long long int) : ===>42<===
operator "" _dump(long double)            : ===>3.141593<===
operator "" _dump(long double)            : ===>31399999999999998506827776.000000<===
operator "" _dump(char)                   : ===>A<===
operator "" _dump(wchar_t)                : ===>66<===
operator "" _dump(char16_t)               : ===>67<===
operator "" _dump(char32_t)               : ===>68<===
operator "" _dump(const     char*, size_t): ===>Hello World<===
operator "" _dump(const  wchar_t*, size_t): ===>Wide String<===
operator "" _dump(const     char*, size_t): ===>UTF-8 String<===
operator "" _dump(const char16_t*, size_t):
operator "" _dump(const char32_t*, size_t):
operator "" _dump_raw(const char*)        : ===>42<===
operator "" _dump_raw(const char*)        : ===>3.1415926<===
operator "" _dump_raw(const char*)        : ===>3.14e+25<===
```
