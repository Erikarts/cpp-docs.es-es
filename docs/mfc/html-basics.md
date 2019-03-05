---
title: Conceptos básicos de HTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: 7617216f8fd9a0e4b62ac8b5f12314d38027d836
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263369"
---
# <a name="html-basics"></a>Conceptos básicos de HTML

La mayoría de los exploradores tienen la capacidad de examinar el código fuente HTML de las páginas que examina. Al ver el origen, verá un número de etiquetas HTML (lenguaje de marcado de hipertexto), incluido entre corchetes angulares (<>), intercalados con texto.

Los pasos siguientes usan etiquetas HTML para crear una página Web sencilla. En estos pasos, podrá escribir texto sin formato en un archivo en el Bloc de notas, realizar algunos cambios, guarde el archivo y vuelva a cargar la página en el explorador para ver los cambios.

#### <a name="to-create-an-html-file"></a>Para crear un archivo HTML

1. Abra el Bloc de notas o en cualquier editor de texto sin formato.

1. Desde el **archivo** menú, elija **New**.

1. Escriba las líneas siguientes:

```
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
</HTML>
```

1. Desde el **archivo** menú, elija **guardar**y guarde el archivo como c:\webpages\First.htm. Deje el archivo abierto en el editor.

1. Conmutador al explorador y desde el **archivo** menú, elija **abierto**, o tipo *file://C:/webpages/first.htm* en el cuadro de dirección URL del explorador. Debería ver una página en blanco con el título de ventana "Top HTML Tags".

   Tenga en cuenta las etiquetas están emparejadas y se incluyen en corchetes angulares. Las etiquetas no distinguen mayúsculas de minúsculas, pero a menudo se utilizan mayúsculas y minúsculas para destacar las etiquetas.

   La etiqueta \<HTML > inicia el documento y la etiqueta \</HTML > finaliza. Etiquetas de cierre (no siempre es necesarias) son los mismos que la etiqueta inicial, pero tienen una barra diagonal (/) delante de la etiqueta. No debería haber ningún espacio entre los corchetes angulares (<) y el inicio de la etiqueta.

1. Conmutador al Bloc de notas y después el  \< /HEAD >, escriba:

```
<BODY>
    HTML is swell.
    Life is good.
</BODY>
```

1. Desde el **archivo** menú, elija **guardar**.

1. Vuelva al explorador y actualice la página.

   Las palabras aparecerán en el área cliente de la ventana del explorador. Tenga en cuenta que se omite el retorno de carro. Si desea tener un salto de línea, debe incluir un `<BR>` después de la primera línea.

   Para todos los pasos siguientes, inserte el texto en cualquier lugar entre \<cuerpo > y \<corporal > para agregar al cuerpo del documento.

9. Agregar un encabezado:

```
<H3>Here's the big picture</H3>
```

10. Agregar una imagen mediante un archivo .gif guardado en el mismo directorio que la página:

```
<IMG src="yourfile.gif">
```

11. Agregue una lista:

```
<UL>Make me an unordered list.
<LI>One programmer</LI>
<LI>Ten SDKs</LI>
<LI>Great Internet Apps</LI>
</UL>
```

12. En la lista de números en su lugar, use emparejados \<OL > y \</OL > etiquetas en lugar de la \<UL > y \</UL > etiquetas.

Que debe ayudarle a comenzar. Si ve una excelente característica en una página Web, puede averiguar cómo creó examinando el código fuente HTML. Los editores HTML como Microsoft FrontPage pueden utilizarse para crear páginas simples y avanzadas.

Este es el código fuente HTML completa para el archivo que ha sido creando:

```
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
<BODY>
HTML is swell.<BR>
Life is good.
<H3>Here's the big picture</H3>
<IMG src="yourfile.gif">
<UL>Make me an unordered list.
<LI>One programmer</LI>
<LI>Ten SDKs</LI>
<LI>Great Internet Apps</LI>
</UL>
</BODY>
</HTML>
```

Para obtener una descripción completa de etiquetas, atributos y extensiones, vea la especificación de lenguaje de marcado de hipertexto (HTML):

[http://www.w3.org/pub/WWW/MarkUp/](http://www.w3.org/pub/www/markup/)

## <a name="see-also"></a>Vea también

[Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)
