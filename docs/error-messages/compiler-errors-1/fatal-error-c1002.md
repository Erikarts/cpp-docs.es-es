---
title: Error irrecuperable C1002
ms.date: 11/04/2016
f1_keywords:
- C1002
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
ms.openlocfilehash: 0588da99994be547742cc530ba435002a2d73359
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640510"
---
# <a name="fatal-error-c1002"></a>Error irrecuperable C1002

el compilador no tiene espacio en el montón en el paso 2

El compilador se quedó sin espacio de memoria dinámica durante su segunda pasada, probablemente debido a un programa con demasiados símbolos o expresiones complejas.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Dividir el archivo de código fuente en varios archivos más pequeños.

1. Divida las expresiones en subexpresiones más pequeñas.

1. Quitar otros programas o controladores que consuman memoria.