---
title: Llamar a código de C++ desde DHTML
ms.date: 11/04/2016
helpviewer_keywords:
- DHTML, calling C++ code from
ms.assetid: 37329acd-4c22-40ca-a85a-b7480748f75f
ms.openlocfilehash: fb63f8671770f57972a4c789d983bdf9658d5ecb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62251740"
---
# <a name="calling-c-code-from-dhtml"></a>Llamar a código de C++ desde DHTML

Un control DHTML puede hospedarse en un contenedor, como Test Container o Internet Explorer. Consulte [Probar propiedades y eventos con un contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información sobre cómo obtener acceso a Test Container.

El contenedor que hospeda el control se comunica con el control mediante las interfaces de control normal. DHTML utiliza la interfaz de envío que termina con "Interfaz de usuario" para comunicarse con el código de C++ y el recurso HTML. En [modificar el Control DHTML ATL](../atl/modifying-the-atl-dhtml-control.md), puede poner en práctica los métodos para llamar a estas interfaces diferentes.

Para ver un ejemplo de llamar a código de C++ desde DHTML, [crear un control DHTML](../atl/creating-an-atl-dhtml-control.md) mediante el Asistente para controles ATL y examine el código en el archivo de encabezado y en el archivo HTML.

## <a name="declaring-webbrowser-methods-in-the-header-file"></a>Declarar métodos de WebBrowser en el archivo de encabezado

Para invocar los métodos de C++ desde la UI DHTML, debe agregar métodos a la interfaz de la interfaz de usuario del control. Por ejemplo, el archivo de encabezado creado por el Asistente para controles ATL contiene el método de C++ `OnClick`, que es un miembro de la interfaz de la interfaz de usuario del control generado por el asistente.

Examinar `OnClick` en el archivo .h del control:

[!code-cpp[NVC_ATL_COM#4](../atl/codesnippet/cpp/calling-cpp-code-from-dhtml_1.h)]

El primer parámetro, *pdispBody*, es un puntero a la interfaz de envío del objeto de cuerpo. El segundo parámetro, *varColor*, identifica el color que se aplica al control.

## <a name="calling-c-code-in-the-html-file"></a>Llamar a código de C++ en el archivo HTML

Una vez que haya declarado los métodos de WebBrowser en el archivo de encabezado, puede invocar los métodos desde el archivo HTML. Observe que en el archivo HTML que el Asistente para controles ATL inserta tres métodos de envío de Windows: tres `OnClick` métodos que envían mensajes a cambiar el color de fondo del control.

Examinar uno de los métodos en el archivo HTML:

`<BUTTON onclick='window.external.OnClick(theBody, "red");'>Red</BUTTON>`

En el código HTML anterior, el método externo de ventana, `OnClick`, se llama como parte de la etiqueta del botón. El método tiene dos parámetros: `theBody`, que hace referencia al cuerpo del documento HTML, y `"red"`, lo que indica que color de fondo del control se cambiará a rojo cuando se hace clic en el botón. El `Red` después de la etiqueta es la etiqueta del botón.

Consulte [modificar el Control DHTML ATL](../atl/modifying-the-atl-dhtml-control.md) para obtener más información acerca de cómo proporcionar sus propios métodos. Consulte [que identifican los elementos del proyecto de Control DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md) para obtener más información sobre el archivo HTML.

## <a name="see-also"></a>Vea también

[Compatibilidad con controles DHTML](../atl/atl-support-for-dhtml-controls.md)
