---
title: Clases de ventana derivadas
ms.date: 11/04/2016
helpviewer_keywords:
- window class hierarchy
- hierarchies, window classes
- classes [MFC], derived
- CWnd class [MFC], classes derived from
- derived classes [MFC], window classes
- window classes [MFC], derived
ms.assetid: 6f7e437e-fbde-4a06-bfab-72d9dbf05292
ms.openlocfilehash: e86ca139b8470dce614564f0c0134a611adeda2c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153383"
---
# <a name="derived-window-classes"></a>Clases de ventana derivadas

Puede crear ventanas directamente desde [CWnd](../mfc/reference/cwnd-class.md), o derivar nuevas clases de ventana de `CWnd`. De esta forma crearía normalmente sus propias ventanas personalizadas. Sin embargo, para crear la mayoría de las ventanas de un programa marco se utilizan en su lugar las clases de ventana marco derivadas de `CWnd`, proporcionadas por MFC.

## <a name="frame-window-classes"></a>Clases de ventana marco

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
Se utiliza para las ventanas marco SDI que enmarcan un documento único y su vista. La ventana marco es a la vez la ventana marco principal de la aplicación y la ventana marco del documento actual.

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
Se utiliza como ventana marco principal para las aplicaciones MDI. La ventana marco principal es un contenedor para todas las ventanas de documento MDI y comparte la barra de menús con ellas. Una ventana marco MDI es una ventana de nivel superior que aparece en el escritorio.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
Se utiliza para los documentos individuales abiertos en una ventana marco principal MDI. Una ventana marco secundaria MDI contenida en la ventana marco principal MDI enmarca cada uno de los documentos y sus vistas. Una ventana secundaria MDI tiene una apariencia muy similar a la de una ventana marco típica, pero se incluye dentro de una ventana marco MDI en lugar de ubicarse en el escritorio. Sin embargo, la ventana secundaria MDI no tiene su propia barra de menús y debe compartir la de la ventana marco MDI que la contiene.

Para obtener más información, consulte [marco Windows](../mfc/frame-windows.md).

## <a name="other-window-classes-derived-from-cwnd"></a>Otras clases de ventana derivadas de CWnd

Además de las ventanas marco, se derivan de `CWnd` otras categorías principales de ventanas:

*Vistas*<br/>
Las vistas se crean mediante el `CWnd`-clase derivada [CView](../mfc/reference/cview-class.md) (o uno de sus clases derivadas). Una vista se adjunta a un documento y actúa como intermediario entre el documento y el usuario. Una vista es una ventana secundaria (no un elemento secundario MDI) que rellena normalmente el área cliente de una ventana marco SDI o de una ventana marco secundaria MDI (o la parte del área cliente no cubierta por una barra de herramientas o una barra de estado).

*Cuadros de diálogo*<br/>
Cuadros de diálogo se crean mediante el `CWnd`-clase derivada [CDialog](../mfc/reference/cdialog-class.md).

*Formularios*<br/>
Vistas de formulario basadas en recursos de plantilla de cuadro de diálogo, como cuadros de diálogo, se crean mediante clases [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md), o [CDaoRecordView](../mfc/reference/cdaorecordview-class.md).

*Controles*<br/>
Los controles como botones, cuadros de lista y cuadros combinados se crean con otras clases derivadas de `CWnd`. Consulte [controlar temas](../mfc/controls-mfc.md).

*Barras de control*<br/>
Ventanas secundarias que contienen controles. Entre los ejemplos se incluyen las barras de herramientas y las barras de estado. Consulte [barras de Control](../mfc/control-bars.md).

## <a name="window-class-hierarchy"></a>Jerarquía de clases de ventana

Hacer referencia a la [gráfico de jerarquías MFC](../mfc/hierarchy-chart.md) en el *referencia de MFC*. Las vistas se explican en [arquitectura documento/vista](../mfc/document-view-architecture.md). Cuadros de diálogo se explican en [cuadros de diálogo](../mfc/dialog-boxes.md).

## <a name="creating-your-own-special-purpose-window-classes"></a>Crear sus propios tipos de ventana para un propósito especial

Además de las clases de ventana proporcionadas por la biblioteca de clases, puede necesitar ventanas secundarias con un propósito especial. Para crear una de estas ventanas, crear su propio [CWnd](../mfc/reference/cwnd-class.md)-clase derivada y conviértalo en una ventana secundaria de un marco o vista. Tenga en cuenta que el marco administra la extensión del área cliente de una ventana marco de documento. La mayor parte del área cliente se administra mediante una vista, pero otras ventanas, por ejemplo, las barras de control o sus propias ventanas personalizadas, pueden compartir el espacio con la vista. Es posible que deba interactuar con los mecanismos de las clases [CView](../mfc/reference/cview-class.md) y [CControlBar](../mfc/reference/ccontrolbar-class.md) para colocar las ventanas secundarias en el área de cliente de una ventana de marco.

[Crear Windows](../mfc/creating-windows.md) describe la creación de objetos de ventana y las ventanas que administran.

## <a name="see-also"></a>Vea también

[Objetos de ventana](../mfc/window-objects.md)
