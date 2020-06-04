---
title: event_source (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.event_source
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
ms.openlocfilehash: e187e57f21e9c94068c0b3396b93deed617fef2a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167074"
---
# <a name="event_source"></a>event_source

Crea un origen de eventos.

## <a name="syntax"></a>Sintaxis

```cpp
[ event_source(type, optimize=[speed | size], decorate=[true | false]) ]
```

### <a name="parameters"></a>Parámetros

*type*<br/>
Enumeración de uno de los valores siguientes:

- `native` para código de C/C++ no administrado (valor predeterminado para las clases no administradas).

- `com` para código COM. Debe usar `coclass` cuando `type`=`com`. Este valor requiere que se incluyan los archivos de encabezado siguientes:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*optimize*<br/>
Cuando el *tipo* es `native`, puede especificar `optimize=size`para indicar que hay 4 bytes de almacenamiento (mínimo) para todos los eventos de una clase o `optimize=speed` (valor predeterminado) para indicar que hay 4 * (número de eventos) bytes de almacenamiento.

*decorate*<br/>
Cuando el *tipo* es `native`, puede especificar `decorate=false`para indicar que el nombre expandido del archivo combinado (. MRG) no debe incluir el nombre de la clase envolvente. [/Fx](../../build/reference/fx-merge-injected-code.md) permite generar archivos .mrg. `decorate=false`, que es el valor predeterminado, da lugar a nombres de tipo completos en el archivo combinado.

## <a name="remarks"></a>Observaciones

El atributo de C++ **event_source** especifica que la clase o estructura a la que se aplica será un origen del evento.

**event_source** se usa junto con el atributo [event_receiver](event-receiver.md) y la palabra clave [__event](../../cpp/event.md) . Utilice `event_receiver` para crear receptores de eventos. Utilice **__event** en métodos del origen del evento para especificar dichos métodos como eventos.

> [!NOTE]
> Una clase o struct basada en plantilla no puede contener eventos.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|**coclase** cuando se `type`=`com`|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos de compilador](compiler-attributes.md)<br/>
[event_receiver](event-receiver.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Atributos de clase](class-attributes.md)
