---
title: Usar los archivos de código fuente de MFC
ms.date: 11/04/2016
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
ms.openlocfilehash: ac8d8ea64de9fd93487b3108857669931e31d0be
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267035"
---
# <a name="using-the-mfc-source-files"></a>Usar los archivos de código fuente de MFC

La biblioteca Microsoft Foundation Class (MFC) proporciona código fuente completo. Archivos de encabezado (. h) se encuentran en el directorio \atlmfc\include; archivos de implementación (.cpp) están en el directorio \atlmfc\src\mfc.

Esta serie de artículos explica las convenciones que utiliza MFC para comentar las distintas partes de cada clase, lo que significan estos comentarios y qué se puede esperar encontrar en cada sección. Los asistentes de Visual C++ usan convenciones similares para las clases que crean automáticamente, y probablemente encontrará estas convenciones útiles para su propio código.

Es posible que esté familiarizado con el **pública**, **protegido**, y **privada** palabras clave de C++. Al examinar los archivos de encabezado MFC, encontrará que cada clase puede tener varios de cada uno de ellos. Por ejemplo, podrían ser funciones y variables de miembro público en más de una **pública** palabra clave. Esto es porque MFC separa las variables de miembro y funciones según su uso, no por el tipo de acceso permitido. MFC utiliza **privada** con moderación; incluso elementos consideran los detalles de implementación suelen estar protegidos y muchas veces son públicos. Aunque no se recomienda el acceso a los detalles de implementación, MFC deja la decisión para usted.

En los archivos de código fuente MFC y los archivos que crea el Asistente para aplicaciones MFC, encontrará comentarios como éstos en declaraciones de clase (normalmente en este orden):

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

Los temas de esta serie de artículos incluyen:

- [Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md)

- [El / / comentario de implementación](../mfc/decrement-implementation-comment.md)

- [La / / Constructors (comentario)](../mfc/decrement-constructors-comment.md)

- [La / / Attributes comentario](../mfc/decrement-attributes-comment.md)

- [La / / Operations (comentario)](../mfc/decrement-operations-comment.md)

- [La / / Overridables comentario](../mfc/decrement-overridables-comment.md)

## <a name="see-also"></a>Vea también

[Temas generales de MFC](../mfc/general-mfc-topics.md)
