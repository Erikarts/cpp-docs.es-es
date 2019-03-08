---
title: Configurar las imágenes para un elemento individual
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
ms.openlocfilehash: 39aa4761dbc753c42f1aedbb18f1832eab471e50
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294712"
---
# <a name="setting-the-images-for-an-individual-item"></a>Configurar las imágenes para un elemento individual

Los diferentes tipos de imágenes utilizados por el elemento de cuadro combinado extendido se determinan por los valores de la *iImage*, *iSelectedImage*, y *iOverlay* los miembros de la [ COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema) estructura. Cada valor es el índice de una imagen en la lista de imágenes asociada del control. De forma predeterminada, estos miembros se establecen en 0, haciendo que el control no mostrar para el elemento no aparece ninguna imagen. Si desea utilizar imágenes para un elemento específico, puede modificar la estructura en consecuencia, cuando se inserta el elemento de cuadro combinado o modificando un elemento de cuadro combinado existente.

## <a name="setting-the-image-for-a-new-item"></a>Establecer la imagen de un nuevo elemento

Si va a insertar un nuevo elemento, inicialice la *iImage*, *iSelectedImage*, y *iOverlay* miembros con los valores adecuados de estructura y, a continuación, inserte el elemento con una llamada a [CComboBoxEx:: InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem).

El ejemplo siguiente inserta un nuevo elemento de cuadro combinado extendido (`cbi`) en el control de cuadro combinado extendido (`m_comboEx`), proporcionando índices para los tres estados de la imagen:

[!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]

## <a name="setting-the-image-for-an-existing-item"></a>Establecer la imagen de un elemento existente

Si va a modificar un elemento existente, deberá trabajar con el *máscara* miembro de un **COMBOBOXEXITEM** estructura.

#### <a name="to-modify-an-existing-item-to-use-images"></a>Para modificar un elemento existente para usar imágenes

1. Declarar un **COMBOBOXEXITEM** estructurar y establecer el *máscara* miembro de datos a los valores está interesado en modificar.

1. Con esta estructura, realice una llamada a [CComboBoxEx:: GetItem](../mfc/reference/ccomboboxex-class.md#getitem).

1. Modificar el *máscara*, *iImage*, y *iSelectedImage* miembros de la estructura recién devuelta, usando los valores adecuados.

1. Realizar una llamada a [CComboBoxEx:: SetItem](../mfc/reference/ccomboboxex-class.md#setitem), pasando la estructura modificada.

El ejemplo siguiente muestra este procedimiento intercambiando las imágenes seleccionadas y del tercer elemento de cuadro combinado extendido:

[!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]

## <a name="see-also"></a>Vea también

[Uso de CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Controles](../mfc/controls-mfc.md)
