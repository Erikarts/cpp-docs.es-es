---
title: Clases de ventana de marco
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], about frame window classes
- frame window classes [MFC]
- windows [MFC], MDI
- document frame windows [MFC], classes
- single document interface (SDI), frame windows
- window classes [MFC], frame
- MFC, frame windows
- MDI [MFC], frame windows
- classes [MFC], window
ms.assetid: c27e43a7-8ad0-4759-b1b7-43f4725f4132
ms.openlocfilehash: d42fa475fca7c92e4ba46b164a9beda9869231c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219787"
---
# <a name="frame-window-classes"></a>Clases de ventana de marco

Cada aplicación tiene una "ventana de marco principal", una ventana del escritorio que normalmente tiene el nombre de la aplicación en su título. Normalmente, cada documento tiene una "ventana de marco de documento". Una ventana de marco de documento contiene al menos una vista, que presenta los datos del documento.

## <a name="frame-windows-in-sdi-and-mdi-applications"></a>Marco Windows en aplicaciones SDI y MDI

Para una aplicación SDI, hay una ventana de marco que se deriva la clase [CFrameWnd](../mfc/reference/cframewnd-class.md). Esta ventana es la ventana de marco principal y la ventana de marco de documento. Para una aplicación MDI, la ventana de marco principal se deriva de clase [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), y las ventanas de marco de documento, que son ventanas secundarias MDI, se derivan de una clase [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).

## <a name="use-the-frame-window-class-or-derive-from-it"></a>Utilice la clase de ventana de marco o derivar de ella

Estas clases proporcionan la mayor parte de la funcionalidad de la ventana de marco que necesita para sus aplicaciones. En circunstancias normales, el comportamiento predeterminado y la apariencia que proporcionan se adapte a sus necesidades. Si necesita una funcionalidad adicional, que se derivan de estas clases.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Clases de ventana de marco creadas por el Asistente para aplicaciones](../mfc/frame-window-classes-created-by-the-application-wizard.md)

- [Estilos de ventana de marco](../mfc/frame-window-styles-cpp.md)

- [Cambiar los estilos de una ventana creada por MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>Vea también

[Ventanas de marco](../mfc/frame-windows.md)
