---
title: Objetos de interfaz de usuario e identificadores de comando
ms.date: 11/19/2018
helpviewer_keywords:
- keyboard shortcuts, associating with IDs
- MFC, command routing
- toolbar controls [MFC], command ID
- menu items, associating with IDs
- user interface objects [MFC], associating with IDs
- command IDs, user interface objects
- command routing [MFC], MFC
- command handling [MFC], user-interface objects
ms.assetid: 4ea19e9b-ed1e-452e-bd33-7f509107a45b
ms.openlocfilehash: 54372facc51062add122c1db2e01e3081127512e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180627"
---
# <a name="user-interface-objects-and-command-ids"></a>Objetos de interfaz de usuario e identificadores de comando

Los elementos de menú, botones de barra de herramientas y teclas de aceleración son "objetos de interfaz de usuario" capaces de generar comandos. Cada objeto de interfaz de usuario de este tipo tiene un identificador. Asociar un objeto de interfaz de usuario con un comando, se asigna el mismo identificador al objeto y el comando. Como se explica en [mensajes](../mfc/messages.md), los comandos se implementan como mensajes especiales. La ilustración "Comandos en el marco de trabajo" a continuación muestra cómo el marco de trabajo administra los comandos. Cuando un objeto de interfaz de usuario genera un comando, como `ID_EDIT_CLEAR_ALL`, uno de los objetos en la aplicación controla el comando, en la ilustración siguiente, el objeto de documento `OnEditClearAll` función se llama a través del mapa de mensajes del documento.

![Comandos en el marco](../mfc/media/vc385p1.gif "comandos en el marco de trabajo") <br/>
Comandos de Framework

La ilustración "Comando Actualizar en el marco de trabajo" muestra cómo MFC actualiza los objetos de interfaz de usuario como elementos de menú y los botones de barra de herramientas. Antes de que despliega un menú o durante el bucle de inactividad en el caso de los botones de barra de herramientas, MFC enruta un comando de actualización. En la ilustración siguiente, llama a su controlador de comando de actualización, el objeto de documento `OnUpdateEditClearAll`, para habilitar o deshabilitar el objeto de interfaz de usuario.

![Comando de actualización en el marco de trabajo](../mfc/media/vc385p2.png "comando Actualizar en el marco de trabajo") <br/>
Actualización de comandos de Framework

## <a name="see-also"></a>Vea también

[Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)
