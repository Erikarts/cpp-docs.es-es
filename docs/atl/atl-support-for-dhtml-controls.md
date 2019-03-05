---
title: Compatibilidad de ATL con controles DHTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
- DHTML controls
ms.assetid: 4ba98098-da5d-4362-96ad-8372f816c307
ms.openlocfilehash: dd8ac616d127c3307c1c432c0b3c9bc2ef1d6181
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265267"
---
# <a name="atl-support-for-dhtml-controls"></a>Compatibilidad de ATL con controles DHTML

Uso de ATL, puede crear un control con la funcionalidad de HTML dinámico (DHTML). Un control DHTML ATL:

- Hospeda el control WebBrowser.

- Especifica, mediante HTML, la interfaz de usuario (UI) del control DHTML.

- Tiene acceso al objeto WebBrowser y sus métodos a través de su interfaz, [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\)).

- Administra la comunicación entre el código de C++ y HTML.

Un control DHTML es similar a cualquier otro control ATL, excepto el control DHTML incluye una interfaz de envío adicionales. Consulte la figura en [que identifican los elementos del proyecto de Control DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md) para ver una ilustración de las interfaces proporcionadas en el proyecto DHTML predeterminado.

Puede ver el control DHTML ATL en un explorador Web o en otro contenedor, como ActiveX Control Test Container.

## <a name="in-this-section"></a>En esta sección

[Identificar los elementos del proyecto de control DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md)<br/>
Describe los elementos de un proyecto de control DHTML.

[Llamar al código C++ desde DHTML](../atl/calling-cpp-code-from-dhtml.md)<br/>
Proporciona un ejemplo de llamar a código de C++ desde un control DHTML.

[Crear un control DHTML ATL](../atl/creating-an-atl-dhtml-control.md)<br/>
Se enumeran los pasos para crear un control DHTML.

[Probar el control DHTML ATL](../atl/testing-the-atl-dhtml-control.md)<br/>
Muestra cómo compilar y probar el proyecto de control DHTML inicial.

[Modificar el control DHTML ATL](../atl/modifying-the-atl-dhtml-control.md)<br/>
Muestra cómo agregar alguna funcionalidad al control.

[Probar el Control DHTML ATL modificado](../atl/testing-the-modified-atl-dhtml-control.md)<br/>
Muestra cómo compilar y probar la funcionalidad del control se ha agregado.

## <a name="related-sections"></a>Secciones relacionadas

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Proporciona vínculos a temas sobre cómo programar utilizando Active Template Library.
