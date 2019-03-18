---
title: Constantes matemáticas
ms.date: 11/04/2016
f1_keywords:
- c.constants
helpviewer_keywords:
- M_PI constant
- M_PI_2 constant
- math constants
- M_2_PI constant
- M_1_PI constant
- M_E constant
- USE_MATH_DEFINES constant
- M_LOG2E constant
- M_LOG10E constant
- M_LN10 constant
- M_SQRT1_2 constant
- _USE_MATH_DEFINES constant
- M_PI_4 constant
- constants, math
- M_2_SQRTPI constant
- M_SQRT2 constant
- M_LN2 constant
ms.assetid: db533c3f-6ae8-4520-9d35-c8fabbef3529
ms.openlocfilehash: bd17004585e0238f36b939b19379ef62e349fac9
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744154"
---
# <a name="math-constants"></a>Constantes matemáticas

## <a name="syntax"></a>Sintaxis

```
#define _USE_MATH_DEFINES // for C++
#include <cmath>

#define _USE_MATH_DEFINES // for C
#include <math.h>
```

## <a name="remarks"></a>Comentarios

Los símbolos siguientes se definen para los valores de sus expresiones indicadas:

|Símbolo|Expresión|Valor|
|------------|----------------|-----------|
|M_E|h|2.71828182845904523536|
|M_LOG2E|log2(e)|1.44269504088896340736|
|M_LOG10E|log10(e)|0.434294481903251827651|
|M_LN2|ln(2)|0.693147180559945309417|
|M_LN10|ln(10)|2.30258509299404568402|
|M_PI|pi|3.14159265358979323846|
|M_PI_2|pi/2|1.57079632679489661923|
|M_PI_4|pi/4|0.785398163397448309616|
|M_1_PI|1/pi|0.318309886183790671538|
|M_2_PI|2/pi|0.636619772367581343076|
|M_2_SQRTPI|2/sqrt(pi)|1.12837916709551257390|
|M_SQRT2|sqrt(2)|1.41421356237309504880|
|M_SQRT1_2|1/sqrt(2)|0.707106781186547524401|

Las constantes matemáticas no están definidas en C o C++ estándar. Para poder utilizarlas, primero debe definir `_USE_MATH_DEFINES` y, después, incluir cmath o math.h.

El archivo ATLComTime.h incluye math.h cuando se compila el proyecto en modo de versión. Si usa una o varias de las constantes matemáticas en un proyecto que también incluye ATLComTime.h, debe definir `_USE_MATH_DEFINES` antes de incluir ATLComTime.h.

## <a name="see-also"></a>Vea también

[Constantes globales](../c-runtime-library/global-constants.md)
