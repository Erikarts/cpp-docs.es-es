---
title: Operadores de desplazamiento a izquierda y derecha (&gt; &gt; y &lt; &lt;)
ms.date: 08/13/2018
f1_keywords:
- <<
- '>>'
helpviewer_keywords:
- << operator [C++], with specific objects
- left shift operators [C++]
- right shift operators [C++]
- bitwise-shift operators [C++]
- '>> operator'
- shift operators [C++]
- operators [C++], shift
ms.assetid: 25fa0cbb-5fdd-4657-8745-b35f7d8f1606
ms.openlocfilehash: fd048bedc45b14bdc7b83120ad039296b54aa850
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222052"
---
# <a name="left-shift-and-right-shift-operators-gtgt-and-ltlt"></a>Operadores de desplazamiento a izquierda y derecha (&gt; &gt; y &lt; &lt;)

Los operadores de desplazamiento bit a bit son el operador de desplazamiento a la derecha (**&gt;&gt;**), que mueve los bits de *shift-expression* hacia la derecha y el operador de desplazamiento a la izquierda (**&lt; &lt;**), que mueve los bits de *shift-expression* a la izquierda. <sup>1</sup>

## <a name="syntax"></a>Sintaxis

> *expresión de desplazamiento* `<<` *additive-expression*
> *shift-expression* `>>` *additive-expression*

## <a name="remarks"></a>Comentarios

> [!IMPORTANT]
> Las descripciones y los ejemplos siguientes son válidos en Windows para arquitecturas x86 y x64. La implementación de los operadores de desplazamiento a la izquierda y desplazamiento a la derecha es significativamente diferente en Windows para dispositivos ARM. Para obtener más información, vea la sección "Operadores de desplazamiento" de la [Hello ARM](https://blogs.msdn.com/b/vcblog/archive/2012/10/25/hello-arm-exploring-undefined-unspecified-and-implementation-defined-behavior-in-c.aspx) entrada de blog.

## <a name="left-shifts"></a>Desplazamientos a la izquierda

El operador de desplazamiento a la izquierda hace que los bits de *shift-expression* se desplace a la izquierda el número de posiciones especificado por *additive-expression*. Las posiciones de bits que quedan vacantes debido a la operación de desplazamiento se rellenan con ceros. Un desplazamiento a la izquierda es un desplazamiento lógico (los bits que se desplazan más allá del final se descartan, incluido el bit de signo). Para obtener más información sobre los tipos de desplazamiento bit a bit, consulte [desplazamiento bit a bit](https://en.wikipedia.org/wiki/Bitwise_shift).

En el ejemplo siguiente se muestran operaciones de desplazamiento a la izquierda con números sin signo. El ejemplo muestra lo que ocurre con los bits representando el valor como un bitset. Para obtener más información, consulte [BitSet (clase)](../standard-library/bitset-class.md).

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned short short1 = 4;
    bitset<16> bitset1{short1};   // the bitset representation of 4
    cout << bitset1 << endl;  // 0b00000000'00000100

    unsigned short short2 = short1 << 1;     // 4 left-shifted by 1 = 8
    bitset<16> bitset2{short2};
    cout << bitset2 << endl;  // 0b00000000'00001000

    unsigned short short3 = short1 << 2;     // 4 left-shifted by 2 = 16
    bitset<16> bitset3{short3};
    cout << bitset3 << endl;  // 0b00000000'00010000
}
```

Si desplaza a la izquierda un número con signo de modo que el bit de signo se vea afectado, el resultado es indefinido. El ejemplo siguiente muestra lo que sucede cuando un 1 bit se desplaza hacia la izquierda en la posición de bit de signo.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short short1 = 16384;
    bitset<16> bitset1(short1);
    cout << bitset1 << endl;  // 0b01000000'00000000

    short short3 = short1 << 1;
    bitset<16> bitset3(short3);  // 16384 left-shifted by 1 = -32768
    cout << bitset3 << endl;  // 0b10000000'00000000

    short short4 = short1 << 14;
    bitset<16> bitset4(short4);  // 4 left-shifted by 14 = 0
    cout << bitset4 << endl;  // 0b00000000'00000000
}
```

## <a name="right-shifts"></a>Desplazamientos a la derecha

El operador de desplazamiento a la derecha hace que el patrón de bits en *shift-expression* se desplace a la derecha el número de posiciones especificado por *additive-expression*. En el caso de números sin signo, las posiciones de bits que quedan vacantes debido a la operación de desplazamiento se rellenan con ceros. Si se trata de números con signo, el bit de signo se emplea para rellenar las posiciones de bits vacantes. Es decir, si el número es positivo se usa 0 y si el número es negativo se usa 1.

> [!IMPORTANT]
> El resultado de un desplazamiento a la derecha de un número negativo con signo depende de la implementación. Aunque Microsoft C++ compilador usa el bit de signo para rellenar las posiciones de bits vacantes, no hay ninguna garantía de que otras implementaciones también lo hagan.

En este ejemplo se muestran operaciones de desplazamiento a la derecha que usan números sin signo:

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned short short11 = 1024;
    bitset<16> bitset11{short11};
    cout << bitset11 << endl;     // 0b00000100'00000000

    unsigned short short12 = short11 >> 1;  // 512
    bitset<16> bitset12{short12};
    cout << bitset12 << endl;     // 0b00000010'00000000

    unsigned short short13 = short11 >> 10;  // 1
    bitset<16> bitset13{short13};
    cout << bitset13 << endl;     // 0b00000000'00000001

    unsigned short short14 = short11 >> 11;  // 0
    bitset<16> bitset14{short14};
    cout << bitset14 << endl;     // 0b00000000'00000000
}
```

En el ejemplo siguiente se muestran operaciones de desplazamiento a la derecha con números positivos con signo.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short short1 = 1024;
    bitset<16> bitset1(short1);
    cout << bitset1 << endl;     // 0b00000100'00000000

    short short2 = short1 >> 1;  // 512
    bitset<16> bitset2(short2);
    cout << bitset2 << endl;     // 0b00000010'00000000

    short short3 = short1 >> 11;  // 0
    bitset<16> bitset3(short3);
    cout << bitset3 << endl;     // 0b00000000'00000000
}
```

