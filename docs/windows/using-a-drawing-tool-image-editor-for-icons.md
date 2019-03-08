---
title: Filtrar Usar una herramienta de dibujo
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.drawing
helpviewer_keywords:
- Image editor [C++], selecting drawing tools
- Image editor [C++], toolbar
- drawing tools
- Image editor [C++], drawing lines
- shapes, drawing
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
ms.openlocfilehash: bde951a2915bf980e09d94c16edc1a9b462c662e
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/07/2019
ms.locfileid: "57563334"
---
# <a name="how-to-use-a-drawing-tool"></a>Filtrar Usar una herramienta de dibujo

El **Editor de imágenes** tiene a mano alzada herramientas de dibujo y borradas que todo funcione de la misma manera. Seleccione la herramienta y, si es necesario, [seleccionar los colores de primer plano y fondo](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) y opciones de tamaño y forma. A continuación, mueva el puntero a la imagen y haga clic o arrastre para dibujar y borrar.

## <a name="drawing-tools"></a>Herramientas de dibujo

Puede seleccionar las herramientas de dibujo desde el **Editor de imágenes** barra de herramientas o el **imagen** menú. Cuando se selecciona el **borrador** herramienta, **pincel** herramienta, o **aerógrafo** herramienta, el selector de opciones muestra las opciones de la herramienta.

> [!TIP]
>  Información sobre herramientas aparece cuando desplace el cursor sobre los botones en la [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md). Estas sugerencias le ayudarán a identificar los botones que se mencionan aquí.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>Para seleccionar y usar una herramienta de dibujo de la barra de herramientas del Editor de imágenes

1. Seleccione un botón en el **Editor de imágenes** barra de herramientas.

   - El **borrador** herramienta pinta la imagen con el color de fondo actual cuando se presiona el botón primario del mouse.

      > [!TIP]
      > En lugar de usar el **borrador** herramienta, le resultará más cómodo dibujar en el color de fondo con una de las herramientas de dibujo.

   - El **lápiz** herramienta dibuja a mano alzada con un ancho constante de un píxel.

   - El **pincel** herramienta tiene varias formas y tamaños.

   - El **aerógrafo** herramienta distribuye aleatoriamente los píxeles de color en torno al centro del pincel.

1. Si es necesario, seleccione los colores y un pincel:

   - En el [paleta de colores](../windows/colors-window-image-editor-for-icons.md), seleccione el botón primario del mouse para seleccionar un color de primer plano o el botón secundario del mouse para seleccionar un color de fondo.

   - En el [selector de opciones](../windows/toolbar-image-editor-for-icons.md), seleccione una forma que representa el pincel que desea usar.

1. Elija el lugar en la imagen donde desee empezar a dibujar o pintar. El puntero cambia de forma según la herramienta seleccionada.

1. Presione el botón primario del mouse (para el color de primer plano) o el botón secundario del mouse (para el color de fondo) y manténgalo presionado mientras dibuja.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>Para seleccionar y usar una herramienta de dibujo en el menú imagen

1. Vaya al menú **imagen** > **herramientas**.

1. En el submenú en cascada, elija la herramienta que desea usar.

## <a name="lines-or-closed-figures"></a>Las líneas o figuras cerradas

El **Editor de imágenes** herramientas para dibujar líneas y figuras cerradas funcionan de la misma manera: sitúe el cursor en un punto y arrastrar a otra. Para las líneas, estos puntos son los puntos de conexión. Figuras cerradas, estos puntos son las esquinas opuestas de un rectángulo delimitador en la ilustración.

Las líneas se dibujan con un ancho determinado por la selección de pincel actual y las figuras enmarcadas se dibujan con un ancho determinado por la selección actual del ancho. Líneas y las figuras, enmarcado tanto rellenado, se dibujan en el color de primer plano actual si presiona el botón primario del mouse, o en el color de fondo actual, si presiona el botón secundario del mouse.

### <a name="to-draw-a-line"></a>Para dibujar una línea

1. Use la [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md) o vaya al menú **imagen**> **herramientas** y elija el **línea** herramienta.

1. Si es necesario, seleccione los colores y un pincel:

   - En el [paleta de colores](../windows/colors-window-image-editor-for-icons.md), seleccione el botón primario del mouse para seleccionar un color de primer plano o el botón secundario del mouse para seleccionar un color de fondo.

   - En el [selector de opciones](../windows/toolbar-image-editor-for-icons.md), seleccione una forma que representa el pincel que desea usar.

1. Coloque el puntero en el punto de partida de la línea.

1. Arrastre al extremo de la línea.

### <a name="to-draw-a-closed-figure"></a>Para dibujar una figura cerrada.

1. Use la **Editor de imágenes** barra de herramientas o vaya al menú **imagen** > **herramientas** y seleccione un **dibujo de figuras cerradas** herramienta.

   El **dibujo de figuras cerradas** herramientas crean figuras a como se indica en sus respectivos botones.

1. Si es necesario, seleccione los colores y un ancho de línea.

1. Mueva el puntero a una de las esquinas del área rectangular en la que va a dibujar en la ilustración.

1. Arrastre el puntero a la esquina diagonalmente opuesta.

## <a name="custom-brushes"></a>Pinceles predeterminados

Un pincel personalizado es una parte rectangular de una imagen que recoger y usar como uno de los **Editor de imágenes**del pincel predefinido. Todas las operaciones que puede realizar en una selección, puede realizar en un pincel personalizado también.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Para crear un pincel personalizado desde una parte de una imagen

1. Seleccione la parte de la imagen que desea utilizar un pincel.

1. Mantenga el **MAYÚS** clave hacia abajo, elija en la selección y arrastre el puntero sobre la imagen o vaya al menú **imagen** > **usar la selección como pincel**.

   La selección se convierte en un pincel personalizado que distribuye los colores de la selección en la imagen. Copias de la selección se dejan a lo largo de la trayectoria de arrastre. Cuanto más lentamente arrastre, se realizan las copias más.

   > [!NOTE]
   > Seleccionar el **utilizar una selección como pincel** sin seleccionar primero una parte de la imagen se utiliza toda la imagen como un pincel. El resultado de usar un pincel personalizado también depende de si ha seleccionado un [fondo transparente u opaco](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Píxeles de un pincel personalizado que coincida con el color de fondo actual normalmente son transparentes: no pinte de la imagen existente. Puede cambiar este comportamiento para que se pinte píxeles de color de fondo a través de la imagen existente.

Puede usar el pincel personalizado como un sello o una galería de símbolos para crear distintos efectos especiales.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Para dibujar formas de pincel personalizado en el color de fondo

1. Seleccionar un fondo opaco o transparente.

1. Establece el color de fondo en el color en el que va a dibujar.

1. Coloque el pincel personalizado donde va a dibujar.

1. Seleccione el botón secundario del mouse. Las regiones opacas del pincel personalizado se dibujan en el color de fondo.

### <a name="to-double-or-halve-the-custom-brush-size"></a>Para duplicar o a la mitad del tamaño del pincel personalizado

Presione el **signo** (**+**) clave duplicar el tamaño del pincel, o el **signo** (**-**) para dividirlo .

### <a name="to-cancel-the-custom-brush"></a>Para cancelar el pincel personalizado

Presione **Esc** o elija otra herramienta de dibujo.

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)<br/>
[Cómo: Creación de un icono u otra imagen](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Cómo: Edición de una imagen](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Cómo: Trabajo con colores](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>