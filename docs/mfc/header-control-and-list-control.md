---
title: Control de encabezado y control de lista
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
ms.openlocfilehash: 934b54de3266138225087d5519af2be51972cf9d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266775"
---
# <a name="header-control-and-list-control"></a>Control de encabezado y control de lista

En la mayoría de los casos, usará el control de encabezado que está incrustado en un [CListCtrl](../mfc/reference/clistctrl-class.md) o [CListView](../mfc/reference/clistview-class.md) objeto. Sin embargo, hay casos donde es deseable, como la manipulación de datos, organizados en columnas o filas, en un objeto de control de encabezado independiente una [CView](../mfc/reference/cview-class.md)-objeto derivado. En estos casos, necesita mayor control sobre la apariencia y comportamiento predeterminado de un control de encabezado incrustado.

En el caso habitual que desea que un control de encabezado para ofrecer estándar, comportamiento predeterminado, es posible que desee usar [CListCtrl](../mfc/reference/clistctrl-class.md) o [CListView](../mfc/reference/clistview-class.md) en su lugar. Use `CListCtrl` cuando desee que la funcionalidad de un control de encabezado predeterminado, incrustado en un control común de vista de lista. Use [CListView](../mfc/reference/clistview-class.md) cuando desee que la funcionalidad de un control de encabezado predeterminado, incrustado en un objeto de vista.

> [!NOTE]
>  Estos controles sólo incluyen un control de encabezado integrado si el control de vista de lista se crea utilizando el **LVS_REPORT** estilo.

En la mayoría de los casos, se puede modificar la apariencia del control de encabezado incrustado cambiando los estilos del control de vista de lista que contiene. Además, se puede obtener información sobre el control de encabezado a través de funciones miembro del control de vista de lista primario. Sin embargo, para un control total y acceso a los atributos y estilos de control de encabezado incrustado, se recomienda que se ha obtenido un puntero al objeto de control de encabezado.

El objeto de control de encabezado incrustado se puede acceder desde cualquiera `CListCtrl` o `CListView` con una llamada a la clase respectiva `GetHeaderCtrl` función miembro. El siguiente código muestra esto:

[!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Usar listas de imágenes con controles de encabezado](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Vea también

[Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
