---
title: Error del compilador C2803
ms.date: 11/04/2016
f1_keywords:
- C2803
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
ms.openlocfilehash: d20b8dde9f4134273adcba0f947f685f7ce7d213
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447273"
---
# <a name="compiler-error-c2803"></a>Error del compilador C2803

'operator operator' debe tener al menos un parámetro formal de tipo de clase

El operador sobrecargado no tiene un parámetro de tipo de clase.

Debe pasar al menos un parámetro por referencia (que no usan punteros, pero las referencias) o por valor para poder escribir "un < b" (un y b es de una clase de tipo A).

Si ambos parámetros son punteros será una comparación de direcciones de puntero pura y no utiliza la conversión definida por el usuario.

El ejemplo siguiente genera C2803:

```
// C2803.cpp
// compile with: /c
class A{};
bool operator< (const A *left, const A *right);   // C2803
// try the following line instead
// bool operator< (const A& left, const A& right);
```