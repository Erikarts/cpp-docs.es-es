---
title: Platform::DisconnectedException (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::DisconnectedException
- VCCORLIB/Platform::DisconnectedException::DisconnectedException
helpviewer_keywords:
- Platform::DisconnectedException
ms.assetid: c25e0d64-5bff-4c21-88e5-c4ec2776fa7f
ms.openlocfilehash: 56276a7d09cc82e05886c2c67a4784993083adb5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57752017"
---
# <a name="platformdisconnectedexception-class"></a>Platform::DisconnectedException (Clase)

Se produce cuando un objeto de proxy COM intenta hacer referencia a un servidor COM que ya no existe.

## <a name="syntax"></a>Sintaxis

```
public ref class DisconnectedException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Comentarios

Cuando la clase A hace referencia a otra clase (clase B) que está en un proceso independiente, la clase A requiere un objeto de proxy para comunicarse con el servidor COM fuera de proceso que contiene la clase B. A veces se puede agotar la memoria del servidor sin que la clase A lo sepa. En ese caso, se produce la excepción RPC_E_DISCONNECTED y se convierte a Platform::DisconnectedException. Un escenario en el que se produce consiste en un origen de eventos que invoca un delegado transferido, pero el delegado se destruye en algún punto después de suscribirse al evento. Cuando esto ocurre, el origen de eventos elimina el delegado de la lista de invocación.

Para obtener más información, consulta la clase [COMException](../cppcx/platform-comexception-class.md) .

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres**: Plataforma

**Metadatos:** platform.winmd

## <a name="see-also"></a>Vea también

[Platform::COMException (Clase)](../cppcx/platform-comexception-class.md)
