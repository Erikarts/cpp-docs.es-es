---
title: decay (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::decay
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
ms.openlocfilehash: 3b22dfecb1162ce67a0d648197465115acb044ba
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688113"
---
# <a name="decay-class"></a>decay (Clase)

Genera el tipo tal y como se pasa por valor. Crea el tipo sin referencia, no constante y no volátil, o crea un puntero al tipo a partir de una función o un tipo de matriz.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct decay;

template <class T>
using decay_t = typename decay<T>::type;
```

### <a name="parameters"></a>Parámetros

*T* \
Tipo que se va a modificar.

## <a name="remarks"></a>Comentarios

Use la plantilla decay para producir el tipo resultante como si el tipo se hubiera pasado por valor como un argumento. La definición de tipo de miembro de plantilla de clase `type` contiene un tipo modificado que se define en las siguientes fases:

- El tipo `U` se define como `remove_reference<T>::type`.

- Si `is_array<U>::value` es True, el tipo modificado `type` es `remove_extent<U>::type *`.

- De lo contrario, si `is_function<U>::value` es True, el tipo modificado `type` es `add_pointer<U>::type`.

- De lo contrario, el tipo modificado `type` es `remove_cv<U>::type`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
