---
title: Error del compilador C3413
ms.date: 11/04/2016
f1_keywords:
- C3413
helpviewer_keywords:
- C3413
ms.assetid: de6c9b05-c373-4bd8-8cb0-12c2cd2e5674
ms.openlocfilehash: e344d06345c0f3a79b86e9cab4e1c5dacb47e9c2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453292"
---
# <a name="compiler-error-c3413"></a>Error del compilador C3413

'name': creación de instancias explícitas no válida

El compilador detectó una instancia explícita mal formada.

El ejemplo siguiente genera la advertencia C3413:

```
// C3413.cpp
template
class MyClass {};   // C3413
```

Posible resolución:

```
// C3413b.cpp
// compile with: /c
template <class T>
class MyClass {};

template <>
class MyClass<int> {};
```