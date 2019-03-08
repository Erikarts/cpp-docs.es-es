---
title: Crear una aplicación de contenedor de documentos activo
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
ms.openlocfilehash: 965778fd5d17aa416b198c101edc3a445a39580b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257307"
---
# <a name="creating-an-active-document-container-application"></a>Crear una aplicación de contenedor de documentos activo

La manera más sencilla y más recomendada para crear una aplicación de contenedor de documentos activos es crear una aplicación de contenedor de EXE de MFC mediante el Asistente para aplicaciones MFC y luego modificar la aplicación para admitir la contención de documentos activos.

#### <a name="to-create-an-active-document-container-application"></a>Para crear una aplicación de contenedor de documentos activos

1. Desde el **archivo** menú, haga clic en **proyecto**desde el **New** submenú.

1. En el panel izquierdo, haga clic en **Visual C++** tipo de proyecto.

1. Seleccione **aplicación MFC** en el panel derecho.

1. Denomine el proyecto *MyProj*, haga clic en **Aceptar**.

1. Seleccione el **compatibilidad con documentos compuestos** página.

1. Seleccione el **contenedor** o **contenedor o servidor completo** opción.

1. Seleccione el **contenedor de documentos activos** casilla de verificación.

1. Haga clic en **Finalizar**.

1. Cuando el Asistente para aplicaciones MFC termina de generar la aplicación, abra los siguientes archivos mediante el Explorador de soluciones:

   - *MyProjview.cpp*

1. En *archivo MyProjview.cpp*, realice los cambios siguientes:

   - En `CMyProjView::OnPreparePrinting`, reemplace el contenido de la función con el código siguiente:

     [!code-cpp[NVC_MFCDocView#56](../mfc/codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]

   `OnPreparePrinting` proporciona compatibilidad con la impresión. Este código reemplaza `DoPreparePrinting`, que es la preparación de impresión predeterminada.

   Contención de documentos activos proporciona un esquema de impresión mejorado:

   - Puede llamar primero el documento activo a través de su `IPrint` interfaz e indicarle que se imprima. Esto es diferente de contención OLE anterior, en el que el contenedor tenía que procesar una imagen del elemento contenido en la impresora `CDC` objeto.

   - Si se produce un error, indicará el elemento contenido que se imprima a través de su `IOleCommandTarget` interfaz

   - Si se produce un error, asegúrese de su propia representación del elemento.

   Las funciones miembro estáticas `COleDocObjectItem::OnPrint` y `COleDocObjectItem::OnPreparePrinting`, tal y como se implementa en el código anterior, controlar este esquema de impresión mejorado.

1. Agregar sus propias implementaciones y compile la aplicación.

## <a name="see-also"></a>Vea también

[Contención de documentos activos](../mfc/active-document-containment.md)
