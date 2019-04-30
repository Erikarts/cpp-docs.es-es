---
title: bad_target (Clase)
ms.date: 11/04/2016
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
ms.openlocfilehash: 04489151cedf1a47aeebd883e76b8d26b51031ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62337770"
---
# <a name="badtarget-class"></a>bad_target (Clase)

Esta clase describe una excepción que se produce cuando un bloque de mensajería recibe un puntero a un destino que no es válido para la operación que se realiza.

## <a name="syntax"></a>Sintaxis

```
class bad_target : public std::exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[bad_target](#ctor)|Sobrecargado. Construye un objeto `bad_target`.|

## <a name="remarks"></a>Comentarios

Esta excepción se produce normalmente por razones como un destino al intentar utilizar un mensaje que se reserva para un destino diferente o liberando una reserva que no contiene.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`bad_target`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

**Espacio de nombres:** simultaneidad

##  <a name="ctor"></a> bad_target

Construye un objeto `bad_target`.

```
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md)
