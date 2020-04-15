---
title: discrete_distribution (Clase)
ms.date: 11/04/2016
f1_keywords:
- random/std::discrete_distribution
- random/std::discrete_distribution::reset
- random/std::discrete_distribution::probabilities
- random/std::discrete_distribution::param
- random/std::discrete_distribution::min
- random/std::discrete_distribution::max
- random/std::discrete_distribution::operator()
- random/std::discrete_distribution::param_type
- random/std::discrete_distribution::param_type::probabilities
- random/std::discrete_distribution::param_type::operator==
- random/std::discrete_distribution::param_type::operator!=
helpviewer_keywords:
- std::discrete_distribution [C++]
- std::discrete_distribution [C++], reset
- std::discrete_distribution [C++], probabilities
- std::discrete_distribution [C++], param
- std::discrete_distribution [C++], min
- std::discrete_distribution [C++], max
- std::discrete_distribution [C++], param_type
- std::discrete_distribution [C++], param_type
ms.assetid: 8c8ba8f8-c06f-4f07-b354-f53950142fcf
ms.openlocfilehash: 83d69df399d556025d0f7d4a8ccd714ff43a76ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368770"
---
# <a name="discrete_distribution-class"></a>discrete_distribution (Clase)

Genera una distribución de enteros discreta que tenga intervalos de ancho uniforme con probabilidad uniforme en cada intervalo.

## <a name="syntax"></a>Sintaxis

```cpp
template<class IntType = int>
class discrete_distribution
   {
public:
   // types
   typedef IntType result_type;
   struct param_type;

   // constructor and reset functions
   discrete_distribution();
   template <class InputIterator>
   discrete_distribution(InputIterator firstW, InputIterator lastW);
   discrete_distribution(initializer_list<double> weightlist);
   template <class UnaryOperation>
   discrete_distribution(size_t count, double xmin, double xmax, UnaryOperation funcweight);
   explicit discrete_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   vector<double> probabilities() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parámetros

*IntType*\
El tipo de resultado entero, el valor predeterminado es **int**. Para ver los tipos posibles, consulte [ \<>aleatorias ](../standard-library/random.md).

## <a name="remarks"></a>Observaciones

Esta distribución de muestreo tiene intervalos de ancho uniforme con probabilidad uniforme en cada intervalo. Para obtener información sobre otras distribuciones de muestreo, consveaulte [piecewise_linear_distribution (Clase)](../standard-library/piecewise-linear-distribution-class.md) y [piecewise_constant_distribution (Clase)](../standard-library/piecewise-constant-distribution-class.md).

La tabla siguiente incluye vínculos a artículos sobre miembros individuales:

|||
|-|-|
|[discrete_distribution](#discrete_distribution)|`discrete_distribution::param`|
|`discrete_distribution::operator()`|[param_type](#param_type)|

La función de propiedad `vector<double> probabilities()` devuelve las probabilidades individuales de cada entero generado.

Para obtener más información acerca de las clases de distribución y sus miembros, vea [ \<>aleatorias ](../standard-library/random.md).

## <a name="example"></a>Ejemplo

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

using namespace std;

void test(const int s) {

    // uncomment to use a non-deterministic generator
    // random_device rd;
    // mt19937 gen(rd());
    mt19937 gen(1701);

    discrete_distribution<> distr({ 1, 2, 3, 4, 5 });

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "probabilities (value: probability):" << endl;
    vector<double> p = distr.probabilities();
    int counter = 0;
    for (const auto& n : p) {
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;
        ++counter;
    }
    cout << endl;

    // generate the distribution as a histogram
    map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    cout << "Distribution for " << s << " samples:" << endl;
    for (const auto& elem : histogram) {
        cout << setw(5) << elem.first << ' ' << string(elem.second, ':') << endl;
    }
    cout << endl;
}

int main()
{
    int samples = 100;

    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;
    cout << "Enter an integer value for the sample count: ";
    cin >> samples;

    test(samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the sample count: 100
min() == 0
max() == 4
probabilities (value: probability):
          0:   0.0666666667
          1:   0.1333333333
          2:   0.2000000000
          3:   0.2666666667
          4:   0.3333333333

Distribution for 100 samples:
    0 :::
    1 ::::::::::::::
    2 ::::::::::::::::::
    3 :::::::::::::::::::::::::::::
    4 ::::::::::::::::::::::::::::::::::::
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<random>

**Espacio de nombres:** std

## <a name="discrete_distributiondiscrete_distribution"></a><a name="discrete_distribution"></a>discrete_distribution::discrete_distribution

Construye la distribución.

```cpp
// default constructor
discrete_distribution();