En el ejemplo siguiente se muestran operaciones de desplazamiento a la derecha con enteros negativos con signo.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short neg1 = -16;
    bitset<16> bn1(neg1);
    cout << bn1 << endl;  // 0b11111111'11110000

    short neg2 = neg1 >> 1; // -8
    bitset<16> bn2(neg2);
    cout << bn2 << endl;  // 0b11111111'11111000

    short neg3 = neg1 >> 2; // -4
    bitset<16> bn3(neg3);
    cout << bn3 << endl;  // 0b11111111'11111100

    short neg4 = neg1 >> 4; // -1
    bitset<16> bn4(neg4);
    cout << bn4 << endl;  // 0b11111111'11111111

    short neg5 = neg1 >> 5; // -1
    bitset<16> bn5(neg5);
    cout << bn5 << endl;  // 0b11111111'11111111
}
```

## <a name="shifts-and-promotions"></a>Desplazamientos y promociones

Las expresiones especificadas a ambos lados de un operador de desplazamiento deben ser de tipos enteros. Promociones de enteros se realizan según las reglas descritas en [conversiones estándar](standard-conversions.md). El tipo del resultado es el mismo que el tipo de ha promovido *shift-expression*.

En el ejemplo siguiente, una variable de tipo **char** se promueve a un **int**.

```cpp
#include <iostream>
#include <typeinfo>

using namespace std;

int main() {
    char char1 = 'a';

    auto promoted1 = char1 << 1;   // 194
    cout << typeid(promoted1).name() << endl;  // int

    auto promoted2 = char1 << 10;  // 99328
    cout << typeid(promoted2).name() << endl;  // int
}
```

## <a name="additional-details"></a>Detalles adicionales

El resultado de una operación de desplazamiento es indefinido si *additive-expression* es negativo o si *additive-expression* es mayor o igual que el número de bits de (promovido)  *expresión de desplazamiento*. No se realiza ninguna operación de desplazamiento si *additive-expression* es 0.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned int int1 = 4;
    bitset<32> b1{int1};
    cout << b1 << endl;    // 0b00000000'00000000'00000000'00000100

    unsigned int int2 = int1 << -3;  // C4293: '<<' : shift count negative or too big, undefined behavior
    unsigned int int3 = int1 >> -3;  // C4293: '>>' : shift count negative or too big, undefined behavior
    unsigned int int4 = int1 << 32;  // C4293: '<<' : shift count negative or too big, undefined behavior
    unsigned int int5 = int1 >> 32;  // C4293: '>>' : shift count negative or too big, undefined behavior
    unsigned int int6 = int1 << 0;
    bitset<32> b6{int6};
    cout << b6 << endl;    // 0b00000000'00000000'00000000'00000100 (no change)
}
```

## <a name="footnotes"></a>Notas al pie

<sup>1</sup> lo siguiente es la descripción de los operadores de desplazamiento en la especificación C ++ 11 de ISO (INCITS/ISO/IEC 14882-2011[2012]), secciones 5.8.2 y 5.8.3.

El valor de `E1 << E2` es `E1` desplazado a la izquierda `E2` posiciones de bits; los bits vacantes se rellenan con ceros. Si `E1` tiene un tipo sin signo, el valor del resultado es **E1 × 2**<sup>**E2**</sup>, reduciendo cada módulo en uno más que el valor máximo que se puede representar el tipo de resultado. De lo contrario, si `E1` tiene un tipo con signo y un valor no negativo, y **E1 × 2**<sup>**E2** </sup> es que se puede representar en el tipo sin signo correspondiente del tipo del resultado, a continuación, ese valor, convertido al tipo de resultado, es el valor resultante; en caso contrario, el comportamiento es indefinido.

El valor de `E1 >> E2` es `E1` desplazado a la derecha `E2` posiciones de bits. Si `E1` tiene un tipo sin signo o si `E1` tiene un tipo con signo y un valor no negativo, el valor del resultado es la parte entera del cociente de **E1/2**<sup>**E2** </sup>. Si `E1` tiene un tipo con signo y un valor negativo, el valor resultante está definido por la implementación.

## <a name="see-also"></a>Vea también

[Expresiones con operadores binarios](../cpp/expressions-with-binary-operators.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
