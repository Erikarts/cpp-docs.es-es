---
title: Error del compilador C2289
ms.date: 11/04/2016
f1_keywords:
- C2289
helpviewer_keywords:
- C2289
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
ms.openlocfilehash: 9fe9b765af72a8864e3e899cafcf648a9facb67e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182800"
---
# <a name="compiler-error-c2289"></a>Error del compilador C2289

el mismo calificador de tipo se ha utilizado más de una vez

Una definición o declaración de tipo utiliza un calificador de tipo (`const`, `volatile`, `signed`o `unsigned`) más de una vez, lo que provoca un error de compatibilidad con ANSI (**/Za**).

El ejemplo siguiente genera la advertencia C2286:

```
// C2289.cpp
// compile with: /Za /c
volatile volatile int i;   // C2289
volatile int j;   // OK
```