---
title: Operaciones de portapapeles en los controles Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- pasting Clipboard data
- CRichEditCtrl class [MFC], paste operation
- cut operation in CRichEditCtrl class [MFC]
- CRichEditCtrl class [MFC], Clipboard operations
- copy operations in rich edit controls
- Clipboard, operations in CRichEditCtrl
- rich edit controls [MFC], Clipboard operations
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
ms.openlocfilehash: 882c589d0d25b54650affa7fd41f916ecf6097d5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276876"
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Operaciones de portapapeles en los controles Rich Edit

La aplicación puede pegar el contenido del Portapapeles en un control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) con el formato del Portapapeles mejor disponible o en un formato específico del Portapapeles. También puede determinar si un control rich edit es capaz de pegar un formato de Portapapeles.

Puede copiar o cortar el contenido de la selección actual utilizando la [copia](../mfc/reference/cricheditctrl-class.md#copy) o [cortar](../mfc/reference/cricheditctrl-class.md#cut) función miembro. De forma similar, puede pegar el contenido del Portapapeles en un control rich edit utilizando la [pegar](../mfc/reference/cricheditctrl-class.md#paste) función miembro. El control pega el primer formato disponible que reconoce, que es probablemente el formato más descriptivo.

Para pegar un formato de Portapapeles específico, puede usar el [PasteSpecial](../mfc/reference/cricheditctrl-class.md#pastespecial) función miembro. Esta función es útil para aplicaciones con un comando Pegado especial que permite al usuario seleccionar el formato del Portapapeles. Puede usar el [CanPaste](../mfc/reference/cricheditctrl-class.md#canpaste) función miembro para determinar si se reconoce un formato especificado por el control.

También puede usar `CanPaste` para determinar si un control rich edit reconoce cualquier formato disponible del Portapapeles. Esta función es útil en el `OnInitMenuPopup` controlador. Una aplicación puede habilitar o atenuar su comando Pegar dependiendo de si el control puede pegar cualquier formato disponible.

Controles Rich Edit. registrar dos formatos de Portapapeles: formato de texto enriquecido y un formato denominado RichEdit texto y objetos. Una aplicación puede registrar estos formatos mediante la [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funcione, especificando el **valores CF_RTF** y **CF_RETEXTOBJ** valores.

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
