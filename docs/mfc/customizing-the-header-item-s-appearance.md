---
title: Personalizar el elemento de encabezado&#39;apariencia
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
ms.openlocfilehash: 081260bd5c1cf6335d398a4fd773c9590dbc8030
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241594"
---
# <a name="customizing-the-header-item39s-appearance"></a>Personalizar el elemento de encabezado&#39;apariencia

Estableciendo el *dwStyle* parámetro al crear un control de encabezado ([CHeaderCtrl:: Create](../mfc/reference/cheaderctrl-class.md#create)), puede definir la apariencia y comportamiento del encabezado de los elementos o del encabezado del propio control.

Este es un muestreo de los estilos que se puede establecer y su finalidad:

- Para convertir un elemento de encabezado de aspecto de un botón de comando, use el **HDS_BUTTONS** estilo.

   Utilice este estilo si desea llevar a cabo acciones en respuesta a los clics del mouse en un elemento de encabezado, como ordenar datos en una columna en particular, como se hace en Microsoft Outlook.

- Para dar una apariencia "seguimiento activo" a los elementos de encabezado cuando el cursor del mouse pasa sobre ellas, utilice el **HDS_HOTTRACK** estilo.

   Seguimiento activo muestra un contorno 3D como pasar el puntero sobre un elemento en un plano en caso contrario, barra.

- Para indicar que se debe ocultar el control de encabezado, utilice la **HDS_HIDDEN** estilo.

   El **HDS_HIDDEN** estilo indica que el control de encabezado está diseñado para usarse como un contenedor de datos y no es un control visual. Este estilo no oculta automáticamente el control, pero, en su lugar, afecta al comportamiento de `CHeaderCtrl::Layout`. El valor devuelto en el *cy* miembro de la `WINDOWPOS` estructura será cero que indica que el control no debería estar visible para el usuario.

Para obtener más información acerca de estas propiedades, vea [elementos](/windows/desktop/Controls/header-controls) en el SDK de Windows. Para obtener información sobre cómo agregar elementos a un control de encabezado, vea [agregar elementos al Control de encabezado](../mfc/adding-items-to-the-header-control.md).

## <a name="see-also"></a>Vea también

[Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
