---
title: extreme_value_distribution (Clase)
ms.date: 11/04/2016
f1_keywords:
- random/std::extreme_value_distribution
- random/std::extreme_value_distribution::reset
- random/std::extreme_value_distribution::a
- random/std::extreme_value_distribution::b
- random/std::extreme_value_distribution::param
- random/std::extreme_value_distribution::min
- random/std::extreme_value_distribution::max
- random/std::extreme_value_distribution::operator()
- random/std::extreme_value_distribution::param_type
- random/std::extreme_value_distribution::param_type::a
- random/std::extreme_value_distribution::param_type::b
- random/std::extreme_value_distribution::param_type::operator==
- random/std::extreme_value_distribution::param_type::operator!=
helpviewer_keywords:
- std::extreme_value_distribution [C++]
- std::extreme_value_distribution [C++], reset
- std::extreme_value_distribution [C++], a
- std::extreme_value_distribution [C++], b
- std::extreme_value_distribution [C++], param
- std::extreme_value_distribution [C++], min
- std::extreme_value_distribution [C++], max
- std::extreme_value_distribution [C++], param_type
- std::extreme_value_distribution [C++], param_type
ms.assetid: a0cd8370-0a54-4e26-9388-8b9678fb57da
ms.openlocfilehash: 5bc0270cb24fcff93d995e8908daaec62c956371
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66451189"
---
# <a name="extremevaluedistribution-class"></a>extreme_value_distribution (Clase)

Genera una distribución de valor extremo.

## <a name="syntax"></a>Sintaxis

```cpp
template<class RealType = double>
class extreme_value_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructor and reset functions
   explicit extreme_value_distribution(result_type a = 0.0, result_type b = 1.0);
   explicit extreme_value_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type a() const;
   result_type b() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parámetros

*RealType*<br/>
El tipo de resultado de coma flotante, el valor predeterminado es **doble**. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).

*URNG*<br/>
El motor del generador de números aleatorios. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Comentarios

La clase de plantilla describe una distribución que produce valores de la especificada por el usuario de punto flotante tipo o tipo **doble** si se proporciona ninguno, distribuido según la distribución de valor extremo. La tabla siguiente incluye vínculos a artículos sobre miembros individuales.

||||
|-|-|-|
|[extreme_value_distribution](#extreme_value_distribution)|`extreme_value_distribution::a`|`extreme_value_distribution::param`|
|`extreme_value_distribution::operator()`|`extreme_value_distribution::b`|[param_type](#param_type)|

Las funciones de propiedad `a()` y `b()` devuelven los valores respectivos para los parámetros de distribución almacenados `a` y `b`.

Para obtener más información sobre las clases de distribución y sus miembros, vea [\<random>](../standard-library/random.md).

Para obtener información detallada sobre la distribución de valor extremo, vea el artículo de Wolfram MathWorld sobre la [distribución de valor extremo](https://go.microsoft.com/fwlink/p/?linkid=401110).

## <a name="example"></a>Ejemplo

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double a, const double b, const int s) {

    // uncomment to use a non-deterministic generator
    //    std::random_device gen;

    std::mt19937 gen(1701);

    std::extreme_value_distribution<> distr(a, b);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "a() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.a() << std::endl;
    std::cout << "b() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.b() << std::endl;

    // generate the distribution as a histogram
    std::map<double, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Distribution for " << s << " samples:" << std::endl;
    int counter = 0;
    for (const auto& elem : histogram) {
        std::cout << std::fixed << std::setw(11) << ++counter << ": "
            << std::setw(14) << std::setprecision(10) << elem.first << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double a_dist = 0.0;
    double b_dist = 1;

    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the \'a\' distribution parameter: ";
    std::cin >> a_dist;
    std::cout << "Enter a floating point value for the \'b\' distribution parameter (must be greater than zero): ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'a' distribution parameter: 0
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == -1.79769e+308
max() == 1.79769e+308
a() == 0.0000000000
b() == 1.0000000000
Distribution for 10 samples:
    1: -0.8813940331
    2: -0.7698972281
    3: 0.2951258007
    4: 0.3110450734
    5: 0.4210546820
    6: 0.4210688771
    7: 0.4598857960
    8: 1.3155194200
    9: 1.5379170046
    10: 2.0568757061
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<random>

**Espacio de nombres:** std

## <a name="extreme_value_distribution"></a>  extreme_value_distribution::extreme_value_distribution

Construye la distribución.

```cpp
explicit extreme_value_distribution(result_type a_value = 0.0, result_type b_value = 1.0);
explicit extreme_value_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parámetros

*a_value*<br/>
El parámetro de distribución `a`.

*b_value*<br/>
El parámetro de distribución `b`.

*parm*<br/>
La estructura `param_type` usada para construir la distribución.

### <a name="remarks"></a>Comentarios

**Condición previa:** `0.0 < b`

El primer constructor crea un objeto cuyo valor `a` almacenado contiene el valor *a_value* y cuyo valor `b` almacenado contiene el valor *b_value*.

El segundo constructor crea un objeto cuyos parámetros almacenados se inicializan desde *parm*. Los parámetros actuales de una distribución existente se pueden obtener y definir llamando a la función miembro `param()`.

## <a name="param_type"></a>  extreme_value_distribution::param_type

Almacena los parámetros de la distribución.

```cpp
struct param_type {
   typedef extreme_value_distribution<result_type> distribution_type;
   param_type(result_type a_value = 0.0, result_type b_value = 1.0);
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parámetros

*a_value*<br/>
El parámetro de distribución `a`.

*b_value*<br/>
El parámetro de distribución `b`.

*right*<br/>
El objeto `param_type` que se va a comparar con este.

### <a name="remarks"></a>Comentarios

**Condición previa:** `0.0 < b`

Esta estructura se puede pasar al constructor de clases de la distribución en el momento de creación de instancias, a la función miembro `param()` para definir los parámetros almacenados de una distribución existente y a `operator()` para usarse en lugar de los parámetros almacenados.

## <a name="see-also"></a>Vea también

[\<random>](../standard-library/random.md)<br/>
