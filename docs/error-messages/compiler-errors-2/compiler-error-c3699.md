---
title: Error del compilador C3699
ms.date: 11/04/2016
f1_keywords:
- C3699
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
ms.openlocfilehash: 93058d34ca9a17ab175a55a7bc7b953d369e65c5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776744"
---
# <a name="compiler-error-c3699"></a>Error del compilador C3699

'operador': no se puede utilizar este direccionamiento indirecto en el tipo 'type'

Se intentó usar el direccionamiento indirecto no permitido en `type`.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3699.

```
// C3699.cpp
// compile with: /clr /c
using namespace System;
int main() {
   String * s;   // C3699
   // try the following line instead
   // String ^ s2;
}
```

## <a name="example"></a>Ejemplo

Una propiedad trivial no puede tener tipo de referencia. Vea [property](../../extensions/property-cpp-component-extensions.md) para obtener más información. El ejemplo siguiente genera C3699.

```
// C3699_b.cpp
// compile with: /clr /c
ref struct C {
   property System::String % x;   // C3699
   property System::String ^ y;   // OK
};
```

## <a name="example"></a>Ejemplo

El equivalente de una sintaxis de "puntero a un puntero" es un identificador para una referencia de seguimiento. El ejemplo siguiente genera C3699.

```
// C3699_c.cpp
// compile with: /clr /c
using namespace System;
void Test(String ^^ i);   // C3699
void Test2(String ^% i);
```