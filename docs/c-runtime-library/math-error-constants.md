---
title: Constantes de error matemático
ms.date: 11/04/2016
f1_keywords:
- _PLOSS
- _UNDERFLOW
- _TLOSS
- _SING
- _DOMAIN
- _OVERFLOW
helpviewer_keywords:
- _TLOSS constant
- _SING constant
- PLOSS constant
- UNDERFLOW constant
- _UNDERFLOW constant
- _OVERFLOW constant
- DOMAIN constant
- OVERFLOW constant
- TLOSS constant
- SING constant
- _DOMAIN constant
- _PLOSS constant
- math error constants
ms.assetid: 4be933a6-674e-45a5-8ac9-090023542f5b
ms.openlocfilehash: 3267a5053cb2cd18cfcb07473bbcc4d6f8295f5d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751861"
---
# <a name="math-error-constants"></a>Constantes de error matemático

## <a name="syntax"></a>Sintaxis

```
#include <math.h>
```

## <a name="remarks"></a>Comentarios

Las rutinas matemáticas de la biblioteca en tiempo de ejecución pueden generar constantes de error matemático.

Estos errores, que se describen como sigue, corresponden a los tipos de excepción definidos en MATH.H y los devuelve la función `_matherr` cuando se produce un error matemático.

|Constante|Significado|
|--------------|-------------|
|`_DOMAIN`|El argumento de la función está fuera del dominio de la función.|
|`_OVERFLOW`|El resultado es demasiado grande para representarlo en el tipo de valor devuelto de la función.|
|`_PLOSS`|Se ha producido una pérdida parcial de significación.|
|`_SING`|Singularidad del argumento: el argumento de la función tiene un valor no válido. (Por ejemplo, el valor 0 se pasa a la función que requiere un valor distinto de cero).|
|`_TLOSS`|Se ha producido una pérdida total de significación.|
|`_UNDERFLOW`|El resultado es demasiado pequeño para representarlo.|

## <a name="see-also"></a>Vea también

[_matherr](../c-runtime-library/reference/matherr.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
