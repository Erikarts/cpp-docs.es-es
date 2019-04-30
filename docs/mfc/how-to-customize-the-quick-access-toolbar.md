---
title: Procedimiento Personalizar la barra de herramientas de acceso rápido
ms.date: 11/19/2018
helpviewer_keywords:
- quick access toolbar [MFC], customization
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
ms.openlocfilehash: c53e405eafe310c0bfc03a916ab85181ae67a34b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396433"
---
# <a name="how-to-customize-the-quick-access-toolbar"></a>Procedimiento Personalizar la barra de herramientas de acceso rápido

La barra de herramientas de acceso rápido (QAT) es una barra de herramientas personalizable que contiene un conjunto de comandos que se muestran al lado del botón de la aplicación o en las fichas de categoría. La siguiente ilustración muestra una barra de herramientas de acceso rápido típico.

![Barra de herramientas de acceso rápido de cinta de opciones MFC](../mfc/media/quick_access_toolbar.png "barra de herramientas de acceso rápido de cinta de opciones MFC")

Para personalizar la barra de herramientas de acceso rápido, ábralo en el **propiedades** , modifique sus comandos y, a continuación, obtener una vista previa del control de la cinta de opciones.

### <a name="to-open-the-quick-access-toolbar-in-the-properties-window"></a>Para abrir la barra de herramientas de acceso rápido en la ventana Propiedades

1. En Visual Studio, en el **vista** menú, haga clic en **vista de recursos**.

1. En **vista de recursos**, haga doble clic en el recurso de cinta para que se muestre en la superficie de diseño.

1. En la superficie de diseño, haga clic en el menú de la barra de herramientas de acceso rápido y, a continuación, haga clic en **propiedades**.

## <a name="quick-access-toolbar-properties"></a>Propiedades de la barra de herramientas de acceso rápido

En la tabla siguiente define las propiedades de la barra de herramientas de acceso rápido.

|Propiedad|Definición|
|--------------|----------------|
|Posición de QAT|Especifica la posición de la barra de herramientas de acceso rápido al iniciar la aplicación. La posición puede ser **anteriormente** o **debajo** el control de la cinta de opciones.|
|Elementos QAT|Especifica los comandos que están disponibles para la barra de herramientas de acceso rápido.|

#### <a name="to-add-or-remove-commands-on-the-quick-access-toolbar"></a>Para agregar o quitar comandos en la barra de herramientas de acceso rápido

1. En el **propiedades** ventana, haga clic en **QAT Items**y, a continuación, haga clic en el botón de puntos suspensivos **(...)** .

1. En el **Editor de elementos de QAT** cuadro de diálogo, use el **agregar** y **quitar** botones para modificar la lista de comandos en la barra de herramientas de acceso rápido.

1. Si desea que un comando aparezca en la barra de herramientas de acceso rápido y el menú de la barra de herramientas de acceso rápido, active la casilla situada junto al comando. Si desea que el comando aparezca sólo en el menú, desactive la casilla.

## <a name="previewing-the-ribbon"></a>Vista previa de la cinta de opciones

Comandos de barra de herramientas acceso rápidos no aparecen en la superficie de diseño. Para verlos, debe obtener una vista previa de la cinta de opciones o ejecutar la aplicación.

#### <a name="to-preview-the-ribbon-control"></a>Para obtener una vista previa del control de la cinta de opciones

- En el **barra de herramientas del Editor de Ribbon**, haga clic en **Ribbon de prueba**.

## <a name="see-also"></a>Vea también

[Diseñador de la cinta de opciones (MFC)](../mfc/ribbon-designer-mfc.md)
