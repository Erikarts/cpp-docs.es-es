---
title: Error del compilador C2942
ms.date: 11/04/2016
f1_keywords:
- C2942
helpviewer_keywords:
- C2942
ms.assetid: 13abf744-8fa1-450d-886d-e5717c04956e
ms.openlocfilehash: 8a594b9d1d8374caa972f6bfdafe5d691e634a9a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366646"
---
# <a name="compiler-error-c2942"></a>Error del compilador C2942

'class': el identificador de clase de tipo se volvió a definir como argumento formal de una función.

No puede usar una clase genérica o de plantilla como un argumento formal. No se puede pasar un argumento directamente al constructor de una clase genérica o clase de plantilla.

El ejemplo siguiente genera la advertencia C2942:

```

// C2942.cpp
// compile with: /c
template<class T>
struct TC {};
void f(int TC<int>) {}   // C2942

// OK
struct TC2 {};
void f(TC2 i) {}
```

También se puede producir el error C2942 al usar genéricos:

```
// C2942b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
void f(int GC<int>) {}   // C2942
ref struct GC2 { };
void f(int GC2) {}
```