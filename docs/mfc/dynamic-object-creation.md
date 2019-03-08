---
title: Creación de objetos dinámicos
ms.date: 11/04/2016
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: 3478e5481c177e0ebca1e6b5c2cd07509371c5ef
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260132"
---
# <a name="dynamic-object-creation"></a>Creación de objetos dinámicos

En este artículo se explica cómo crear un objeto dinámicamente en tiempo de ejecución. El procedimiento utiliza la información de clase en tiempo de ejecución, como se describe en el artículo [acceso a información de clase de tiempo de ejecución](../mfc/accessing-run-time-class-information.md).

#### <a name="to-dynamically-create-an-object-given-its-run-time-class"></a>Para crear dinámicamente un objeto, dada su clase en tiempo de ejecución

1. Use el código siguiente para crear un objeto dinámicamente mediante el uso de la `CreateObject` función de la `CRuntimeClass`. Tenga en cuenta que en caso de error, `CreateObject` devuelve **NULL** en lugar de generar una excepción:

   [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>Vea también

[Uso de CObject](../mfc/using-cobject.md)
