---
title: Utilizar varios conjuntos de resultados de un procedimiento almacenado
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
ms.openlocfilehash: fe41bfe1d9fb0207f55d2cd653a56a1ff00ce2d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570685"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>Utilizar varios conjuntos de resultados de un procedimiento almacenado

Mayoría de los procedimientos almacenados devuelven varios conjuntos de resultados. Estos procedimientos almacenados suelen incluyen una o varias instrucciones select. El consumidor debe tener en cuenta esta inclusión para controlar todos los conjuntos de resultados.

## <a name="to-handle-multiple-result-sets"></a>Para controlar varios resultados establece

1. Crear un `CCommand` clase con `CMultipleResults` como un argumento de plantilla y el descriptor de acceso de su elección, normalmente un descriptor de acceso dinámico o manual. Si usa otro tipo de descriptor de acceso, es posible que no pueda determinar las columnas de salida para cada conjunto de filas.

1. Ejecute el procedimiento almacenado como de costumbre y enlazar las columnas (vea [¿cómo puedo recuperar datos?](../../data/oledb/fetching-data.md)).

1. Usar los datos.

1. Llame a `GetNextResult` en el `CCommand` clase. Si hay otro conjunto de filas de resultados, `GetNextResult` devuelve S_OK y debe volver a enlazar las columnas si usas un descriptor de acceso manual. Si `GetNextResult` devuelve un error, hay conjuntos de no hay más resultados disponibles.

## <a name="see-also"></a>Vea también

[Usar procedimientos almacenados](../../data/oledb/using-stored-procedures.md)