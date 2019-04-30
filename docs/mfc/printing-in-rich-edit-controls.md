---
title: Imprimir controles Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
ms.openlocfilehash: 2ddc52e43da2e409117ccc5169442002ac27a315
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62238400"
---
# <a name="printing-in-rich-edit-controls"></a>Imprimir controles Rich Edit

Puede indicar a un control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) para representar la salida para un dispositivo específico, como una impresora. También puede especificar el dispositivo de salida para el que un control rich edit da formato a su texto.

Para dar formato a parte del contenido de un control rich edit para un dispositivo específico, puede usar el [FormatRange](../mfc/reference/cricheditctrl-class.md#formatrange) función miembro. El [FORMATRANGE](/windows/desktop/api/richedit/ns-richedit-_formatrange) estructura utilizada con esta función especifica el intervalo de texto para dar formato, así como el contexto de dispositivo (DC) para el dispositivo de destino.

Después de dar formato al texto para un dispositivo de salida, puede enviar la salida al dispositivo mediante el [DisplayBand](../mfc/reference/cricheditctrl-class.md#displayband) función miembro. Si utiliza varias veces `FormatRange` y `DisplayBand`, puede implementar una aplicación que imprime el contenido de un control rich edit las bandas. (Las bandas es la división de los resultados en partes más pequeñas para fines de impresión.)

Puede usar el [función miembro SetTargetDevice](../mfc/reference/cricheditctrl-class.md#settargetdevice) da formato a la función miembro para especificar el dispositivo de destino para el que un control rich edit su texto. Esta función es útil para WYSIWYG (lo que ve es lo que obtendrá) de formato, en el que una aplicación coloca texto usando métricas de fuente de la impresora predeterminada en lugar de la pantalla.

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
