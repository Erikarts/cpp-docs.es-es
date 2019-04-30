---
title: _com_ptr_t::QueryInterface
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
ms.openlocfilehash: 42953c92e4cf31b5ccd02dd51811fc1fdeedbcaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399283"
---
# <a name="comptrtqueryinterface"></a>_com_ptr_t::QueryInterface

**Específicos de Microsoft**

Las llamadas del **QueryInterface** función miembro de `IUnknown` en el puntero de interfaz encapsulado.

## <a name="syntax"></a>Sintaxis

```
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType*& p
) throw ( );
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType** p
) throw( );
```

#### <a name="parameters"></a>Parámetros

*iid*<br/>
`IID` de un puntero de interfaz.

*p*<br/>
Puntero de interfaz sin formato.

## <a name="remarks"></a>Comentarios

Las llamadas `IUnknown::QueryInterface` en el puntero de interfaz encapsulado con los valores especificados `IID` y devuelve el puntero de interfaz sin formato resultante en *p*. Esta rutina devuelve el valor HRESULT para indicar éxito o error.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)