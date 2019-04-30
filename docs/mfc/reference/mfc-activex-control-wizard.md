---
title: Asistente para controles ActiveX MFC
ms.date: 09/12/2018
f1_keywords:
- vc.appwiz.mfc.ctl.overview
helpviewer_keywords:
- ActiveX controls [MFC], MFC
- MFC ActiveX controls [MFC], wizards
- OLE controls [MFC], creating
- MFC ActiveX Control Wizard
- OLE controls [MFC]
ms.assetid: f19d698c-bdc3-4c74-af97-3d6ccb441b75
ms.openlocfilehash: cec4c3aa6aedfa7a1f8234c6cc2355970d453f56
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412779"
---
# <a name="mfc-activex-control-wizard"></a>Asistente para controles ActiveX MFC

Un control ActiveX es un tipo específico de [servidor de automatización](../../mfc/automation-servers.md); es un componente reutilizable. La aplicación que hospeda el control ActiveX es el [cliente de automatización](../../mfc/automation-clients.md) de ese control. Si su objetivo es crear un componente reutilizable de este tipo, a continuación, use este asistente para crear el control. Consulte [controles ActiveX MFC](../../mfc/mfc-activex-controls.md) para obtener más información.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que sustituyen a ActiveX, vea [controles ActiveX](../activex-controls.md).

Como alternativa, puede crear una automatización MFC aplicación server usando la [MFC Application Wizard](../../mfc/reference/mfc-application-wizard.md).

Un control ActiveX creado con este asistente puede tener una interfaz de usuario, o puede ser invisible. Puede especificar esta opción en el [configuración del Control](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) página del asistente. Un control timer es un ejemplo de un control ActiveX que podría desear ser invisible.

Los controles ActiveX pueden tener una interfaz de usuario complejas. Algunos controles pueden ser similar a los formularios encapsulados: un control único que contiene muchos campos, cada uno de ellos un control de Windows por derecho propio. Por ejemplo, un objeto de partes automática implementado como un control ActiveX de MFC puede presentar una interfaz de usuario de forma similar a través del cual los usuarios podían leer y editar el número de pieza, nombre de una parte y otra información. Consulte [controles ActiveX MFC](../../mfc/mfc-activex-controls.md) para obtener más información.

Si necesita crear un contenedor para sus objetos ActiveX, vea [crear un contenedor de controles ActiveX](../../mfc/reference/creating-an-mfc-activex-control-container.md).

El programa MFC inicial incluye archivos de código fuente (.cpp) de C++, los archivos de recursos (.rc) y un archivo de proyecto (.vcxproj). El código generado en estos archivos iniciales se basa en MFC.

La lista de ejemplo siguiente muestra las tareas y tipos de mejoras para el control ActiveX:

- [Optimizar un Control ActiveX](../../mfc/mfc-activex-controls-optimization.md)

- [Agregar eventos estándar a un Control ActiveX](../../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [Agregar eventos personalizados](../../mfc/mfc-activex-controls-adding-custom-events.md)

- [Agregar métodos estándar](../../mfc/mfc-activex-controls-adding-stock-methods.md)

- [Agregar métodos personalizados](../../mfc/mfc-activex-controls-adding-custom-methods.md)

- [Agregar propiedades estándar](../../mfc/mfc-activex-controls-adding-stock-properties.md)

- [Agregar propiedades personalizadas](../../mfc/mfc-activex-controls-adding-custom-properties.md)

- [Programar controles ActiveX en un contenedor de controles ActiveX](../../mfc/programming-activex-controls-in-a-activex-control-container.md)

## <a name="overview"></a>Información general

Esta página del asistente describe la configuración de aplicación actual para el proyecto de control ActiveX de MFC que está creando. De forma predeterminada, el asistente crea un proyecto de la manera siguiente:

- El proyecto predeterminado genera ningún archivo de licencia o la Ayuda de tiempo de ejecución. Puede cambiar estos valores predeterminados en el [configuración de la aplicación](../../mfc/reference/application-settings-mfc-activex-control-wizard.md) página. Solo las selecciones realizadas en esta página del Asistente de Control ActiveX se reflejan en el **Introducción** página.

- El proyecto incluye una clase de control y una clase de página de propiedades, según el nombre del proyecto. Puede editar los nombres de los nombres de proyecto y archivo en el [nombres de Control](../../mfc/reference/control-names-mfc-activex-control-wizard.md) página.

- El control se basa en ningún control de Windows existente y se activa cuando se vuelve visible, tiene una interfaz de usuario e incluye un **sobre** cuadro de diálogo. Puede cambiar estos valores predeterminados en el [configuración del Control](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) página.

## <a name="see-also"></a>Vea también

[Creación y administración de proyectos de Visual C++](../../build/creating-and-managing-visual-cpp-projects.md)<br/>
[Tipos de proyecto de Visual C++](../../build/reference/visual-cpp-project-types.md)<br/>
[Conceptos](../../atl/active-template-library-atl-concepts.md)
