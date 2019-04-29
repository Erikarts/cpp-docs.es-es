---
title: Error del compilador C2814
ms.date: 11/04/2016
f1_keywords:
- C2814
helpviewer_keywords:
- C2814
ms.assetid: 7d165136-a08b-4497-a76d-60a21bb19404
ms.openlocfilehash: 6562e8a0968f83a0e7e968b538b4d94dc1047fa5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329561"
---
# <a name="compiler-error-c2814"></a>Error del compilador C2814

'miembro': un tipo nativo no se puede anidar dentro de un 'tipo' administrado o WinRT

## <a name="example"></a>Ejemplo

Un tipo nativo no se puede anidar en un tipo CLR o WinRT. El ejemplo siguiente genera el error C2814 y muestra cómo corregirlo.

```
// C2814.cpp
// compile with: /clr /c
ref class A {
   class B {};   // C2814
   ref class C {};   // OK
};
```