// construct using a range of weights, [firstW, lastW)
template <class InputIterator>
discrete_distribution(InputIterator firstW, InputIterator lastW);

// construct using an initializer list for range of weights
discrete_distribution(initializer_list<double> weightlist);

// construct using unary operation function
template <class UnaryOperation>
discrete_distribution(size_t count, double low, double high, UnaryOperation weightfunc);

// construct from an existing param_type structure
explicit discrete_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parámetros

*firstW*\
Primer iterador de la lista a partir del que se va a construir la distribución.

*lastW*\
Último iterador de la lista a partir del que se va a construir la distribución (no se incluye, ya que los iteradores usan un elemento vacío para el final).

*lista de peso*\
[initializer_list](../cpp/initializers.md) a partir de la que se va a construir la distribución.

*Contar*\
Número de elementos del intervalo de distribución. Si `count==0`, equivale al constructor predeterminado (siempre genera cero).

*Bajo*\
Valor mínimo del intervalo de distribución.

*Alto*\
Valor máximo del intervalo de distribución.

*weightfunc*\
Objeto que representa la función de probabilidad de la distribución. Tanto el parámetro como el valor devuelto deben ser convertibles a **double**.

*Parmesana*\
La estructura `param_type` usada para construir la distribución.

### <a name="remarks"></a>Observaciones

El constructor predeterminado crea un objeto cuyo valor de probabilidad almacenado tiene un elemento con el valor 1. Esto derivará en una distribución que siempre genera cero.

El constructor de intervalo de iterador que tiene parámetros *firstW* y *lastW* crea un objeto de distribución mediante valores de peso tomados de los iteradores sobre la secuencia del intervalo [*firstW*, *lastW*).

El constructor de lista de inicializadores que tiene un parámetro *weightlist* construye un objeto de distribución con ponderaciones de la lista de inicializadores *weightlist*.

El constructor que tiene parámetros *count*, *low*, *high* y *weightfunc* crea un objeto de distribución que se inicializa según estas reglas:

- Si *count* < 1, **n** = 1 y, como tal, equivale al constructor predeterminado, que siempre genera cero.
- Si *count* > 0, **n** = *count*. Proporcionado **d** á (*alto* - *bajo*) / **n** es mayor que cero, utilizando subrangos uniformes **d,** cada peso se asigna de la siguiente manera: `weight[k] = weightfunc(x)`, donde **x** = *bajo* + **k** * **d** + **d** / 2, para **k** a 0, ..., **n** - 1.

El constructor que tiene un parámetro `param_type`*parm* crea un objeto de distribución mediante *parm* como la estructura de parámetros almacenada.

## <a name="discrete_distributionparam_type"></a><a name="param_type"></a>discrete_distribution::param_type

Almacena todos los parámetros de la distribución.

```cpp
struct param_type {
   typedef discrete_distribution<result_type> distribution_type;
   param_type();

   // construct using a range of weights, [firstW, lastW)
   template <class InputIterator>
   param_type(InputIterator firstW, InputIterator lastW);

   // construct using an initializer list for range of weights
   param_type(initializer_list<double> weightlist);

   // construct using unary operation function
   template <class UnaryOperation>
   param_type(size_t count, double low, double high, UnaryOperation weightfunc);

   std::vector<double> probabilities() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parámetros

*firstW*\
Primer iterador de la lista a partir del que se va a construir la distribución.

*lastW*\
Último iterador de la lista a partir del que se va a construir la distribución (no se incluye, ya que los iteradores usan un elemento vacío para el final).

*lista de peso*\
[initializer_list](../cpp/initializers.md) a partir de la que se va a construir la distribución.

*Contar*\
Número de elementos del intervalo de distribución. Si *count* es 0, equivale al constructor predeterminado (siempre genera cero).

*Bajo*\
Valor mínimo del intervalo de distribución.

*Alto*\
Valor máximo del intervalo de distribución.

*weightfunc*\
Objeto que representa la función de probabilidad de la distribución. Tanto el parámetro como el valor devuelto deben ser convertibles a **double**.

*Correcto*\
El objeto `param_type` que se va a comparar con este.

### <a name="remarks"></a>Observaciones

Este paquete de parámetros se puede pasar a `operator()` para generar el valor devuelto.

## <a name="see-also"></a>Consulte también

[\<>al azar](../standard-library/random.md)
