---
title: Agregar elementos al control
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
ms.openlocfilehash: 88e008f06fb669db1c13872b1a58555eeb357d86
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394785"
---
# <a name="adding-items-to-the-control"></a>Agregar elementos al control

Para agregar elementos al control de lista ([CListCtrl](../mfc/reference/clistctrl-class.md)), llame a uno de varias versiones de la [InsertItem](../mfc/reference/clistctrl-class.md#insertitem) función miembro, dependiendo de qué información tiene. Una versión toma un [LV_ITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) estructura que prepare. Dado que el `LV_ITEM` estructura contiene muchos miembros, tener mayor control sobre los atributos del elemento de control de lista.

Dos miembros importantes (con respecto a la vista de informe) de la `LV_ITEM` estructura son el `iItem` y `iSubItem` miembros. El `iItem` miembro es el índice de base cero del elemento que se hace referencia la estructura y el `iSubItem` miembro es el índice basado en uno de un subelemento, o cero si la estructura contiene información sobre un elemento. Con estos dos miembros se determina, por elemento, el tipo y valor de la información del subelemento que se muestra cuando el control de lista está en vista de informe. Para obtener más información, consulte [CListCtrl:: SetItem](../mfc/reference/clistctrl-class.md#setitem).

Miembros adicionales especifican texto, icono, estado y datos de elemento del elemento. "Los datos del elemento" es un valor definido por la aplicación asociado con un elemento de vista de lista. Para obtener más información sobre la `LV_ITEM` estructura, vea [CListCtrl:: GetItem](../mfc/reference/clistctrl-class.md#getitem).

Otras versiones de `InsertItem` tardar uno o varios valores independientes, correspondientes a los miembros de la `LV_ITEM` estructura, lo que permite inicializar solo aquellos miembros que desea admitir. Por lo general, el control de lista administra el almacenamiento para los elementos de lista, pero se pueden almacenar parte de la información en la aplicación en su lugar, mediante "elementos de devolución de llamada". Para obtener más información, consulte [elementos de devolución de llamada y máscara de devolución de llamada](../mfc/callback-items-and-the-callback-mask.md) en este tema y [elementos de devolución de llamada y máscara de devolución de llamada](/windows/desktop/Controls/using-list-view-controls) en el SDK de Windows.

Para obtener más información, consulte [agregar vista de lista de elementos y subelementos](/windows/desktop/Controls/using-list-view-controls).

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
