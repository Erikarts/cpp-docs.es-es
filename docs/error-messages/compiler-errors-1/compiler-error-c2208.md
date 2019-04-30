---
title: Error del compilador C2208
ms.date: 11/04/2016
f1_keywords:
- C2208
helpviewer_keywords:
- C2208
ms.assetid: 9ae704bc-bf70-45f1-8e47-0470f21edd4e
ms.openlocfilehash: 7970ba5d8d2b19bd6e330fad1879880fc5cbf32d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400453"
---
# <a name="compiler-error-c2208"></a>Error del compilador C2208

'type': no han definido miembros utilizando este tipo

Es un identificador que se resuelve en un nombre de tipo en una declaración de agregado, pero el compilador no puede declarar a un miembro.

El ejemplo siguiente genera C2208:

```
// C2208.cpp
class C {
   C;   // C2208
   C(){}   // OK
};
```