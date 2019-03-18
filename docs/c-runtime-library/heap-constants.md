---
title: Constantes de montón
ms.date: 11/04/2016
f1_keywords:
- _HEAPBADPTR
- _HEAPEMPTY
- _HEAPBADBEGIN
- _HEAPOK
- _HEAPBADNODE
- _HEAPEND
helpviewer_keywords:
- _HEAPOK constants
- _HEAPEND constants
- HEAPBADBEGIN constants
- _HEAPBADNODE constants
- HEAPBADNODE constants
- HEAPBADPTR constants
- _HEAPEMPTY constants
- HEAPEND constants
- HEAPOK constants
- HEAPEMPTY constants
- _HEAPBADBEGIN constants
- _HEAPBADPTR constants
- heap constants
ms.assetid: 3f751bb9-2dc4-486f-b5f5-9061c96d3754
ms.openlocfilehash: 44c7a280ebffd0073f1dfb3a0a3cbdbd2efee0fb
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745369"
---
# <a name="heap-constants"></a>Constantes de montón

## <a name="syntax"></a>Sintaxis

```
#include <malloc.h>
```

## <a name="remarks"></a>Comentarios

Estas constantes proporcionan el valor devuelto mediante la indicación del estado del montón.

|Constante|Significado|
|--------------|-------------|
|`_HEAPBADBEGIN`|La información de encabezado inicial no se encontró o no era válida.|
|`_HEAPBADNODE`|Se encontró un nodo incorrecto o el montón está dañado.|
|`_HEAPBADPTR`|El campo **_pentry** de la estructura **_HEAPINFO** no contiene un puntero válido en el montón (solo la rutina `_heapwalk`).|
|`_HEAPEMPTY`|No se ha inicializado el montón.|
|`_HEAPEND`|Se ha llegado al final del montón correctamente (solo la rutina `_heapwalk`).|
|`_HEAPOK`|El montón es coherente (solo las rutinas `_heapset` y `_heapchk`). Ningún error hasta el momento; la estructura **_HEAPINFO** contiene información sobre la próxima entrada (solo la rutina `_heapwalk`).|

## <a name="see-also"></a>Vea también

[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
