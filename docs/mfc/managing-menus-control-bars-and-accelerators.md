---
title: Administrar menús, barras de control y aceleradores
ms.date: 11/04/2016
helpviewer_keywords:
- MDI [MFC], frame windows
- control bars [MFC], updating in frame windows
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- accelerator tables [MFC]
- sharing menus [MFC]
- updating user-interface objects [MFC]
- frame windows [MFC], updating
- status bars [MFC], updating
ms.assetid: 97ca1997-06df-4373-b023-4f7ecd81047b
ms.openlocfilehash: 9a089829658265cd835a8c7344aa5bc45fbc109a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226175"
---
# <a name="managing-menus-control-bars-and-accelerators"></a>Administrar menús, barras de control y aceleradores

La ventana de marco administra la actualización de los objetos de interfaz de usuario, incluidos menús, botones de barra de herramientas, la barra de estado y los aceleradores. También administra el uso compartido de la barra de menús en las aplicaciones MDI.

## <a name="managing-menus"></a>Administrar menús

La ventana de marco participa en la actualización de elementos de interfaz de usuario mediante el mecanismo ON_UPDATE_COMMAND_UI descrito en [cómo actualizar objetos de interfaz de usuario](../mfc/how-to-update-user-interface-objects.md). Los botones de barras de herramientas y barras de controles se actualizan durante el bucle de inactividad. Elementos de menú en los menús desplegables en la barra de menús se actualizan justo antes de que quita el menú.

Para aplicaciones MDI, la ventana de marco MDI administra la barra de menús y el título. Una ventana marco MDI posee un menú predeterminado que se utiliza como la barra de menús cuando no hay ningún ventanas secundarias MDI activos. Cuando hay secundarias activas, barra de menús de la ventana de marco MDI toma el menú de la ventana secundaria MDI activa. Si una aplicación MDI admite varios tipos de documentos, como documentos de gráfico y hojas de cálculo, cada tipo incluye sus propios menús en la barra de menús y cambia el título de la ventana de marco principal.

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) proporciona implementaciones predeterminadas para los comandos estándar en el menú Ventana que aparece para las aplicaciones MDI. En concreto, el comando nueva ventana (ID_WINDOW_NEW) se implementa para crear una nueva ventana de marco y la vista en el documento actual. Deberá reemplazar estas implementaciones solo si necesita personalización avanzada.

Varias ventanas secundarias MDI del mismo tipo de documento comparten recursos de menú. Si varias ventanas secundarias MDI se crean mediante la misma plantilla de documento, puede usar todos el mismo recurso de menú, ahorrando recursos de sistema de Windows.

## <a name="managing-the-status-bar"></a>Administración de la barra de estado

La ventana de marco también coloca la barra de estado dentro de su área de cliente y administra el estado de los indicadores de la barra. Borra de la ventana de marco y actualiza el área de mensajes en la barra de estado según sea necesario y muestra las cadenas de mensajes, como el usuario selecciona los elementos de menú o botones de barra de herramientas, como se describe en [cómo mostrar información de comandos en la barra de estado](../mfc/how-to-display-command-information-in-the-status-bar.md).

## <a name="managing-accelerators"></a>Administración de aceleradores

Cada ventana de marco mantiene una tabla de aceleradores opcional que traducción Acelerador de teclado automáticamente. Este mecanismo facilita definir teclas de aceleración (también denominadas teclas de método abreviado) que invocan comandos de menú.

## <a name="see-also"></a>Vea también

[Uso de ventanas de marco](../mfc/using-frame-windows.md)
