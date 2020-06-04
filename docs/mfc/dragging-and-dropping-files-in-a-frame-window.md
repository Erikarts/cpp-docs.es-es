---
title: Arrastrar y colocar archivos en una ventana de marco
ms.date: 11/04/2016
helpviewer_keywords:
- drag and drop [MFC], files
- drag and drop [MFC], File Manager
- Windows Explorer [MFC]
- File Manager drag and drop support [MFC]
- files [MFC], drag and drop
- frame windows [MFC], dragging and dropping files in
- drag and drop [MFC], Windows Explorer
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
ms.openlocfilehash: 0129b939e0fe2afd5dd29623bb44418bfd16c20d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240665"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>Arrastrar y colocar archivos en una ventana de marco

La ventana de marco administra una relación con el Explorador de archivos o el Administrador de archivos.

Al agregar unos Inicializando llama en el reemplazo de la `CWinApp` función miembro `InitInstance`, tal y como se describe en [CWinApp: La clase Application](../mfc/cwinapp-the-application-class.md), puede tener la ventana de marco indirectamente abrir archivos arrastra desde el Explorador de archivos o el Administrador de archivos y se coloca en la ventana de marco. Consulte [Administrador de archivos de arrastrar y colocar](../mfc/special-cwinapp-services.md).

## <a name="see-also"></a>Vea también

[Uso de ventanas de marco](../mfc/using-frame-windows.md)
