---
title: Advertencia del compilador (nivel 4) C4626
ms.date: 11/04/2016
f1_keywords:
- C4626
helpviewer_keywords:
- C4626
ms.assetid: 7f822ff4-a4a3-4f17-b45b-e8b7b4659a14
ms.openlocfilehash: cb00365d12a60885a86a42417bf1c1052a5c6d6c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349609"
---
# <a name="compiler-warning-level-4-c4626"></a>Advertencia del compilador (nivel 4) C4626

'clase derivada': el operador de asignaciones se definió implícitamente como eliminado porque un operador de asignaciones es inaccesible o se ha eliminado

Se eliminó un operador de asignación o no está accesible en una clase base y, por tanto, no se generó para una clase derivada. Cualquier intento de asignar objetos de este tipo provocará un error del compilador.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

El ejemplo siguiente genera el error C4626 y muestra cómo corregirlo.

```
// C4626
// compile with: /W4
#pragma warning(default : 4626)
class B
{
// public:
   B& operator = (const B&)
   {
      return *this;
   }
};

class D : public B
{

}; // C4626 - to fix, make B's copy constructor public

int main()
{
   D m;
   D n;
   // m = n;   // this line will cause an error
}
```