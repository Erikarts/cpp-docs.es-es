---
title: Error de las herramientas del vinculador LNK1264
ms.date: 11/04/2016
f1_keywords:
- LNK1264
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
ms.openlocfilehash: ca17b6946b9e988507af2786825223e042356d0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505097"
---
# <a name="linker-tools-error-lnk1264"></a>Error de las herramientas del vinculador LNK1264

/ LTCG: PGINSTRUMENT especificado pero no generación de código necesarios; Error de instrumentación

**/ LTCG: PGINSTRUMENT** se ha especificado, pero se encontraron archivos no .obj que se compilaron con [/GL](../../build/reference/gl-whole-program-optimization.md). Instrumentación no puede tener lugar y en el vínculo de error. Debe haber al menos un archivo .obj en la línea de comandos que se compila con **/GL** para que puedan realizarse la instrumentación.

Optimización guiada por perfiles (PGO) sólo está disponible en los compiladores de 64 bits.