---
title: Invalidar el enrutamiento de comandos estándar
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
ms.openlocfilehash: 5383c1053894d44e23baf51b19ac3df4e60158e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410166"
---
# <a name="overriding-the-standard-command-routing"></a>Invalidar el enrutamiento de comandos estándar

En raras ocasiones cuando se debe implementar alguna variación del enrutamiento de marco estándar, puede invalidarlo. La idea consiste en cambiar el enrutamiento en una o más clases invalidando `OnCmdMsg` en esas clases. Hacer esto:

- En la clase que interrumpe el orden para pasar a un objeto no predeterminado.

- En el nuevo objeto no predeterminado o en destinos de comando a su vez podría pasar comandos.

Si inserta un nuevo objeto en el enrutamiento, su clase debe ser una clase de destino del comando. En las versiones de reemplazo `OnCmdMsg`, asegúrese de llamar a la versión que está reemplazando. Consulte la [OnCmdMsg](../mfc/reference/ccmdtarget-class.md#oncmdmsg) función miembro de clase `CCmdTarget` en el *referencia de MFC* y las versiones de clases como `CView` y `CDocument` en el código de origen proporcionado para obtener ejemplos.

## <a name="see-also"></a>Vea también

[Cómo el marco llama a un controlador](../mfc/how-the-framework-calls-a-handler.md)
