---
title: Error del compilador C3764
ms.date: 11/04/2016
f1_keywords:
- C3764
helpviewer_keywords:
- C3764
ms.assetid: af5d254c-8d4a-4dda-aad9-3c5c1257c868
ms.openlocfilehash: 2570ee9abb148b919242de7786cd6fa91765286f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400258"
---
# <a name="compiler-error-c3764"></a>Error del compilador C3764

'función_de_reemplazo': no se puede invalidar el método de clase base 'función_de_clase_base'

El compilador detectó una invalidación con formato incorrecto. Por ejemplo, la función de la clase base no era `virtual`. Para obtener más información, consulte [invalidar](../../extensions/override-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3764.

```
// C3764.cpp
// compile with: /clr /c
public ref struct A {
   void g(int);
   virtual void h(int);
};

public ref struct B : A {
   virtual void g(int) override {}   // C3764
   virtual void h(int) override {}   // OK
};
```

## <a name="example"></a>Ejemplo

C3764 también puede producirse cuando un método de clase base es explícitamente y con nombre se reemplaza. El ejemplo siguiente genera C3764.

```
// C3764_b.cpp
// compile with: /clr /c
ref struct A {
   virtual void Test() {}
};

ref struct B : public A {
   virtual void Test() override {}
   virtual void Test2() = A::Test {}   // C3764
};
```