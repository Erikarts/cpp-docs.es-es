---
title: Advertencia del compilador (nivel 4) C4701
ms.date: 11/04/2016
f1_keywords:
- C4701
helpviewer_keywords:
- C4701
ms.assetid: d7c76c66-1f3f-4d3c-abe4-5d94c84a5a1f
ms.openlocfilehash: cbe70de39d2306edd50bb936ac5bbb4ad14af0e5
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037268"
---
# <a name="compiler-warning-level-4-c4701"></a>Advertencia del compilador (nivel 4) C4701

variable local potencialmente no inicializada 'nombre' utilizada

La variable local *nombre* es posible que se han usado sin que se asigna un valor. Esto podría producir resultados imprevisibles.

## <a name="example"></a>Ejemplo

El código siguiente genera C4701 y C4703.

```cpp
#include <malloc.h>

void func(int size)
{
    void* p;
    if (size < 256) {
        p = malloc(size);
    }

    if (p != nullptr) // C4701 and C4703
        free(p);
}

void main()
{
    func(9);
}
```

```Output
c:\src\test.cpp(10) : warning C4701: potentially uninitialized local variable 'p' used
c:\src\test.cpp(10) : warning C4703: potentially uninitialized local pointer variable 'p' used
```

Para corregir esta advertencia, inicialice la variable tal como se muestra en este ejemplo:

```cpp
#include <malloc.h>

void func(int size)
{
    void* p = nullptr;
    if (size < 256) {
        p = malloc(size);
    }

    if (p != nullptr)
        free(p);
}

void main()
{
    func(9);
}
```

## <a name="see-also"></a>Vea también

[Advertencia del compilador (nivel 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)<br/>
[Advertencias, /sdl y mejora de la detección de variables sin inicializar](https://www.microsoft.com/security/blog/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/)