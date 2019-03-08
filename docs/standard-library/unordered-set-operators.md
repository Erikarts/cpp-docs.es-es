---
title: Operadores de &lt;unordered_set&gt;
ms.date: 11/04/2016
f1_keywords:
- unordered_set/std::operator!=
- unordered_set/std::operator==
ms.assetid: 8653eea6-12f2-4dd7-aa2f-db38a71599a0
ms.openlocfilehash: b86dd81a7bc4085c86e87d5d81b59e795ce7ae8a
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523187"
---
# <a name="ltunorderedsetgt-operators"></a>Operadores de &lt;unordered_set&gt;

|||||
|-|-|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|[operator!=](#op_neq_unordered_multiset)|[operator==](#op_eq_eq_unordered_multiset)|

## <a name="op_neq"></a> operator!=

Comprueba si el objeto [unordered_set](../standard-library/unordered-set-class.md) del lado izquierdo del operador no es igual que el objeto unordered_set del lado derecho.

```cpp
bool operator!=(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto de tipo `unordered_set`.

*right*<br/>
Objeto de tipo `unordered_set`.

### <a name="return-value"></a>Valor devuelto

**True** si los unordered_set no son iguales; **false** si son iguales.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos unordered_set no se ve afectada por el orden arbitrario en el que almacenan sus elementos. Dos unordered_set son iguales si tienen el mismo número de elementos y los elementos de un contenedor son una permutación de los elementos del otro contenedor. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// unordered_set_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_set<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 != c2: " << (c1 != c2) << endl;
   cout << "c1 != c3: " << (c1 != c3) << endl;
   cout << "c2 != c3: " << (c2 != c3) << endl;

    return (0);
}
```

**Salida:**

`c1 != c2: true`

`c1 != c3: false`

`c2 != c3: true`

## <a name="op_eq_eq"></a>  operator==

Comprueba si el objeto [unordered_set](../standard-library/unordered-set-class.md) del lado izquierdo del operador es igual que el objeto unordered_set del lado derecho.

```cpp
bool operator==(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto de tipo `unordered_set`.

*right*<br/>
Objeto de tipo `unordered_set`.

### <a name="return-value"></a>Valor devuelto

**True** si los unordered_set son iguales; **false** si no son iguales.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos unordered_set no se ve afectada por el orden arbitrario en el que almacenan sus elementos. Dos unordered_set son iguales si tienen el mismo número de elementos y los elementos de un contenedor son una permutación de los elementos del otro contenedor. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// unordered_set_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_set<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 == c2: " << (c1 == c2) << endl;
   cout << "c1 == c3: " << (c1 == c3) << endl;
   cout << "c2 == c3: " << (c2 == c3) << endl;

    return (0);
}
```

**Resultado:**

`c1 == c2: false`

`c1 == c3: true`

`c2 == c3: false`

## <a name="op_neq_unordered_multiset"></a> operator!=

Comprueba si el objeto [unordered_multiset](../standard-library/unordered-multiset-class.md) del lado izquierdo del operador no es igual que el objeto unordered_multiset del lado derecho.

```cpp
bool operator!=(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto de tipo `unordered_multiset`.

*right*<br/>
Objeto de tipo `unordered_multiset`.

### <a name="return-value"></a>Valor devuelto

**True** si los unordered_multiset no son iguales; **false** si son iguales.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos unordered_multiset no se ve afectada por el orden arbitrario en el que almacenan sus elementos. Dos unordered_multiset son iguales si tienen el mismo número de elementos y los elementos de un contenedor son una permutación de los elementos del otro contenedor. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// unordered_multiset_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_multiset<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');
    c1.insert('c');

    c2.insert('c');
    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 != c2: " << (c1 != c2) << endl;
   cout << "c1 != c3: " << (c1 != c3) << endl;
   cout << "c2 != c3: " << (c2 != c3) << endl;

    return (0);
}
```

**Salida:**

`c1 != c2: true`

`c1 != c3: false`

`c2 != c3: true`

## <a name="op_eq_eq_unordered_multiset"></a>  operator==

Comprueba si el objeto [unordered_multiset](../standard-library/unordered-multiset-class.md) del lado izquierdo del operador es igual que el objeto unordered_multiset del lado derecho.

```cpp
bool operator==(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Objeto de tipo `unordered_multiset`.

*right*<br/>
Objeto de tipo `unordered_multiset`.

### <a name="return-value"></a>Valor devuelto

**True** si los unordered_multiset son iguales; **false** si no son iguales.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos unordered_multiset no se ve afectada por el orden arbitrario en el que almacenan sus elementos. Dos unordered_multiset son iguales si tienen el mismo número de elementos y los elementos de un contenedor son una permutación de los elementos del otro contenedor. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// unordered_multiset_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_multiset<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');
    c1.insert('c');

    c2.insert('c');
    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 == c2: " << (c1 == c2) << endl;
   cout << "c1 == c3: " << (c1 == c3) << endl;
   cout << "c2 == c3: " << (c2 == c3) << endl;

    return (0);
}
```

**Salida:**

`c1 == c2: false`

`c1 == c3: true`

`c2 == c3: false`

## <a name="see-also"></a>Vea también

[<unordered_set>](../standard-library/unordered-set.md)<br/>
