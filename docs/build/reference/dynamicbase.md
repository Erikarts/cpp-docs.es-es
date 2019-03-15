---
title: /DYNAMICBASE
ms.date: 06/12/2018
f1_keywords:
- /dynamicbase
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
ms.openlocfilehash: 13987b4ba9c25db0f5417da562ff86f4230937d7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808305"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

Especifica si debe generarse una imagen ejecutable que puede reubicarse aleatoriamente durante la carga mediante el uso de la característica de selección aleatoria (ASLR) de diseño del espacio de direcciones de Windows que estuvo disponible en Windows Vista poseían primera vez.

## <a name="syntax"></a>Sintaxis

> **/DYNAMICBASE**[**:NO**]

## <a name="remarks"></a>Comentarios

El **/DYNAMICBASE** opción modifica el encabezado de un *imagen ejecutable*, un archivo .dll o .exe, para indicar si la aplicación debería fusionarse aleatoriamente en tiempo de carga y permite la dirección virtual selección aleatoria de asignación, lo que afecta a la ubicación de memoria virtual de montones, pilas y otras asignaciones de sistema operativo. El **/DYNAMICBASE** opción se aplica a las imágenes de 32 bits y 64 bits. ASLR se admite en Windows Vista y sistemas operativos posteriores. Omite la opción de sistemas operativos anteriores.

De forma predeterminada, **/DYNAMICBASE** está habilitado. Para deshabilitar esta opción, utilice **: no**. El **/DYNAMICBASE** opción es necesaria para la [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) opción tenga efecto.

## <a name="see-also"></a>Vea también

- [Opciones de EDITBIN](editbin-options.md)
- [Defensas de seguridad de Software de ISV de Windows](https://msdn.microsoft.com/library/bb430720.aspx)