---
title: pointer_to_unary_function (Clase)
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_unary
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
ms.openlocfilehash: 710453711e60f4607a20eb3e71b65127c8dd5316
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370273"
---
# <a name="pointertounaryfunction-class"></a>pointer_to_unary_function (Clase)

Convierte un puntero a función unaria en una función unaria adaptable. En desuso en C ++ 11, se ha quitado en C ++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Arg, class Result>
class pointer_to_unary_function
    : public unary_function<Arg, Result>
{
public:
    explicit pointer_to_unary_function(Result(*pfunc)(Arg));
    Result operator()(Arg left) const;
};
```

### <a name="parameters"></a>Parámetros

*pfunc*<br/>
La función binaria que se va a convertir.

*left*<br/>
El objeto al que *\*pfunc* está llamado.

## <a name="return-value"></a>Valor devuelto

La clase de plantilla almacena una copia de `pfunc`. Define su función miembro `operator()` para que devuelva (\* **pfunc**)(_ *Left*).

## <a name="remarks"></a>Comentarios

Un puntero de función unaria es un objeto de función y puede pasarse a cualquier algoritmo de la biblioteca estándar de C++ que esté esperando una función unaria como un parámetro, pero no es adaptable. Para usarlo con un adaptador, por ejemplo al enlazar un valor a este o usándolo con un negador, debe proporcionarse con los tipos anidados `argument_type` y `result_type` que hacen posible dicha adaptación. La conversión mediante `pointer_to_unary_function` permite a los adaptadores de función que funcionen con punteros de función binaria.

## <a name="example"></a>Ejemplo

El constructor de `pointer_to_unary_function` no suele usarse directamente. Vea la función del asistente [ptr_fun](../standard-library/functional-functions.md#ptr_fun) para obtener un ejemplo de cómo declarar y usar el predicador del adaptador de `pointer_to_unary_function`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<functional>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
