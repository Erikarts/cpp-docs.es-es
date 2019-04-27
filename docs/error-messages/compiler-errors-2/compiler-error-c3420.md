---
title: Error del compilador C3420
ms.date: 11/04/2016
f1_keywords:
- C3420
helpviewer_keywords:
- C3420
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
ms.openlocfilehash: 3db109598ce0741ca34a230d8925994543bcb5ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182462"
---
# <a name="compiler-error-c3420"></a>Error del compilador C3420

'finalizador': un finalizador no puede ser virtual

Solo se puede llamar a un finalizador de forma no virtual desde su tipo envolvente. Por consiguiente, es un error declarar un finalizador virtual.

Para obtener más información, consulte [destructores y finalizadores en cómo: Definir y utilizar clases y structs (C++ / c++ / CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3420.

```
// C3420.cpp
// compile with: /clr /c
ref class R {
   virtual !R() {}   // C3420
};
```