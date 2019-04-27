---
title: Error del compilador C2006
ms.date: 11/04/2016
f1_keywords:
- C2006
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
ms.openlocfilehash: c23f17483925f25468214165fb459db577e576fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209015"
---
# <a name="compiler-error-c2006"></a>Error del compilador C2006

'directiva' esperaba un nombre de archivo, que pero se encontró 'token'

Las directivas como [#include](../../preprocessor/hash-include-directive-c-cpp.md) o [#import](../../preprocessor/hash-import-directive-cpp.md) requieren un nombre de archivo. Para resolver el error, asegúrese de que *token* es un nombre de archivo válido. Además, coloque el nombre de archivo en comillas dobles o corchetes angulares.

El ejemplo siguiente genera C2006:

```
// C2006.cpp
#include stdio.h   // C2006
```

Posible resolución:

```
// C2006b.cpp
// compile with: /c
#include <stdio.h>
```