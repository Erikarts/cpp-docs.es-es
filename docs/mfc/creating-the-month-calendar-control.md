---
title: Crear el control de calendario mensual
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
ms.openlocfilehash: 809bc9fdf6b4477363d0a43d007a2884bb43a049
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258754"
---
# <a name="creating-the-month-calendar-control"></a>Crear el control de calendario mensual

¿Cómo se crea el control de calendario mensual depende de si está utilizando el control en un cuadro de diálogo o crearla en una ventana nondialog.

### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>Usar CMonthCalCtrl directamente en un cuadro de diálogo

1. En el editor de cuadro de diálogo, agregue un Control de calendario mensual al recurso de plantilla de cuadro de diálogo. Especifique su identificador de control.

1. Especifique cualquier estilo necesario, mediante el cuadro de diálogo Propiedades del control de calendario mensual.

1. Use la [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de tipo [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md) con la propiedad del Control. Este miembro puede utilizarse para llamar a `CMonthCalCtrl` funciones miembro.

1. Utilice la ventana Propiedades para asignar funciones de controlador en la clase de cuadro de diálogo para cualquier notificación de control de calendario de mes de los mensajes necesite controlar (consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)).

1. En [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), establecer los estilos adicionales para el `CMonthCalCtrl` objeto.

### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>Usar CMonthCalCtrl en una ventana nondialog

1. Defina el control en la clase de vista o la ventana.

1. El control llama [crear](../mfc/reference/cmonthcalctrl-class.md#create) función miembro, posiblemente en [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), posiblemente tan pronto como la ventana primaria [OnCreate](../mfc/reference/cwnd-class.md#oncreate) función de controlador (si es creación de subclases del control). Establecer los estilos para el control.

## <a name="see-also"></a>Vea también

[Uso de CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
