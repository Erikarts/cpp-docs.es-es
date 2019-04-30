---
title: less_equal (struct)
ms.date: 11/04/2016
f1_keywords:
- functional/std::less_equal
helpviewer_keywords:
- less_equal function
- less_equal struct
ms.assetid: 32085782-c7e0-4310-9b40-8aa3c1bff211
ms.openlocfilehash: e1949477cc130bbbc8cdfeea082ec73f14bf4aad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223948"
---
# <a name="lessequal-struct"></a>less_equal (struct)

Predicado binario que realiza la operación menor o igual que (`operator<=`) sobre sus argumentos.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type = void>
struct less_equal : public binary_function <Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator<=
template <>
struct less_equal<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const
    -> decltype(std::forward<T>(Left) <= std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parámetros

*Tipo*, *T*, *U* cualquier tipo que admita un `operator<=` que toma operandos de los tipos especificados o deducidos.

*Izquierda*<br/>
Operando izquierdo de la operación menor o igual que. La plantilla no especializada toma un argumento de referencia de valor l de tipo *tipo*. La plantilla especializada realiza el reenvío de valor l directo y los argumentos de referencia de valor r del tipo deducen *T*.

*Derecha*<br/>
Operando derecho de la operación menor o igual que. La plantilla no especializada toma un argumento de referencia de valor l de tipo *tipo*. La plantilla especializada realiza el reenvío de valor l directo y los argumentos de referencia de valor r del tipo deducen *U*.

## <a name="return-value"></a>Valor devuelto

Resultado de `Left <= Right`. La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator<=`.

## <a name="remarks"></a>Comentarios

El predicado binario `less_equal` <  `Type`> proporciona una ordenación débil estricta de un conjunto de valores de elemento de tipo *tipo* en clases de equivalencia, si y solo si este tipo satisface el estándar de matemático requisitos para lo que se ordenan. Las especializaciones para cualquier tipo de puntero producen una ordenación total de los elementos, en la que todos los elementos de valores distintos están ordenados unos con respecto a otros.

## <a name="example"></a>Ejemplo

```cpp
// functional_less_equal.cpp
// compile with: /EHsc
#define _CRT_RAND_S
#include <stdlib.h>
#include <vector>
#include <algorithm>
#include <functional>
#include <cstdlib>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;
   vector <int>::reverse_iterator rIter1;
   unsigned int randomNumber;

   int i;
   for ( i = 0 ; i < 5 ; i++ )
   {
      if ( rand_s( &randomNumber ) == 0 )
      {
         // Convert the random number to be between 1 - 50000
         // This is done for readability purposes
         randomNumber = ( unsigned int) ((double)randomNumber /
            (double) UINT_MAX * 50000) + 1;

         v1.push_back( randomNumber );
      }
   }
   for ( i = 0 ; i < 3 ; i++ )
   {
      v1.push_back( 2836 );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use the binary predicate less_equal<int>( )
   sort( v1.begin( ), v1.end( ), less_equal<int>( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

## <a name="sample-output"></a>Resultados del ejemplo

```Output
Original vector v1 = (31247 37154 48755 15251 6205 2836 2836 2836)
Sorted vector v1 = (2836 2836 2836 6205 15251 31247 37154 48755)
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<functional>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
