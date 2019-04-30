---
title: Advertencia del compilador (nivel 1) C4727
ms.date: 11/04/2016
f1_keywords:
- C4727
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
ms.openlocfilehash: be1a248fc2709706e137b543344966735c19064e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386439"
---
# <a name="compiler-warning-level-1-c4727"></a>Advertencia del compilador (nivel 1) C4727

"El PCH denominado archivo_pch con la misma marca de tiempo en archivo_obj_1 y archivo_obj_2.  Usar el primer PCH.

C4727 se produce cuando se compilan varios elementos con **/Yc**, y donde el compilador no pudo marcar todos los archivos .obj con la misma marca de tiempo de pch.

Para resolver, compile un archivo de código fuente con **/c/Yc** (crea pch), y los demás compilan por separado con **/Yu /c** (utiliza pch), a continuación, vincularlos entre sí.

Por lo tanto, si genera C4727 e hice lo siguiente:

**cl /clr /GL a.cpp b.cpp c.cpp /Ycstdafx.h**

En su lugar se haría lo siguiente:

**cl /clr /GL a.cpp /Ycstdafx.h /c**

**cl /clr /GL b.cpp c.cpp /Yustdafx.h /link a.obj**

Para obtener más información, consulte

- [/Yc (Crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md)

- [/Yu (Usar el archivo de encabezado precompilado)](../../build/reference/yu-use-precompiled-header-file.md)