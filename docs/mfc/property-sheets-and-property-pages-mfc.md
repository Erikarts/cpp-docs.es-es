---
title: Hojas de propiedades y páginas de propiedades (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], tabs
- property pages [MFC], property sheets
- CPropertyPage class [MFC], property sheets and pages
- CPropertySheet class [MFC], property sheets and pages
- property sheets, propert pages
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
ms.openlocfilehash: 971b8cde1560e54f87269e8b85a41cdec55c091d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445401"
---
# <a name="property-sheets-and-property-pages-mfc"></a>Hojas de propiedades y páginas de propiedades (MFC)

MFC [cuadro de diálogo](../mfc/dialog-boxes.md) puede tener un aspecto "pestaña cuadro de diálogo" mediante la incorporación de hojas de propiedades y páginas de propiedades. Llama a una "hoja de propiedades" en MFC, parece que este tipo de cuadro de diálogo, similar a muchos cuadros de diálogo en Microsoft Word, Excel y Visual C++, contiene una pila de hojas con pestañas, muy similar a una pila de carpetas vistas de delante hacia atrás, o un grupo de ventanas en cascada. Controles de la primera ficha están visibles; solo en la ficha con la etiqueta está visible en las pestañas posteriores. Hojas de propiedades son especialmente útiles para administrar un gran número de propiedades o configuraciones que se pueden dividir en varios grupos. Normalmente, una hoja de propiedades puede simplificar una interfaz de usuario mediante la sustitución de varios cuadros de diálogo independiente.

A partir de la versión 4.0 de MFC, las hojas de propiedades y páginas de propiedades se implementan mediante los controles comunes que vienen con Windows 95 y Windows NT versión 3.51 y versiones posterior.

Hojas de propiedades se implementan con clases [CPropertySheet](../mfc/reference/cpropertysheet-class.md) y [CPropertyPage](../mfc/reference/cpropertypage-class.md) (se describe en el *referencia de MFC*). `CPropertySheet` define el cuadro de diálogo general que puede contener varias "páginas" según `CPropertyPage`.

Para obtener información sobre cómo crear y trabajar con hojas de propiedades, vea el tema [hojas de propiedades](../mfc/property-sheets-mfc.md).

## <a name="see-also"></a>Vea también

[Cuadros de diálogo](../mfc/dialog-boxes.md)<br/>
[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Hojas de propiedades y páginas de propiedades en MFC](../mfc/property-sheets-and-property-pages-in-mfc.md)<br/>
[Intercambio de datos](../mfc/exchanging-data.md)<br/>
[Creación de una hoja de propiedades no modal](../mfc/creating-a-modeless-property-sheet.md)<br/>
[Control del botón Aplicar](../mfc/handling-the-apply-button.md)

