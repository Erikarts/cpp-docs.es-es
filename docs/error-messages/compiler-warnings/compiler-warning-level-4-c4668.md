---
title: Advertencia del compilador (nivel 4) C4668
ms.date: 11/04/2016
f1_keywords:
- C4668
helpviewer_keywords:
- C4668
ms.assetid: c6585460-bc4a-4a15-9242-4cbfce53c961
ms.openlocfilehash: 11d96941a1efddde87068af8829e24259f2fa312
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408165"
---
# <a name="compiler-warning-level-4-c4668"></a>Advertencia del compilador (nivel 4) C4668

'símbolo' no está definido como macro de preprocesador y se reemplaza por '0' para 'directivas'

Se usó un símbolo que no se ha definido con una directiva de preprocesador. El símbolo se evaluará como false. Para definir un símbolo, puede usar el [#define (directiva)](../../preprocessor/hash-define-directive-c-cpp.md) o [/D](../../build/reference/d-preprocessor-definitions.md) opción del compilador.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4668:

```
// C4668.cpp
// compile with: /W4
#include <stdio.h>

#pragma warning (default : 4668)   // turn warning on

int main()
{
    #if q   // C4668, q is not defined
        printf_s("defined");
    #else
        printf_s("undefined");
    #endif
}
```