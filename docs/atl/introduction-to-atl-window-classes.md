---
title: Introducción a las clases de ventana ATL
ms.date: 11/04/2016
helpviewer_keywords:
- window classes
ms.assetid: 503efc2c-a269-495d-97cf-3fb300d52f3d
ms.openlocfilehash: 0c3bc70b5edfb089a6276003625b876d8c553dcb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301654"
---
# <a name="introduction-to-atl-window-classes"></a>Introducción a las clases de ventana ATL

Las siguientes clases ATL están diseñadas para implementar y manipular las ventanas:

- [CWindow](../atl/reference/cwindow-class.md) le permite adjuntar un identificador de ventana para el `CWindow` objeto. A continuación, llame a `CWindow` métodos para manipular la ventana.

- [CWindowImpl](../atl/reference/cwindowimpl-class.md) le permite implementar una nueva ventana y procesar mensajes con un mapa de mensajes. Puede crear una ventana basada en una clase, una clase existente de la superclase o subclase nueva de Windows de una ventana existente.

- [CDialogImpl](../atl/reference/cdialogimpl-class.md) le permite implementar modal o un cuadro de diálogo no modal y procesar los mensajes con un mapa de mensajes.

- [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) es una clase creada previamente que implementa una ventana cuyo mapa de mensajes está contenido en otra clase. Uso de `CContainedWindowT` permite centralizar el procesamiento de mensajes en una clase.

- [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) le permite implementar un cuadro de diálogo (modal o no modal) que hospeda los controles ActiveX.

- [CSimpleDialog](../atl/reference/csimpledialog-class.md) le permite implementar un cuadro de diálogo modal con funcionalidad básica.

- [CAxWindow](../atl/reference/caxwindow-class.md) le permite implementar una ventana que hospeda un control ActiveX.

- [CAxWindow2T](../atl/reference/caxwindow2t-class.md) le permite implementar una ventana que hospeda un control ActiveX con licencia.

Además de las clases de ventana concreta, ATL proporciona varias clases diseñadas para facilitar la implementación de un objeto de ventana ATL. Son las siguientes:

- [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) administra la información de una nueva clase de ventana.

- [CWinTraits](../atl/reference/cwintraits-class.md) y [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) proporcionan un método sencillo de estandarizar los rasgos de un objeto de ventana ATL.

## <a name="see-also"></a>Vea también

[Clases de ventana](../atl/atl-window-classes.md)
