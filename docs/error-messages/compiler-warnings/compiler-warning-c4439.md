---
title: Advertencia del compilador C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: d604c234b9445a7e5304118124620f0057f30975
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311350"
---
# <a name="compiler-warning-c4439"></a>Advertencia del compilador C4439

'function': definición de función con un tipo administrado en la firma debe tener una convención de llamada __clrcall

El compilador lo reemplazó implícitamente una convención de llamada con [__clrcall](../../cpp/clrcall.md). Para resolver esta advertencia, quite el `__cdecl` o `__stdcall` convención de llamada.

C4439 siempre se emite como un error. Puede desactivar esta advertencia con el `#pragma warning` o **/wd**; vea [advertencia](../../preprocessor/warning.md) o  [ /w, / W0, / W1, / W2, / w3, / W4, / W1, / W2, / w3, / W4, / Wall, / WD, / we, / WO, / wv, /WX (nivel de advertencia)](../../build/reference/compiler-option-warning-level.md)para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4439.

```
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```