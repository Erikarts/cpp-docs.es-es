---
title: Error del compilador C3657
ms.date: 11/04/2016
f1_keywords:
- C3657
helpviewer_keywords:
- C3657
ms.assetid: 89a28a18-4c17-43a1-bda6-deb52c32d203
ms.openlocfilehash: f979d5776bea5e8fb6e0255bdcdeaacb284932ac
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778467"
---
# <a name="compiler-error-c3657"></a>Error del compilador C3657

los destructores no pueden invalidar o ser invalidados explícitamente

Los destructores o finalizadores no se puede reemplazar explícitamente. Para obtener más información, consulte [invalidaciones explícitas](../../extensions/explicit-overrides-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3657.

```
// C3657.cpp
// compile with: /clr
public ref struct I {
   virtual ~I() { }
   virtual void a();
};

public ref struct D : I {
   virtual ~D() = I::~I {}   // C3657
   virtual void a() = I::a {}   // OK
};
```