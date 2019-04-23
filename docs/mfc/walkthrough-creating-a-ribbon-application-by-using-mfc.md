---
title: 'Tutorial: Crear una aplicación de cinta usando MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon application, creating (MFC)
- creating a ribbon aplication (MFC)
ms.assetid: e61393e2-1d6b-4594-a7ce-157d3d1b0d9f
ms.openlocfilehash: 29991a389a09e1fe3dc0074b80fd9a255458f673
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781229"
---
# <a name="walkthrough-creating-a-ribbon-application-by-using-mfc"></a>Tutorial: Crear una aplicación de cinta usando MFC

En este tutorial se muestra cómo usar el **MFC Application Wizard** para crear una aplicación que tiene una cinta de opciones de forma predeterminada. A continuación, puede expandir la cinta de opciones mediante la adición de un **personalizado** categoría de cinta de opciones que tiene un **favoritos** panel y, a continuación, agregar algunos comandos al panel usan con frecuencia la cinta de opciones.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial se da por supuesto que ha configurado Visual Studio para usar **configuración General de desarrollo**. Si usa una configuración diferente, algunos de los elementos de interfaz (IU) del usuario que se hace referencia en las instrucciones siguientes podrían no mostrarse.

### <a name="to-create-an-mfc-application-that-has-a-ribbon"></a>Para crear una aplicación MFC con una cinta de opciones

1. Use la **MFC Application Wizard** para crear una aplicación MFC que tiene una cinta de opciones. Para ejecutar el asistente, en el **archivo** menú, elija **New**y, a continuación, haga clic en **proyecto**.

1. En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C++** nodo bajo **plantillas instaladas**, seleccione **MFC**y, a continuación, seleccione  **Aplicación MFC**. Escriba un nombre para el proyecto, por ejemplo, *MFCRibbonApp*y, a continuación, haga clic en **Aceptar**.

1. Establecer las siguientes opciones el **MFC Application Wizard**:

    1. En el **tipo de aplicación** en sección **estilo Visual y colores**, seleccione **Office 2007 (tema azul)**.

    1. En el **compatibilidad con documentos compuestos** sección, asegúrese de que **ninguno** está seleccionada.

    1. En el **propiedades de la plantilla de documento** sección la **la extensión de archivo** , escriba una extensión de nombre de archivo para los documentos que crea esta aplicación, por ejemplo, *mfcrbnapp*.

    1. En el **soporte técnico de la base de datos** sección, asegúrese de que **ninguno** está seleccionada.

    1. En el **características de la interfaz de usuario** sección, asegúrese de que **usar una cinta de opciones** está seleccionada.

    1. De forma predeterminada, el **MFC Application Wizard** agrega compatibilidad con varios paneles de acoplamiento. Debido a que en este tutorial solo se enseña la cinta, puede quitar estas opciones de la aplicación. En el **características avanzadas** sección, desactive todas las opciones.

1. Haga clic en **finalizar** para crear la aplicación MFC.

1. Para comprobar que la aplicación se creó correctamente, compílela y ejecútela. Para compilar la aplicación, en el **compilar** menú, haga clic en **compilar solución**. Si la aplicación se compila correctamente, puede ejecutarla haciendo **Iniciar depuración** en el **depurar** menú.

    El asistente crea automáticamente una cinta de opciones que tiene una categoría de cinta de opciones que se denomina **inicio**. Esta cinta contiene tres paneles de cinta de opciones, que se denominan **Portapapeles**, **vista**, y **ventana**.

### <a name="to-add-a-category-and-panel-to-the-ribbon"></a>Para agregar una categoría y un panel a la cinta

1. Para abrir el recurso de cinta en el asistente creó el **vista** menú, elija **Other Windows** y, a continuación, haga clic en **vista de recursos**. En **vista de recursos**, haga clic en **cinta** y, a continuación, haga doble clic en **IDR_RIBBON**.

