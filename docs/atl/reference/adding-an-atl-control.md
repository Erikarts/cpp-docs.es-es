---
title: Agregar un Control ATL
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
ms.assetid: 10223e7e-fdb7-4163-80c6-44aeafa8e6ce
ms.openlocfilehash: 836b19cef38549bcdf6cddeeda5bbb7fee08a1c1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298443"
---
# <a name="adding-an-atl-control"></a>Agregar un Control ATL

Use este asistente para agregar un objeto de interfaz de usuario a un proyecto que admita las interfaces para todos los contenedores potenciales. Para admitir estas interfaces, el proyecto debe se ha creado como una aplicación ATL o como una aplicación MFC con compatibilidad con ATL. Puede usar el [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md) para crear una aplicación ATL, o bien [agregar un objeto ATL a una aplicación MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad con ATL para una aplicación MFC.

## <a name="to-add-an-atl-control-to-your-project"></a>Para agregar un control ATL al proyecto

1. En el **el Explorador de soluciones** o [vista de clases](/visualstudio/ide/viewing-the-structure-of-code), haga clic en el nombre del proyecto al que desea agregar el objeto simple ATL.

1. Haga clic en **agregar** desde el menú contextual y, a continuación, haga clic en **Agregar clase**.

1. En el [Agregar clase](../../ide/add-class-dialog-box.md) cuadro de diálogo, en el panel Plantillas, haga clic en **Control ATL**y, a continuación, haga clic en **agregar** para mostrar el [Asistente para controles ATL](../../atl/reference/atl-control-wizard.md).

Mediante el **Asistente para controles ATL**, puede crear uno de los tres tipos de controles:

- Un control estándar

- Un control compuesto

- Un control DHTML

Además, puede reducir el tamaño del control y quitar las interfaces que no se usan por la mayoría de los contenedores seleccionando **control mínimo** en el **opciones** página del asistente.

## <a name="see-also"></a>Vea también

[Agregar funciones al control compuesto](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)
