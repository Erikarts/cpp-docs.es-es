---
title: Error del compilador C2372
ms.date: 11/04/2016
f1_keywords:
- C2372
helpviewer_keywords:
- C2372
ms.assetid: 406bea63-c8d3-4231-9d26-c70af6980840
ms.openlocfilehash: db13a6bc108588fbbd9c15e2bcc647bea073a333
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339031"
---
# <a name="compiler-error-c2372"></a>Error del compilador C2372

'identifier': redefinición; diferentes tipos de direccionamiento indirecto

El identificador ya está definido con un tipo derivado diferentes.

El ejemplo siguiente genera la advertencia C2326:

```
// C2372.cpp
// compile with: /c
extern int *fp;
extern int fp[];   // C2372
extern int fp2[];   // OK
```