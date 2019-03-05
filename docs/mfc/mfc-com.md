---
title: MFC COM
ms.date: 09/12/2018
f1_keywords:
- MFC COM (MFC)
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
ms.openlocfilehash: 67c7ea3e93b3158abc552c552c450c31c109be80
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257831"
---
# <a name="mfc-com"></a>MFC COM

Un subconjunto de MFC está diseñado para ofrecer compatibilidad con COM, aunque la mayoría de Active Template Library (ATL) está diseñado para la programación COM. Temas de esta sección describe la compatibilidad con de MFC COM.

Tecnologías activas (como ActiveX controles, contención de documentos activos, OLE y así sucesivamente) usan el modelo de objetos componentes (COM) para habilitar los componentes de software interactuar entre sí en un entorno de red, independientemente del lenguaje con el que fueran creado. Tecnologías activas pueden utilizarse para crear aplicaciones que se ejecutan en el escritorio o en Internet. Para obtener más información, consulte [Introducción a COM](../atl/introduction-to-com.md) o [el modelo de objetos componentes](/windows/desktop/com/the-component-object-model).

Tecnologías activas incluyen tecnologías de cliente y servidor, incluido lo siguiente:

- Controles ActiveX son objetos interactivos que se pueden utilizar en contenedores como un sitio Web. Para obtener más información sobre los controles ActiveX, vea:

   - [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

   - [Controles ActiveX en Internet](../mfc/activex-controls-on-the-internet.md)

   - [Información general: Internet](../mfc/mfc-internet-programming-basics.md)

   - [Actualizar un ActiveX Control existente que se usará en Internet](../mfc/upgrading-an-existing-activex-control.md)

   - [Depurar un Control ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

- Active scripting controla el comportamiento integrado de uno o varios controles ActiveX desde un explorador o el servidor. Para obtener más información sobre secuencias de comandos ActiveX, vea [tecnología activa en Internet](../mfc/active-technology-on-the-internet.md).

- [Automatización](../mfc/automation.md) (anteriormente conocida como automatización OLE) permite que una aplicación manipule objetos implementados en otra aplicación o "exponer" objetos de forma que se puedan manipular.

   El objeto automatizado puede ser local o remoto (en otra máquina accesible a través de una red). La automatización está disponible para objetos COM y OLE.

- En esta sección también proporciona información sobre cómo escribir componentes COM mediante MFC, por ejemplo, en [puntos de conexión](../mfc/connection-points.md).

Para obtener una explicación de lo que todavía se denomina OLE en comparación con lo que ahora se denomina tecnología activa, vea los temas sobre [OLE](../mfc/ole-in-mfc.md).

## <a name="in-this-section"></a>En esta sección

[Contención de documentos activos](../mfc/active-document-containment.md)

[Automatización](../mfc/automation.md)

[Puntos de conexión](../mfc/connection-points.md)

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>Vea también

[Conceptos](../mfc/mfc-concepts.md)
