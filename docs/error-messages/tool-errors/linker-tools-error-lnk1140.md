---
title: Error de las herramientas del vinculador LNK1140
ms.date: 11/04/2016
f1_keywords:
- LNK1140
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
ms.openlocfilehash: 48c735f29918c4d1caeb15123f7376276d116fb4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255071"
---
# <a name="linker-tools-error-lnk1140"></a>Error de las herramientas del vinculador LNK1140

demasiados módulos para la base de datos de programa; vincule con/PDB: NONE

El proyecto contiene más de 4096 módulos.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Vuelva a vincular con [/PDB: NONE](../../build/reference/pdb-use-program-database.md).

1. Algunos módulos se compile sin información de depuración.

1. Reduzca el número de módulos.