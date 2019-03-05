---
title: Elementos de devolución de llamada y máscara de devolución de llamada
ms.date: 11/04/2016
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
ms.openlocfilehash: 35967f128c6cc59bc9cea90da559b32c51fb38d1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261081"
---
# <a name="callback-items-and-the-callback-mask"></a>Elementos de devolución de llamada y máscara de devolución de llamada

Para cada uno de sus elementos, un control de vista de lista normalmente almacena el texto de etiqueta, el índice de la lista de imágenes de iconos del elemento, y un conjunto de bits marcas de estado del elemento. Puede definir elementos individuales como elementos de devolución de llamada, que son útiles si la aplicación ya almacena parte de la información de un elemento.

Define un elemento como un elemento de devolución de llamada mediante la especificación de los valores adecuados para el `pszText` y `iImage` los miembros de la **LV_ITEM** estructura (consulte [CListCtrl:: GetItem](../mfc/reference/clistctrl-class.md#getitem)). Si la aplicación mantiene el texto del elemento o del subelemento, especifique el **LPSTR_TEXTCALLBACK** valor para el `pszText` miembro. Si la aplicación realiza un seguimiento del icono del elemento, especifique el **I_IMAGECALLBACK** valor para el `iImage` miembro.

Además de definir elementos de devolución de llamada, también puede modificar la máscara de devolución de llamada del control. Esta máscara es un conjunto de marcas de bits que especifican los Estados de elemento para el que la aplicación, en lugar de control, almacena los datos actuales. La máscara de devolución de llamada se aplica a todos los elementos del control, a diferencia de la designación de elemento de devolución de llamada, que se aplica a un elemento específico. La máscara de devolución de llamada es cero de forma predeterminada, lo que significa que el control realiza el seguimiento de todos los Estados del elemento. Para cambiar este comportamiento predeterminado, inicialice la máscara para cualquier combinación de los siguientes valores:

- **LVIS_CUT** el elemento está marcado para una operación de cortar y pegar.

- **LVIS_DROPHILITED** el elemento está resaltado como destino de arrastrar y colocar.

- **LVIS_FOCUSED** el elemento tiene el foco.

- **LVIS_SELECTED** el elemento está seleccionado.

- **LVIS_OVERLAYMASK** la aplicación almacena el índice de la imagen de superposición actual para cada elemento de lista de imágenes.

- **LVIS_OVERLAYMASK** la aplicación almacena el índice de la imagen del estado actual para cada elemento de lista de imágenes.

Para obtener más información sobre la recuperación y la configuración de esta máscara, consulte [CListCtrl:: GetCallbackMask](../mfc/reference/clistctrl-class.md#getcallbackmask) y [CListCtrl:: SetCallbackMask](../mfc/reference/clistctrl-class.md#setcallbackmask).

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
