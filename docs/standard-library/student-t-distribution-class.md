---
title: student_t_distribution (Clase)
ms.date: 11/04/2016
f1_keywords:
- random/std::student_t_distribution
- random/std::student_t_distribution::result_type
- random/std::student_t_distribution::reset
- random/std::student_t_distribution::operator()
- random/std::student_t_distribution::n
- random/std::student_t_distribution::param
- random/std::student_t_distribution::min
- random/std::student_t_distribution::max
- random/std::student_t_distribution::param_type
helpviewer_keywords:
- std::student_t_distribution [C++]
- std::student_t_distribution [C++], result_type
- std::student_t_distribution [C++], reset
- std::student_t_distribution [C++], n
- std::student_t_distribution [C++], param
- std::student_t_distribution [C++], min
- std::student_t_distribution [C++], max
- std::student_t_distribution [C++], param_type
ms.assetid: 87b48127-9311-4d07-95df-833ed46bf0b1
ms.openlocfilehash: 42e7337a2a0803af51e7dd11f53c482dbfc2aa0f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458999"
---
# <a name="studenttdistribution-class"></a>student_t_distribution (Clase)

Genera una distribución *t* de Student.

## <a name="syntax"></a>Sintaxis

```cpp
template<class RealType = double>
class student_t_distribution {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructor and reset functions
   explicit student_t_distribution(result_type n = 1.0);
   explicit student_t_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type n() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parámetros

*RealType*\
El tipo de resultado de punto flotante, el valor predeterminado es **Double**. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Comentarios

La clase de plantilla describe una distribución que genera valores de un tipo de entero especificado por el usuario o de tipo **Double** si no se proporciona ninguno, distribuido según la distribución *t*de Student. La tabla siguiente incluye vínculos a artículos sobre miembros individuales.

||||
|-|-|-|
|[student_t_distribution](#student_t_distribution)|`student_t_distribution::n`|`student_t_distribution::param`|
|`student_t_distribution::operator()`||[param_type](#param_type)|

La función de propiedad `n()` devuelve el valor del parámetro de distribución almacenado `n`.

Para más información sobre las clases de distribución y sus miembros, vea [\<random>](../standard-library/random.md).

Para obtener más detalles sobre el algoritmo de la distribución *t* de Student, vea el artículo de Wolfram MathWorld sobre [Distribución t de Students](http://mathworld.wolfram.com/Studentst-Distribution.html).

## <a name="example"></a>Ejemplo

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double n, const int s) {

    // uncomment to use a non-deterministic generator
    //    std::random_device gen;
    std::mt19937 gen(1701);

    std::student_t_distribution<> distr(n);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "n() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.n() << std::endl;

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
    double n_dist = 0.5;
    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the 'n' distribution parameter (must be greater than zero): ";
    std::cin >> n_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(n_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == -1.79769e+308
max() == 1.79769e+308
n() == 1.0000000000
Distribution for 10 samples:
    1: -1.3084956212
    2: -1.0899518684
    3: -0.9568771388
    4: -0.9372088821
    5: -0.7381334669
    6: -0.2488074854
    7: -0.2028714601
    8: 1.4013074495
    9: 5.3244792236
    10: 92.7084335614
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<random>

**Espacio de nombres:** std

## <a name="student_t_distribution"></a>  student_t_distribution::student_t_distribution

Construye la distribución.

```cpp
explicit student_t_distribution(RealType n = 1.0);
explicit student_t_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parámetros

*n*\
El parámetro de distribución `n`.

*PARM*\
Paquete de parámetros utilizado para construir la distribución.

### <a name="remarks"></a>Comentarios

**Condición previa:** `0.0 < n`

El primer constructor crea un objeto cuyo valor `n` almacenado contiene el valor *n*.

El segundo constructor crea un objeto cuyos parámetros almacenados se inicializan desde *parm*. Los parámetros actuales de una distribución existente se pueden obtener y definir llamando a la función miembro `param()`.

## <a name="param_type"></a>  student_t_distribution::param_type

Almacena todos los parámetros de la distribución.

```cpp
struct param_type {
   typedef student_t_distribution<result_type> distribution_type;
   param_type(result_type n = 1.0);
   result_type n() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parámetros

*n*\
El parámetro de distribución `n`.

*correcta*\
El objeto `param_type` que se va a comparar con este.

### <a name="remarks"></a>Comentarios

**Condición previa:** `0.0 < n`

Esta estructura se puede pasar al constructor de clases de la distribución en el momento de creación de instancias, a la función miembro `param()` para definir los parámetros almacenados de una distribución existente y a `operator()` para usarse en lugar de los parámetros almacenados.

## <a name="see-also"></a>Vea también

[\<random>](../standard-library/random.md)
