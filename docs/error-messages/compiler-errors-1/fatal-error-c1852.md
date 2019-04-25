---
title: Error irrecuperable C1852
ms.date: 11/04/2016
f1_keywords:
- C1852
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
ms.openlocfilehash: 895c2fc988c9566f9e50b1ac1a18eb4dc1c6661a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165741"
---
# <a name="fatal-error-c1852"></a>Error irrecuperable C1852

'filename' no es un archivo de encabezado precompilado válido

El archivo no es un encabezado precompilado.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Archivo no válido especificado con **/Yu** o **#pragma hdrstop**.

1. El compilador supone una extensión de archivo .pch si no se especifica lo contrario.