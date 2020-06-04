---
title: Error del compilador C3499
ms.date: 11/04/2016
f1_keywords:
- C3499
helpviewer_keywords:
- C3499
ms.assetid: 6717de5c-ae0f-4024-bdf2-b5598009e7b6
ms.openlocfilehash: e50aaeac4a9f02cf3e67c25a08afdc2df0f1c62f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738016"
---
# <a name="compiler-error-c3499"></a>Error del compilador C3499

una expresión lambda de la que se ha especificado que tiene un tipo de valor devuelto void no puede devolver un valor

El compilador genera este error cuando una expresión lambda que especifica `void` como el tipo de valor devuelto devuelve un valor; o cuando una expresión lambda contiene más de una instrucción y devuelve un valor, pero no especifica su tipo de valor devuelto.

### <a name="to-correct-this-error"></a>Para corregir este error

- No devuelva un valor de la expresión lambda, o bien

- Facilite el tipo de valor devuelvo de la expresión lambda, o bien

- Combine las instrucciones que componen el cuerpo de la expresión lambda en una única instrucción.

## <a name="example"></a>Ejemplo

El ejemplo siguiente produce un error C3499 porque el cuerpo de una expresión lambda contiene varias instrucciones y devuelve un valor, pero la expresión lambda no especifica el tipo de valor devuelto:

```cpp
// C3499a.cpp

int main()
{
   [](int x) { int n = x * 2; return n; } (5); // C3499
}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra dos posibles soluciones para C3499. La primera solución facilita el tipo de valor devuelto de la expresión lambda. La segunda solución combina las instrucciones que componen el cuerpo de la expresión lambda en una única instrucción.

```cpp
// C3499b.cpp

int main()
{
   // Possible resolution 1:
   // Provide the return type of the lambda expression.
   [](int x) -> int { int n = x * 2; return n; } (5);

   // Possible resolution 2:
   // Combine the statements that make up the body of
   // the lambda expression into a single statement.
   [](int x) { return x * 2; } (5);
}
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)
