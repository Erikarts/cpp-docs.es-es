---
title: Usar IDispEventImpl (ATL)
ms.date: 11/04/2016
f1_keywords:
- IDispEventImpl
helpviewer_keywords:
- IDispEventImpl class, using
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
ms.openlocfilehash: 5175ffd615837fb10ba1bbced5da7f7733b6e193
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301563"
---
# <a name="using-idispeventimpl"></a>Usar IDispEventImpl

Cuando se usa `IDispEventImpl` para controlar eventos, tendrá que:

- Derive la clase de [IDispEventImpl](../atl/reference/idispeventimpl-class.md).

- Agregar un mapa de receptores de eventos a la clase.

- Agregar entradas en el mapa de receptor de eventos mediante el [SINK_ENTRY](reference/composite-control-macros.md#sink_entry) o [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex) macro.

- Implemente los métodos que le interesa en el control.

- Aconsejar y desaconsejar el origen del evento.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo controlar el `DocumentChange` eventos desencadenados por la palabra **aplicación** objeto. Este evento se define como un método en el `ApplicationEvents` dispinterface.

El ejemplo proviene del [ejemplo ATLEventHandling](../visual-cpp-samples.md).

```cpp
[ uuid(000209F7-0000-0000-C000-000000000046), hidden ]
dispinterface ApplicationEvents {
properties:
methods:
    [id(0x00000001), restricted, hidden]
    void Startup();

    [id(0x00000002)]
    void Quit();

    [id(0x00000003)]
    void DocumentChange();
};
```

El ejemplo se utiliza `#import` para generar los archivos de encabezado requeridos desde la biblioteca de tipos de Word. Si desea usar este ejemplo con otras versiones de Word, debe especificar el archivo dll de mso correcto. Por ejemplo, Office 2000 proporciona mso9.dll y OfficeXP proporciona mso.dll. Este código se ha simplificado de stdafx.h:

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventimpl_1.h)]

Aparece el siguiente código en NotSoSimple.h. El código relevante se anota mediante comentarios:

[!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/cpp/using-idispeventimpl_2.h)]

## <a name="see-also"></a>Vea también

[Control de eventos](../atl/event-handling-and-atl.md)<br/>
[Ejemplo ATLEventHandling](../visual-cpp-samples.md)
