---
title: '&lt;functional&gt; (Operadores)'
ms.date: 11/04/2016
f1_keywords:
- functional/std::operator!=
- functional/std::operator==
helpviewer_keywords:
- functional operators
ms.assetid: d4b3c760-f3e2-4b65-bdaa-d42e8dd6f5e1
ms.openlocfilehash: 6fd4e25b3ca7b56e2221cb99b64f7c8e109bf452
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159564"
---
# <a name="ltfunctionalgt-operators"></a>&lt;functional&gt; (Operadores)

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a>  operator==

Comprueba si el objeto al que se puede llamar está vacío.

```cpp
template <class Fty>
bool operator==(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
bool operator==(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parámetros

*Fty*<br/>
Tipo de función que se va a contener.

*f*<br/>
Objeto de función

*npc*<br/>
Un puntero nulo.

### <a name="remarks"></a>Comentarios

Los dos operadores toman un argumento que es una referencia a un objeto `function` y un argumento que es una constante de puntero nulo. Ambos devuelven true únicamente si el objeto `function` está vacío.

### <a name="example"></a>Ejemplo

```cpp
// std__functional__operator_eq.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
{
    return (-val);
}

int main()
{
    std::function<int(int)> fn0;
    std::cout << std::boolalpha << "empty == "
        << (fn0 == 0) << std::endl;

    std::function<int(int)> fn1(neg);
    std::cout << std::boolalpha << "empty == "
        << (fn1 == 0) << std::endl;

    return (0);
}
```

```Output
empty == true
empty == false
```

## <a name="op_neq"></a> operator!=

Comprueba si el objeto al que se puede llamar no está vacío.

```cpp
template <class Fty>
bool operator!=(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
bool operator!=(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parámetros

*Fty*<br/>
Tipo de función que se va a contener.

*f*<br/>
Objeto de función

*npc*<br/>
Un puntero nulo.

### <a name="remarks"></a>Comentarios

Los dos operadores toman un argumento que es una referencia a un objeto `function` y un argumento que es una constante de puntero nulo. Ambos devuelven True solo si el objeto `function` no está vacío.

### <a name="example"></a>Ejemplo

```cpp
// std__functional__operator_ne.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0;
    std::cout << std::boolalpha << "not empty == "
        << (fn0 != 0) << std::endl;

    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "not empty == "
        << (fn1 != 0) << std::endl;

    return (0);
    }
```

```Output
not empty == false
not empty == true
```

## <a name="see-also"></a>Vea también

[\<functional>](../standard-library/functional.md)<br/>
