---
title: _CIsin
ms.date: 04/10/2018
api_name:
- _CIsin
api_location:
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CIsin
- _CIsin
helpviewer_keywords:
- _CIsin intrinsic
- CIsin intrinsic
ms.assetid: f215f39a-2341-4f1c-ba8e-cb522451ceb2
ms.openlocfilehash: 66f26e9fa4dd08d18b15deca4efa40c236e092c9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944545"
---
# <a name="_cisin"></a>_CIsin

Calcula el seno del valor superior de la pila de punto flotante.

## <a name="syntax"></a>Sintaxis

```C
void __cdecl _CIsin();
```

## <a name="remarks"></a>Comentarios

Esta versión intrínseca de la función [sin](../c-runtime-library/reference/sin-sinf-sinl.md) tiene una convención de llamada especializada que el compilador entiende. Acelera la ejecución porque evita que se generen copias y ayuda con la asignación de registros.

El valor resultante se inserta en la parte superior de la pila de punto flotante.

## <a name="requirements"></a>Requisitos

**Plataforma:** x86

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[sin, sinf, sinl](../c-runtime-library/reference/sin-sinf-sinl.md)<br/>
