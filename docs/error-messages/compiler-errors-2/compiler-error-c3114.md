---
title: Error del compilador C3114
ms.date: 11/04/2016
f1_keywords:
- C3114
helpviewer_keywords:
- C3114
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
ms.openlocfilehash: 6ce5b9860cd75619f26a3585981af5807c33535a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50606679"
---
# <a name="compiler-error-c3114"></a>Error del compilador C3114

'argument': argumento de atributo no válido con nombre

En el orden de un miembro de datos de clase de atributo como un argumento con nombre válido, debe marcar no `static`, `const`, o `literal`. Si una propiedad, la propiedad no debe ser `static` y debe tener get y descriptores de acceso.

Para obtener más información, consulte [propiedad](../../windows/property-cpp-component-extensions.md) y [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3114.

```
// C3114.cpp
// compile with: /clr /c
public ref class A : System::Attribute {
public:
   static property int StaticProp {
      int get();
   }

   property int Prop2 {
      int get();
      void set(int i);
   }
};

[A(StaticProp=123)]   // C3114
public ref class R {};

[A(Prop2=123)]   // OK
public ref class S {};
```