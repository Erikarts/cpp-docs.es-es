---
title: Clase is_literal_type
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_literal_type
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
ms.openlocfilehash: 450c32d050a18f64e71992bd7a30412ebafe93de
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456219"
---
# <a name="isliteraltype-class"></a>Clase is_literal_type

Comprueba si un tipo se puede usar como una variable `constexpr` o si se puede construir, usar o devolver desde funciones `constexpr`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* es un *tipo literal*; en caso contrario, contiene false. Un tipo literal es **void**, un tipo escalar, un tipo de referencia, una matriz de tipo literal o un tipo de clase literal. Un tipo de clase literal es un tipo de clase que tiene un destructor trivial, es o bien un tipo de agregado o bien contiene al menos un constructor `constexpr` que no es de movimiento y no es de copia, y todas sus clases base y miembros de datos no estáticos son tipos literales no volátiles. Aunque el tipo de un literal es siempre un tipo literal, el concepto de tipo literal incluye todo lo que el compilador evalúe como `constexpr` en tiempo de compilación.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
