---
title: Error del compilador C2355
ms.date: 11/04/2016
f1_keywords:
- C2355
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
ms.openlocfilehash: 80871a73a7c3b4ad04b475539015f85d21ae88b7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611290"
---
# <a name="compiler-error-c2355"></a>Error del compilador C2355

'this': solo se puede hacer referencia a this en funciones miembro no estáticas o inicializadores de miembro de datos no estáticos

El puntero `this` solo es válido en funciones miembro no estáticas o en inicializadores de miembro de datos no estáticos. Este error puede producirse si el ámbito de clase de una definición de función miembro fuera de la declaración de clase no está calificado correctamente. El error también puede producirse si el puntero `this` se utiliza en una función que no se haya declarado en la clase.

Para corregir este problema, asegúrese de que la definición de función miembro coincida con una declaración de función miembro de la clase y que no se haya declarado como estática. En los inicializadores de miembro de datos, asegúrese de que el miembro de datos no se haya declarado como estático.

El ejemplo siguiente genera el error C2355 y muestra cómo corregirlo:

```
// C2355.cpp
// compile with: /c
class MyClass {};
MyClass *p = this;   // C2355

// OK
class MyClass2 {
public:
   void Test() {
      MyClass2 *p = this;
   }
};
```