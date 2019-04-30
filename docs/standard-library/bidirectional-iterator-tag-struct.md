---
title: bidirectional_iterator_tag (Struct)
ms.date: 11/04/2016
f1_keywords:
- xutility/std::bidirectional_iterator_tag
helpviewer_keywords:
- bidirectional_iterator_tag class
- bidirectional_iterator_tag struct
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
ms.openlocfilehash: c8296ddf30c0e2a3d34e69cbf079c0477e0e8b7a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62414088"
---
# <a name="bidirectionaliteratortag-struct"></a>bidirectional_iterator_tag (Struct)

Una clase que proporciona un tipo de valor devuelto para `iterator_category` función que representa un iterador bidireccional.

## <a name="syntax"></a>Sintaxis

```cpp
struct bidirectional_iterator_tag    : public forward_iterator_tag {};
```

## <a name="remarks"></a>Comentarios

Las clases de etiquetas de categoría se usan como etiquetas de compilación para la selección de algoritmos. La función de plantilla debe buscar la categoría más específica de su argumento de iterador para que pueda usar el algoritmo más eficaz en tiempo de compilación. Para cada tipo de iterador `Iterator`, `iterator_traits`< `Iterator`>:: **iterator_category** debe definirse para que sea la etiqueta de categoría más específica que describe el comportamiento del iterador.

El tipo es igual a **iterador** \< **Iter**>:: **iterator_category** cuando `Iter` describe un objeto que puede actuar como un bidireccional iterador.

## <a name="example"></a>Ejemplo

Vea [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) para obtener un ejemplo de cómo usar `bidirectional_iterator_tag`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iterator>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[forward_iterator_tag (Struct)](../standard-library/forward-iterator-tag-struct.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
