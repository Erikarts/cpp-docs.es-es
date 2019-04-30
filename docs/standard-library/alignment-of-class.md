---
title: alignment_of (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: 2633749a72ceeea197579dca4300b58250f60d73
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411089"
---
# <a name="alignmentof-class"></a>alignment_of (Clase)

Obtiene una alineación del tipo especificado. Este struct se implementa en términos de [alignof](../cpp/alignof-and-alignas-cpp.md). Use `alignof` directamente cuando solo sea necesario consultar un valor de alineación. Use alignment_of cuando necesite una constante integral, por ejemplo, al realizar un envío de etiquetas.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>Parámetros

*Ty*<br/>
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

La consulta de tipo contiene el valor de la alineación del tipo *Ty*.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[aligned_storage (Clase)](../standard-library/aligned-storage-class.md)<br/>
