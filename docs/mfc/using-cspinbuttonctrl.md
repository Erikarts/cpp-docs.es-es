---
title: Usar CSpinButtonCtrl
ms.date: 11/04/2016
f1_keywords:
- CSpinButtonCtrl
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: 6bb663b6ff9b9b039bd774f6e607c7acdb1c4b11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411726"
---
# <a name="using-cspinbuttonctrl"></a>Usar CSpinButtonCtrl

El *botón de número* control (también conocido como un *arriba-abajo* control) proporciona un par de flechas en las que un usuario puede hacer clic para ajustar un valor. Este valor se conoce como el *posición actual*. La posición permanece dentro del intervalo del botón de número. Cuando el usuario hace clic en la flecha hacia arriba, se mueve la posición en el valor máximo; y cuando el usuario hace clic en la flecha hacia abajo, la posición se mueve hacia el mínimo.

El control de botón de número se representa en MFC mediante el [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) clase.

> [!NOTE]
>  De forma predeterminada, el intervalo para el botón de número tiene el máximo establecido en cero (0) y el mínimo establecido en 100. Dado que el valor máximo es menor que el valor mínimo, al hacer clic en la flecha arriba reduce la posición y al hacer clic en la flecha hacia abajo aumenta la lo. Use [CSpinButtonCtrl:: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) para ajustar estos valores.

Normalmente, se muestra la posición actual en un control complementario. El control complementario se conoce como el *ventana relacionada*. Para ver una ilustración de un control de botón de número, vea [acerca de los controles de flechas](/windows/desktop/Controls/up-down-controls) en el SDK de Windows.

Para crear un control de número y una ventana relacionada del control de edición, en Visual Studio, en primer lugar arrastre un control de edición en el cuadro de diálogo o ventana y, a continuación, arrastre un control de número. Seleccione el control de flechas y establezca su **Auto Buddy** y **establecer Buddy Integer** propiedades a **True**. Establezca también la **alineación** propiedad; **Derecha alinear** es más habitual. Con esta configuración, el control de edición se establece como la ventana relacionada porque el control de edición precede directamente en el orden de tabulación. El control de edición muestra números enteros y el control de número se incrusta en el lado derecho del control de edición. Si lo desea, puede establecer el intervalo válido del control de flechas con el [CSpinButtonCtrl:: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) método. No hay controladores de eventos son necesarios para comunicarse entre el control de número y la ventana relacionada porque intercambian datos directamente. Si usa un control de número para otros propósitos, por ejemplo, para desplazarse a través de una secuencia de windows o los cuadros de diálogo, a continuación, agregue un controlador para el mensaje UDN_DELTAPOS y realizar allí la acción personalizada.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Estilos de botón de cuadro de número](../mfc/spin-button-styles.md)

- [Funciones miembro del botón de número](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>Vea también

[Controles](../mfc/controls-mfc.md)
