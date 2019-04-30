---
title: Error de las herramientas del vinculador LNK1188
ms.date: 11/04/2016
f1_keywords:
- LNK1188
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
ms.openlocfilehash: 69ac20522aebb7391319c0de210e06b305f3fd0d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226483"
---
# <a name="linker-tools-error-lnk1188"></a>Error de las herramientas del vinculador LNK1188

BADFIXUPSECTION:: destino de corrección no válida "symbol"; posible sección de longitud cero

Durante un vínculo de VxD, el destino de una reubicación no tenía una sección. Con LINK386 (una versión anterior), un registro OMF GROUP (generado por una directiva de grupo de MASM) puede haberse usado para combinar la sección de longitud cero con otra sección de longitud distinta de cero. El formato COFF no es compatible con la directiva de grupo y las secciones de longitud cero. Cuando LINK convierte automáticamente este tipo de objetos OMF a COFF, puede producirse este error.