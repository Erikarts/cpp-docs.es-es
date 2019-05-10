---
title: CComSafeArrayBound (clase)
ms.date: 05/06/2019
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
helpviewer_keywords:
- CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
ms.openlocfilehash: 6d4650273661c0ce40558a37ef02bb2a3ff81809
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221139"
---
# <a name="ccomsafearraybound-class"></a>CComSafeArrayBound (clase)

Esta clase es un contenedor para un [SAFEARRAYBOUND](/windows/desktop/api/oaidl/ns-oaidl-tagsafearraybound) estructura.

## <a name="syntax"></a>Sintaxis

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CComSafeArrayBound](#ccomsafearraybound)|El constructor.|
|[GetCount](#getcount)|Llame a este método para devolver el número de elementos.|
|[GetLowerBound](#getlowerbound)|Llame a este método para devolver el límite inferior.|
|[GetUpperBound](#getupperbound)|Llame a este método para devolver el límite superior.|
|[SetCount](#setcount)|Llame a este método para establecer el número de elementos.|
|[SetLowerBound](#setlowerbound)|Llame a este método para establecer el límite inferior.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator =](#operator_eq)|Establece el `CComSafeArrayBound` a un nuevo valor.|

## <a name="remarks"></a>Comentarios

Esta clase es un contenedor para el `SAFEARRAYBOUND` estructura usa [CComSafeArray](../../atl/reference/ccomsafearray-class.md). Proporciona métodos para consultar y establecer los límites superiores e inferiores de una sola dimensión de un `CComSafeArray` objeto y el número de elementos que contiene. Multidimensional `CComSafeArray` objeto usa una matriz de `CComSafeArrayBound` objetos, uno para cada dimensión. Por lo tanto, cuando se usan métodos como [GetCount](#getcount), tenga en cuenta que este método no devolverá el número total de elementos de una matriz multidimensional.

**Encabezado:** atlsafe.h

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsafe.h

##  <a name="ccomsafearraybound"></a>  CComSafeArrayBound::CComSafeArrayBound

El constructor.

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>Parámetros

*ulCount*<br/>
Número de elementos de la matriz.

*lLowerBound*<br/>
El límite inferior desde la que se asigna el número de la matriz.

### <a name="remarks"></a>Comentarios

Si la matriz es necesario acceder desde un C++ programa, se recomienda que el límite inferior se define como 0. Puede ser preferible utilizar un valor de límite inferior diferente si la matriz es para su uso con otros lenguajes, como Visual Basic.

##  <a name="getcount"></a>  CComSafeArrayBound::GetCount

Llame a este método para devolver el número de elementos.

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos.

### <a name="remarks"></a>Comentarios

Si el asociado `CComSafeArray` objeto representa una matriz multidimensional, este método devolverá solo el número total de elementos de la dimensión más a la derecha. Use [CComSafeArray::GetCount](../../atl/reference/ccomsafearray-class.md#getcount) para obtener el número total de elementos.

##  <a name="getlowerbound"></a>  CComSafeArrayBound::GetLowerBound

Llame a este método para devolver el límite inferior.

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el límite inferior de la `CComSafeArrayBound` objeto.

##  <a name="getupperbound"></a>  CComSafeArrayBound::GetUpperBound

Llame a este método para devolver el límite superior.

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el límite superior de la `CComSafeArrayBound` objeto.

### <a name="remarks"></a>Comentarios

El límite superior depende del número de elementos y el valor de límite inferior. Por ejemplo, si el límite inferior es 0 y el número de elementos es 10, el límite superior se establecerá automáticamente al 9.

##  <a name="operator_eq"></a>  CComSafeArrayBound::operator =

Establece el `CComSafeArrayBound` a un nuevo valor.

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>Parámetros

*bound*<br/>
Objeto `CComSafeArrayBound`.

*ulCount*<br/>
Número de elementos.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la `CComSafeArrayBound` objeto.

### <a name="remarks"></a>Comentarios

El `CComSafeArrayBound` objeto se puede asignar una existente `CComSafeArrayBound`, o si se suministra el número de elementos, en el que caso el límite inferior se establece en 0 de forma predeterminada.

##  <a name="setcount"></a>  CComSafeArrayBound::SetCount

Llame a este método para establecer el número de elementos.

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>Parámetros

*ulCount*<br/>
Número de elementos.

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos de la `CComSafeArrayBound` objeto.

##  <a name="setlowerbound"></a>  CComSafeArrayBound::SetLowerBound

Llame a este método para establecer el límite inferior.

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>Parámetros

*lLowerBound*<br/>
El límite inferior.

### <a name="return-value"></a>Valor devuelto

Devuelve el nuevo límite inferior de la `CComSafeArrayBound` objeto.

### <a name="remarks"></a>Comentarios

Si la matriz es necesario acceder desde un programa de Visual C++, se recomienda que el límite inferior se define como 0. Puede ser preferible utilizar un valor de límite inferior diferente si la matriz es para su uso con otros lenguajes, como Visual Basic.

El límite superior depende del número de elementos y el valor de límite inferior. Por ejemplo, si el límite inferior es 0 y el número de elementos es 10, el límite superior se establecerá automáticamente al 9.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
