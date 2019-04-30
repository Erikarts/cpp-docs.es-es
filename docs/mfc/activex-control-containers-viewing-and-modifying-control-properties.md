---
title: 'Contenedores de controles ActiveX: Ver y modificar las propiedades del Control'
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], viewing and modifying
- ActiveX control containers [MFC], viewing and modifying properties
- resource editors, viewing and modifying ActiveX controls
- ActiveX controls [MFC], properties
- controls [MFC], properties
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
ms.openlocfilehash: 0a03acfd880bcf63017eec9796315b98e5d5f4d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394889"
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>Contenedores de controles ActiveX: Ver y modificar las propiedades del Control

Al insertar un control ActiveX en un proyecto, es útil ver y cambiar las propiedades admitidas por el control ActiveX. En este artículo se describe cómo usar el editor de recursos de Visual C++ para hacer esto.

Si la aplicación de contenedor del control ActiveX utiliza controles incrustados, puede ver y modificar las propiedades del control en el editor de recursos. También puede usar el editor de recursos para establecer los valores de propiedad durante el tiempo de diseño. A continuación, el editor de recursos guarda automáticamente estos valores en el archivo de recursos del proyecto. Cualquier instancia del control, a continuación, tendrá que sus propiedades inicializadas con estos valores.

Este procedimiento se supone que ha insertado un control en su proyecto. Para obtener información, consulte [contenedores de controles ActiveX: Insertar un Control en una aplicación de contenedor de controles](../mfc/inserting-a-control-into-a-control-container-application.md).

Es el primer paso para ver las propiedades del control agregar una instancia del control a la plantilla de cuadro de diálogo del proyecto.

### <a name="to-view-the-properties-of-a-control"></a>Para ver las propiedades de un control

1. En la vista de recursos, abra el **diálogo** carpeta.

1. Abra la plantilla de cuadro de diálogo principal.

1. Insertar un control ActiveX mediante el **insertar ActiveX Control** cuadro de diálogo. Para obtener más información, consulte [ver y agregar controles ActiveX a un cuadro de diálogo](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

1. Seleccione el control ActiveX en el cuadro de diálogo.

1. En la ventana Propiedades, haga clic en el **propiedades** botón.

Use la **propiedades** cuadro de diálogo para modificar y probar las nuevas propiedades inmediatamente.

## <a name="see-also"></a>Vea también

[Contenedores de controles ActiveX](../mfc/activex-control-containers.md)
