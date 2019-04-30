---
title: Usar CHotKeyCtrl
ms.date: 11/04/2016
f1_keywords:
- CHotKeyCtrl
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
ms.openlocfilehash: f52d676f68718cdd4d16cf93bf0d7e3fd6b03822
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349859"
---
# <a name="using-chotkeyctrl"></a>Usar CHotKeyCtrl

Un control hot key, representado por la clase [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md), es una ventana que muestra una representación de texto de la combinación de teclas que el usuario escribe en él, como CTRL + MAYÚS + Q. También mantiene una representación interna de esta clave en forma de un código de tecla virtual y un conjunto de marcas que representan el estado de desplazamiento. El control de tecla de acceso frecuente realmente no establece la tecla de acceso rápido, hacerlo es hasta el programa. (Para obtener una lista de códigos de tecla virtuales estándares, vea Winuser.h.)

Usar un control de tecla de acceso frecuente para obtener la entrada del usuario para qué tecla de acceso rápido asociar a una ventana o un subproceso. Controles de tecla de acceso frecuente usan a menudo en los cuadros de diálogo, como podría mostrar cuando se solicita al usuario para asignar una tecla de acceso rápido. Es responsabilidad de su programa para recuperar los valores que describen la tecla de acceso rápido desde el control de tecla de acceso frecuente y llamar a las funciones adecuadas para asociar la tecla de acceso rápido a una ventana o un subproceso.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Uso de un control de tecla de acceso directo](../mfc/using-a-hot-key-control.md)

- [Establecimiento de una tecla de acceso directo](../mfc/setting-a-hot-key.md)

- [Teclas de acceso directo globales](../mfc/global-hot-keys.md)

- [Teclas de acceso directo específicas del subproceso](../mfc/thread-specific-hot-keys.md)

## <a name="see-also"></a>Vea también

[Controles](../mfc/controls-mfc.md)
