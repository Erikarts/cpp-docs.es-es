---
title: OnCmdMsg (Controlador)
ms.date: 11/04/2016
f1_keywords:
- OnCmdMsg
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
ms.openlocfilehash: 6ed2e4c09e2fe413d29ad9953dbb8a03c106e86c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385302"
---
# <a name="oncmdmsg-handler"></a>OnCmdMsg (Controlador)

Para llevar a cabo el enrutamiento de comandos, llama cada destino del comando el `OnCmdMsg` función de miembro del destino del comando siguiente en la secuencia. Uso de destino del comando `OnCmdMsg` para determinar si puede controlar un comando y su enrutamiento a otro destino de comando si no puede controlarla.

Cada clase de destino del comando puede reemplazar el `OnCmdMsg` función miembro. Las invalidaciones permiten a cada clase enrutar comandos a un determinado destino siguiente. Una ventana de marco, por ejemplo, siempre enruta los comandos a su ventana secundaria actual o la vista, tal como se muestra en la tabla [ruta estándar de comando](../mfc/command-routing.md).

El valor predeterminado `CCmdTarget` implementación de `OnCmdMsg` utiliza el mapa de mensajes de la clase de destino del comando para buscar una función de controlador para cada mensaje de comando que recibe, de la misma manera que se va a buscar mensajes estándar. Si encuentra a una coincidencia, llama al controlador. Búsqueda de mapa de mensajes se explica en [cómo el marco de las búsquedas de mapas de mensajes](../mfc/how-the-framework-searches-message-maps.md).

## <a name="see-also"></a>Vea también

[Cómo el marco llama a un controlador](../mfc/how-the-framework-calls-a-handler.md)
