---
title: Error del compilador C2380
ms.date: 11/04/2016
f1_keywords:
- C2380
helpviewer_keywords:
- C2380
ms.assetid: 717b1e6e-ddfe-4bac-a5f3-7f9a4dcb1572
ms.openlocfilehash: c0494d4ba405a084e7b455139016c98af7d95191
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344835"
---
# <a name="compiler-error-c2380"></a>Error del compilador C2380

tipos anteriores 'identifier' (¿constructor con tipo de valor devuelto o redefinición no válida de nombre de clase actual?)

Un constructor devuelve un valor o vuelve a definir el nombre de clase.

El ejemplo siguiente genera la advertencia C2326:

```
// C2380.cpp
// compile with: /c
class C {
public:
   int C();   // C2380, specifies an int return
   int C;   // C2380, redefinition of i
   C();   // OK
};
```