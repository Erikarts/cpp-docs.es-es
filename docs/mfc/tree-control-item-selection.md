---
title: Selección de elementos de control de árbol
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
ms.openlocfilehash: a88a2c8ea5b935bbcb1f40b705337ff676d8b8a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363563"
---
# <a name="tree-control-item-selection"></a>Selección de elementos de control de árbol

Cuando se cambia la selección de un elemento a otro, un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envía [TVN_SELCHANGING](/windows/desktop/Controls/tvn-selchanging) y [TVN_SELCHANGED](/windows/desktop/Controls/tvn-selchanged) mensajes de notificación. Ambas notificaciones incluyen un valor que especifica si el cambio es el resultado de un clic del mouse o una pulsación de tecla. Las notificaciones también incluyen información sobre el elemento que está ganando la selección y el elemento que está perdiendo la selección. Puede usar esta información para establecer los atributos del elemento que dependen del estado de selección del elemento. Devolver **TRUE** en respuesta a `TVN_SELCHANGING` impide que la selección del cambio; devolver **FALSE** permite el cambio.

Una aplicación puede cambiar la selección mediante una llamada a la [SelectItem](../mfc/reference/ctreectrl-class.md#selectitem) función miembro.

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
