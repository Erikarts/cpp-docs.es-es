---
title: CLOCKS_PER_SEC, CLK_TCK
ms.date: 11/04/2016
f1_keywords:
- CLOCKS_PER_SEC
- CLK_TCK
helpviewer_keywords:
- CLOCKS_PER_SEC
- CLK_TCK constant
ms.assetid: bc285106-383d-44cb-91bf-276ad7de57bf
ms.openlocfilehash: a604425809f43be238cbcc7b9148782bb937e00f
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220366"
---
# <a name="clockspersec-clktck"></a>CLOCKS_PER_SEC, CLK_TCK

## <a name="syntax"></a>Sintaxis

```
#include <time.h>
```

## <a name="remarks"></a>Comentarios

El tiempo en segundos es el valor devuelto por la función `clock`, dividido entre `CLOCKS_PER_SEC`. `CLK_TCK` es equivalente, pero se considera obsoleto.

## <a name="see-also"></a>Vea también

[clock](../c-runtime-library/reference/clock.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
