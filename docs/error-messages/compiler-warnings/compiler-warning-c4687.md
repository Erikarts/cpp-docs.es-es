---
title: Advertencia del compilador C4687
ms.date: 11/04/2016
f1_keywords:
- C4687
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
ms.openlocfilehash: 1978e1a35ba5b5d59b5961a21378d8af6921d145
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58778668"
---
# <a name="compiler-warning-c4687"></a>Advertencia del compilador C4687

'class': una clase abstracta sellada no puede implementar una interfaz 'interface'

Normalmente, un tipo sealed abstracto sólo es útil para contener las funciones miembro estáticas.

Para obtener más información, consulte [abstracta](../../extensions/abstract-cpp-component-extensions.md)y [sealed](../../extensions/sealed-cpp-component-extensions.md).

C4687 se emite como un error de forma predeterminada. Puede suprimir C4687 con la [advertencia](../../preprocessor/warning.md) pragma. Si está seguro de que desea implementar una interfaz en un tipo sealed abstracto, puede suprimir la advertencia C4687.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4687.

```
// C4687.cpp
// compile with: /clr /c
interface class A {};

ref struct B sealed abstract : A {};   // C4687
ref struct C sealed : A {};   // OK
ref struct D abstract : A {};   // OK
```