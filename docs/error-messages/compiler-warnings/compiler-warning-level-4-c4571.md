---
title: Advertencia del compilador (nivel 4) C4571
ms.date: 11/04/2016
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 92164bf297a44871897b6c6150eb54f8c5ccf3cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220460"
---
# <a name="compiler-warning-level-4-c4571"></a>Advertencia del compilador (nivel 4) C4571

Informativo: semántica de catch (...) cambiada desde Visual C++ 7.1; ya no se detectan excepciones estructuradas (SEH)

C4571 se genera para cada bloque catch (...) al compilar con **/EHs**.

Cuando se compila con **/EHs**, un bloque catch (...) no detecta una excepción estructurada (división por cero, un puntero nulo, por ejemplo); un catch (...) bloque will solo catch producida explícitamente, las excepciones de C++.  Para más información, consulte [Control de excepciones](../../cpp/exception-handling-in-visual-cpp.md).

De forma predeterminada, esta advertencia está desactivada.  Active esta advertencia para asegurarse de que cuando se compila con **/EHs** los bloques catch (...) no tiene intención de excepciones estructuradas.  Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

Puede resolver en una de las siguientes maneras, C4571

- Compile con **/EHa** si aún desea que los bloques catch (...) para detectar las excepciones estructuradas.

- No habilite C4571 si no desea que los bloques catch (...) para detectar las excepciones estructuradas, pero desea usar los bloques catch (...).  Puede detectar mediante las palabras clave de control de excepciones estructurado de excepciones estructuradas (**__try**, **__except**, y **__finally**).  Pero recuerde que, cuando se compila **/EHs** destructores solo se llamará cuando se produce una excepción de C++, no cuando se produce una excepción SEH.

- Reemplace el bloque catch (...) con los bloques catch específica para C++ excepciones y si lo desea, agregue estructurado de excepciones en torno a la C++ control de excepciones (**__try**, **__except**, y **__finally**).  Consulte [control de excepciones estructurado (C/C ++)](../../cpp/structured-exception-handling-c-cpp.md) para obtener más información.

Consulte [/EH (modelo de control de excepciones)](../../build/reference/eh-exception-handling-model.md) para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4571.

```
// C4571.cpp
// compile with: /EHs /W4 /c
#pragma warning(default : 4571)
int main() {
   try {
      int i = 0, j = 1;
      j /= i;   // this will throw a SE (divide by zero)
   }
   catch(...) {}   // C4571 warning
}
```