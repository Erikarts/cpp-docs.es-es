---
title: CSimpleArrayEqualHelper (clase)
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
ms.openlocfilehash: 8b7e32ddab5b2f0667b17b0f127ac2e7e5d9a426
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293256"
---
# <a name="csimplearrayequalhelper-class"></a>CSimpleArrayEqualHelper (clase)

Esta clase es una aplicación auxiliar para el [CSimpleArray](../../atl/reference/csimplearray-class.md) clase.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class CSimpleArrayEqualHelper
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Una clase derivada.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|(Estático) Comprueba si dos `CSimpleArray` igualdad de los elementos de objeto.|

## <a name="remarks"></a>Comentarios

Esta clase de rasgos es un complemento para el `CSimpleArray` clase. Proporciona un método para comparar dos elementos almacenados en un `CSimpleArray` objeto. De forma predeterminada, los elementos se comparan mediante **operator=()**, pero si la matriz contiene los tipos de datos complejos que no tienen su propio operador de igualdad, deberá invalidar esta clase.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpcoll.h

##  <a name="isequal"></a>  CSimpleArrayEqualHelper::IsEqual

Comprueba si dos `CSimpleArray` igualdad de los elementos de objeto.

```
static bool IsEqual(
    const T& t1,
    const T& t2);
```

### <a name="parameters"></a>Parámetros

*t1*<br/>
Un objeto de tipo T.

*t2*<br/>
Un objeto de tipo T.

### <a name="return-value"></a>Valor devuelto

Devuelve true si los elementos si no son iguales, es false.

## <a name="see-also"></a>Vea también

[CSimpleArray (clase)](../../atl/reference/csimplearray-class.md)<br/>
[CSimpleArrayEqualHelperFalse (clase)](../../atl/reference/csimplearrayequalhelperfalse-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
