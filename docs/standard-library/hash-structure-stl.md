---
title: Estructura hash (biblioteca estándar de C++) | Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- thread/std::hash
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
ms.openlocfilehash: e6d0cea7bfc8cd745e7276f7fc29d493f178fc9b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451950"
---
# <a name="hash-structure-c-standard-library"></a>Estructura hash (biblioteca estándar de C++)

Define una función miembro que devuelve un valor que se determina de forma exclusiva mediante `Val`. La función miembro define una función [hash](../standard-library/hash-class.md) adecuada para asignar valores de tipo `thread::id` a una distribución de valores de índice.

## <a name="syntax"></a>Sintaxis

```cpp
template <>
struct hash<thread::id> :
    public unary_function<thread::id, size_t>
{
    size_t operator()(thread::id Val) const;

};
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<subproceso >

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<thread>](../standard-library/thread.md)\
[Struct unary_function](../standard-library/unary-function-struct.md)
