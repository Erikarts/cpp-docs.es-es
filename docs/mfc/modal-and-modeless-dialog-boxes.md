---
title: Cuadros de diálogo modales y no modales
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
ms.openlocfilehash: c3a5263736324d7fe25066e8879d13b3a41768de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62238423"
---
# <a name="modal-and-modeless-dialog-boxes"></a>Cuadros de diálogo modales y no modales

Puede usar la clase [CDialog](../mfc/reference/cdialog-class.md) para administrar dos tipos de cuadros de diálogo:

- *Cuadros de diálogo modales*, que requiere que el usuario responda antes de continuar con el programa

- *Cuadros de diálogo no modal*, que permanecen en la pantalla y están disponibles para su uso en cualquier momento, pero permite que otras actividades de usuario

La edición de recursos y procedimientos para crear una plantilla de cuadro de diálogo son los mismos para los cuadros de diálogo modales y no modales.

Creación de un cuadro de diálogo para que su programa requiere los siguientes pasos:

1. Use la [editor de cuadro de diálogo](../windows/dialog-editor.md) para diseñar el cuadro de diálogo y crear su recurso de plantilla de cuadro de diálogo.

1. Cree una clase de cuadro de diálogo.

1. Conectar el [controles del recurso de cuadro de diálogo para controladores de mensajes](../windows/adding-event-handlers-for-dialog-box-controls.md) en la clase de cuadro de diálogo.

1. Agregar miembros de datos asociadas a los controles del cuadro de diálogo y especifique [intercambio de datos de cuadro de diálogo](../mfc/dialog-data-exchange.md) y [validaciones de datos de cuadro de diálogo](../mfc/dialog-data-validation.md) para los controles.

## <a name="see-also"></a>Vea también

[Cuadros de diálogo](../mfc/dialog-boxes.md)<br/>
[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)