1. En primer lugar, agregue una categoría personalizada a la cinta de opciones haciendo doble clic en **categoría** en el **cuadro de herramientas**.

    Una categoría que tiene el título **Category1** se crea. De forma predeterminada, la categoría contiene un panel.

    Haga clic en **Category1** y, a continuación, haga clic en **propiedades**. En el **propiedades** ventana, cambio **título** a *personalizado*.

    El **Large Images** y **imágenes pequeñas** propiedades especifican los mapas de bits que se utilizan como iconos para los elementos de la cinta de opciones en esta categoría. Dado que la creación de mapas de bits personalizados está fuera del ámbito de este tutorial, simplemente reutilice los mapas de bits creados por el asistente. Los mapas de bits pequeños son de 16 por 16 píxeles. Para imágenes pequeñas, utilice los mapas de bits que se accede mediante el `IDB_FILESMALL` identificador de recurso. Los mapas de bits grandes son de 32 por 32 píxeles. Las imágenes de gran tamaño, utilice los mapas de bits que se accede mediante el `IDB_FILELARGE` identificador de recurso.

    > [!NOTE]
    > En las pantallas HDPI (Gran número de puntos por pulgada), se usan automáticamente las versiones HDPI de las imágenes.

1. A continuación, personalice el panel. Los paneles se usan para agrupar los elementos que se relacionan lógicamente entre sí. Por ejemplo, en el **inicio** ficha de esta aplicación, el **cortar**, **copia**, y **pegar** los comandos se encuentran en el  **Portapapeles** panel. Para personalizar el panel, haga clic en **Panel1** y, a continuación, haga clic en **propiedades**. En el **propiedades** ventana, cambio **título** a *favoritos*.

    Puede especificar el **Image Index** para el panel. Este número especifica el icono que se muestra si el panel de la cinta se agrega a la **la barra de herramientas de acceso rápido**. El icono no se muestra en el panel de la cinta.

1. Para comprobar que la categoría y el panel de la cinta se crearon correctamente, obtenga una vista previa del control de cinta. En el **barra de herramientas del Editor de Ribbon**, haga clic en el **Ribbon de prueba** botón. Un **personalizado** pestaña y **favoritos** panel debe mostrarse en la cinta de opciones.

### <a name="to-add-elements-to-the-ribbon-panels"></a>Para agregar elementos a los paneles de la cinta

1. Para agregar elementos al panel que creó en el procedimiento anterior, arrastre controles desde el **Editor de Ribbon** sección de la **cuadro de herramientas** al panel en la vista de diseño.

1. En primer lugar, agregue un **impresión** botón. El **impresión** botón tendrá un submenú que contiene un **impresión rápida** comando que imprime mediante el uso de la impresora predeterminada. Ambos comandos ya se han definido para esta aplicación. Se encuentran en el menú de la aplicación.

    Para crear el **impresión** botón, arrastre una herramienta de botón al panel.

    En el **propiedades** ventana, cambie el **ID** propiedad **ID_FILE_PRINT**, que ya debe estar definida. Cambio **título** a *impresión*. Cambio **índice de imagen** a *4*.

    Para crear el **impresión rápida** botón, haga clic en la columna de valor de propiedad junto a **elementos de menú**y, a continuación, haga clic en el botón de puntos suspensivos (**...** ). En el **Editor elementos**, haga clic en el sin etiqueta **agregar** botón para crear un elemento de menú. En el **propiedades** ventana, cambio **título** a *impresión rápida*, **ID** a *ID_FILE_PRINT_DIRECT*, y **imagen** a *5*. La propiedad image especifica el **impresión rápida** icono en el `IDB_FILESMALL` recurso de mapa de bits.

1. Para comprobar que los botones se agregaron al panel de la cinta, compile la aplicación y ejecútela. Para compilar la aplicación, en el **compilar** menú, haga clic en **compilar solución**. Si la aplicación se compila correctamente, ejecute la aplicación haciendo **Iniciar depuración** en el **depurar** menú. El **impresión** botón y el cuadro combinado en el **favoritos** panel en el **personalizado** se debe mostrar la pestaña en la cinta de opciones.

## <a name="next-steps"></a>Pasos siguientes

[Cómo: Personalizar la barra de herramientas de acceso rápido](../mfc/how-to-customize-the-quick-access-toolbar.md)

[Cómo: Personalizar el botón aplicación](../mfc/how-to-customize-the-application-button.md)

Para obtener ejemplos de extremo a otro, consulte [ejemplos (MFC Feature Pack)](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Vea también

[Tutoriales](../mfc/walkthroughs-mfc.md)<br/>
[Ejemplos (MFC Feature Pack)](../overview/visual-cpp-samples.md)
