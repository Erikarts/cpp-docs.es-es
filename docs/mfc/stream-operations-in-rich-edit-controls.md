---
title: Operaciones de secuencia en los controles Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], stream operations
- CRichEditCtrl class [MFC], stream storage
- rich edit controls [MFC], stream operations
- storage, stream in CRichEditCtrl
- stream operations in CRichEditCtrl
- stream storage and CRichEditCtrl
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
ms.openlocfilehash: 04cf0b06773937bf66defccbb0e5e880c06e8d88
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267984"
---
# <a name="stream-operations-in-rich-edit-controls"></a>Operaciones de secuencia en los controles Rich Edit

Puede utilizar secuencias para transferir datos dentro o fuera de un control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Un flujo se define mediante una [estructura EDITSTREAM](/windows/desktop/api/richedit/ns-richedit-_editstream) estructura, que especifica un búfer y una función de devolución de llamada definido por la aplicación.

Para leer datos en un amplio control de edición (es decir, los datos de secuencia), utilice el [función miembro StreamIn](../mfc/reference/cricheditctrl-class.md#streamin) función miembro. El control llama repetidamente a la función de devolución de llamada definido por la aplicación, que transfiere una parte de los datos en el búfer cada vez.

Para guardar el contenido de un amplio control de edición (es decir, transmitir los datos de salida), puede usar el [función miembro StreamOut](../mfc/reference/cricheditctrl-class.md#streamout) función miembro. El control escribe varias veces en el búfer y, a continuación, llama a la función de devolución de llamada definido por la aplicación. Para cada llamada, la función de devolución de llamada guarda el contenido del búfer.

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
