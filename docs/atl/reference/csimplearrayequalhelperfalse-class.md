---
title: CSimpleArrayEqualHelperFalse (clase)
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
ms.openlocfilehash: 35207fdcbffc0e0367d86682b5f731eef617d761
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277960"
---
# <a name="csimplearrayequalhelperfalse-class"></a>CSimpleArrayEqualHelperFalse (clase)

Esta clase es una aplicación auxiliar para el [CSimpleArray](../../atl/reference/csimplearray-class.md) clase.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class CSimpleArrayEqualHelperFalse
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Una clase derivada.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|(Estático) Devuelve "false".|

## <a name="remarks"></a>Comentarios

Esta clase de rasgos es un complemento para el `CSimpleArray` clase. TI siempre devuelve false y además, llamará a `ATLASSERT` con el argumento false si nunca se hace referencia. En situaciones donde no se define lo suficientemente la prueba de igualdad, esta clase permite que una matriz que contiene elementos para funcionar correctamente para la mayoría de los métodos, pero producirá un error de forma bien definida para los métodos que dependen de las comparaciones como [CSimpleArray:: Buscar](../../atl/reference/csimplearray-class.md#find).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpcoll.h

##  <a name="isequal"></a>  CSimpleArrayEqualHelperFalse::IsEqual

Devuelve false.

```
static bool IsEqual(const T&, const T&);
```

### <a name="return-value"></a>Valor devuelto

Devuelve false.

### <a name="remarks"></a>Comentarios

Este método siempre devuelve false y llamará a `ATLASSERT` con el argumento false si se hace referencia. El propósito de `CSimpleArrayEqualHelperFalse::IsEqual` es forzar a métodos mediante comparaciones genere un error de una manera bien definida cuando las pruebas de igualdad no se han definido correctamente.

## <a name="see-also"></a>Vea también

[CSimpleArrayEqualHelper (clase)](../../atl/reference/csimplearrayequalhelper-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
