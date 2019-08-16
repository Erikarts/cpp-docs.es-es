---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: d07e995be0ecd99974356a7516e7c4deee677637
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403274"
---
# <a name="varianttsetstring"></a>_variant_t::SetString

**Específicos de Microsoft**

Asigna una cadena a este objeto `_variant_t`.

## <a name="syntax"></a>Sintaxis

```
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>Parámetros

*pSrc*<br/>
Puntero a la cadena de caracteres.

## <a name="remarks"></a>Comentarios

Convierte una cadena de caracteres ANSI en una cadena `BSTR` Unicode y la asigna a este objeto `_variant_t`.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_variant_t (Clase)](../cpp/variant-t-class.md)