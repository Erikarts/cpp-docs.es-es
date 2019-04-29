---
title: Control de lista y vista de lista
ms.date: 11/04/2016
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
ms.openlocfilehash: 5c9612a22eab27d568c0dbb86d29ba031fe5985e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365338"
---
# <a name="list-control-and-list-view"></a>Control de lista y vista de lista

Para mayor comodidad, MFC encapsula el control de lista de dos maneras. Puede usar los controles de lista:

- Directamente, insertando un [CListCtrl](../mfc/reference/clistctrl-class.md) objeto en una clase de cuadro de diálogo.

- Indirectamente, mediante el uso de la clase [CListView](../mfc/reference/clistview-class.md).

`CListView` facilita la integración de un control de lista con la arquitectura documento/vista MFC, que encapsula el control como [CEditView](../mfc/reference/ceditview-class.md) encapsula un control de edición: el control rellena toda el área expuesta de una vista MFC. (La vista *es* el control, se convierte en `CListView`.)

Un `CListView` objeto hereda de [CCtrlView](../mfc/reference/cctrlview-class.md) y su base de clases y agrega una función miembro para recuperar el control de lista subyacente. Usar miembros de la vista para trabajar con la vista como una vista. Use la [GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl) función miembro para tener acceso a funciones miembro del control de lista. Utilice a estos miembros para:

- Agregar, eliminar o manipular "elementos" en la lista.

- Establecer u obtener atributos de control de lista.

Para obtener una referencia a la `CListCtrl` subyacente un `CListView`, llame a `GetListCtrl` desde la clase de vista de lista:

[!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]

En este tema se describe dos formas de usar el control de lista.

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
