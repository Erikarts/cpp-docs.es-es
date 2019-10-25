---
title: mersenne_twister_engine (Clase)
ms.date: 11/04/2016
f1_keywords:
- random/std::mersenne_twister_engine
helpviewer_keywords:
- mersenne_twister_engine class
ms.assetid: 7ee968fa-a1cc-450f-890f-7305de062685
ms.openlocfilehash: 79613c76b3ea6dc15643e83a15d5bd6d90b60c6a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687702"
---
# <a name="mersenne_twister_engine-class"></a>mersenne_twister_engine (Clase)

Genera una secuencia de íntegros aleatoria de alta calidad basada en el algoritmo de Mersenne twister.

## <a name="syntax"></a>Sintaxis

```cpp
template <class UIntType,
    size_t W, size_t N, size_t M, size_t R,
    UIntType A, size_t U, UIntType D, size_t S,
    UIntType B, size_t T, UIntType C, size_t L, UIntType F>
class mersenne_twister_engine;
```

### <a name="parameters"></a>Parámetros

@No__t_1 *UIntType*
El tipo de resultado integral sin signo. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).

*W* \
**Tamaño de palabra**. Tamaño de cada palabra, en bits, de la secuencia de estado. **Condición previa:** `2u < W ≤ numeric_limits<UIntType>::digits`

*N* \
**Tamaño de estado**. El número de elementos (valores) en la secuencia de estado.

*M* \
**Tamaño de cambio**. El número de elementos que omitir durante cada vuelta. **Condición previa:** `0 < M ≤ N`

*R*\
**Bits de máscara**. **Condición previa:** `R ≤ W`

*Un* \
**Máscara XOR**. **Condición previa:** `A ≤ (1u<<W) - 1u`

@No__t_4 *U*, *S*, *T*, *L*
**Parámetros de cambio de atenuación**. Utilizados como valores de cambio durante la codificación (atenuación). Condición previa: `U,S,T,L ≤ W`

*D*, *B*, *C* \
**Parámetros de máscara de bit de atenuación**. Utilizados como valores de máscara de bit durante la codificación (atenuación). Condición previa: `D,B,C ≤ (1u<<W) - 1u`

@No__t_1 *F*
**Multiplicador de inicialización**. Utilizado para ayudar a la inicialización de la secuencia. Condición previa: `F ≤ (1u<<W) - 1u`

## <a name="members"></a>Miembros

||||
|-|-|-|
|`mersenne_twister_engine::mersenne_twister_engine`|`mersenne_twister_engine::min`|`mersenne_twister_engine::discard`|
|`mersenne_twister_engine::operator()`|`mersenne_twister_engine::max`|`mersenne_twister_engine::seed`|

`default_seed` es un miembro constante, definido como `5489u`, utilizado como el valor de parámetro predeterminado para `mersenne_twister_engine::seed` y el constructor de valores simple.

Para obtener más información sobre los miembros del motor, vea [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Comentarios

Esta plantilla de clase describe un motor de número aleatorio que devuelve valores en el intervalo cerrado [`0`, `2`<sup>W</sup>  -  `1`]. Contiene un valor integral grande con `W * (N - 1) + R` bits. Extrae *W* bits a la vez de este valor grande y, cuando ha utilizado todos los bits, desplaza el valor grande cambiando y mezclando los bits para que tenga un nuevo conjunto de bits del que extraer. El estado del motor es el último `N` los valores de `W` bits usados si se ha llamado a `operator()` al menos *N* veces, de lo contrario, los valores de `W` bits de `M` que se han usado y los últimos valores de `N - M` de la inicialización.

El generador refuerza el valor grande que contiene mediante el uso de un registro de desplazamiento de comentarios generalizado con retorcido definido por los valores de desplazamiento *N* y *M*, un valor de torsión *R*y un valor de máscara XOR condicional *a*. Además, los bits del registro de cambio sin procesar se codifican (se atenúan) según una matriz de codificación de bits definida por los valores *U*, *D*, *S*, *B*, *T*, *C*y *L*.

El argumento de la plantilla `UIntType` debe ser lo suficientemente grande para contener valores de hasta `2`<sup>W</sup> - `1`. Los valores de los demás argumentos de plantilla deben cumplir los siguientes requisitos: `2u < W, 0 < M, M ≤ N, R ≤ W, U ≤ W, S ≤ W, T ≤ W, L ≤ W, W ≤ numeric_limits<UIntType>::digits, A ≤ (1u<<W) - 1u, B ≤ (1u<<W) - 1u, C ≤ (1u<<W) - 1u, D ≤ (1u<<W) - 1u, and F ≤ (1u<<W) - 1u`.

Aunque puede construir un generador directamente a partir de este motor, se recomienda que use una de estas definiciones de tipos predefinidas:

`mt19937`: Motor de Mersenne twister de 32 bits (Matsumoto y Nishimura, 1998).

```cpp
typedef mersenne_twister_engine<unsigned int, 32, 624, 397,
    31, 0x9908b0df,
    11, 0xffffffff,
    7, 0x9d2c5680,
    15, 0xefc60000,
    18, 1812433253> mt19937;
```

`mt19937_64`: Motor de Mersenne twister de 64 bits (Matsumoto y Nishimura, 2000).

```cpp
typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,
    31, 0xb5026f5aa96619e9ULL,
    29, 0x5555555555555555ULL,
    17, 0x71d67fffeda60000ULL,
    37, 0xfff7eee000000000ULL,
    43, 6364136223846793005ULL> mt19937_64;
```

Para obtener información detallada sobre el algoritmo de Mersenne twister, vea el artículo de la Wikipedia sobre [Mersenne twister](https://go.microsoft.com/fwlink/p/?linkid=402356).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo de código, vea [\<random>](../standard-library/random.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<random>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[\<random>](../standard-library/random.md)
