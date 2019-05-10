---
title: Clase de contenedor::swap
ms.date: 11/04/2016
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
ms.openlocfilehash: b344747c42e9b8b751b97747aacec0b39d10d6a1
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221519"
---
# <a name="container-classswap"></a>Clase de contenedor::swap

> [!NOTE]
> Este tema es de Microsoft C++ documentación como un ejemplo funcional de los contenedores usados en el C++ biblioteca estándar. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).

Intercambia las secuencias controladas entre **\*this** y su argumento.

## <a name="syntax"></a>Sintaxis

```cpp
void swap(Container& right);
```

## <a name="remarks"></a>Comentarios

Si **\*this.get\_allocator ==** _right_**.get_allocator**, realiza un intercambio en tiempo constante. De lo contrario, realiza varias asignaciones de elementos y llamadas de constructor proporcionales al número de elementos de ambas secuencias controladas.

## <a name="see-also"></a>Vea también

[Clase contenedora de ejemplo](../standard-library/sample-container-class.md)<br/>
