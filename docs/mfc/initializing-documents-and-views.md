---
title: Inicializar documentos y vistas
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
ms.openlocfilehash: 0cf9faecbb7e0d74c2199a1a829aa68241e1c019
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297117"
---
# <a name="initializing-documents-and-views"></a>Inicializar documentos y vistas

Se crean documentos de dos maneras diferentes, por lo que la clase de documento debe ser compatible con ambas formas. En primer lugar, el usuario puede crear un nuevo documento vacío con el comando nuevo archivo. En ese caso, inicialice el documento en el reemplazo del [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) función miembro de clase [CDocument](../mfc/reference/cdocument-class.md). En segundo lugar, el usuario puede utilizar el comando Abrir en el menú archivo para crear un nuevo documento cuyo contenido se lee desde un archivo. En ese caso, inicialice el documento en el reemplazo del [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) función miembro de clase `CDocument`. Si dos inicializaciones son iguales, puede llamar a una función miembro común desde ambos reemplazos, o `OnOpenDocument` puede llamar a `OnNewDocument` para inicializar un documento limpio y, después, finalice la operación de apertura.

Las vistas se crean después de que se crean sus documentos. El mejor momento para inicializar una vista es después de que el marco de trabajo ha terminado de crear el documento, la ventana de marco y la vista. Puede inicializar la vista invalidando el [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) función miembro de [CView](../mfc/reference/cview-class.md). Si necesita reinicializar o ajustar algo cada vez que los cambios del documento, se puede reemplazar [OnUpdate](../mfc/reference/cview-class.md#onupdate).

## <a name="see-also"></a>Vea también

[Inicialización y limpieza de documentos y vistas](../mfc/initializing-and-cleaning-up-documents-and-views.md)
