---
title: Advertencia del compilador (nivel 3) C4290
ms.date: 11/04/2016
f1_keywords:
- C4290
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
ms.openlocfilehash: c585294686298a1197d437d41a0d541f1268985f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402091"
---
# <a name="compiler-warning-level-3-c4290"></a>Advertencia del compilador (nivel 3) C4290

C++especificación de excepción que se ignoran, excepto to indicar que una función no es __declspec (nothrow)

Una función se declara mediante la especificación de excepción, que Visual C++ admite pero no implementa. Con la excepción que deba volver a compilar las especificaciones que se omiten durante la compilación de código y vinculada para ser reutilizado en futuras versiones que admiten las especificaciones de excepción.

Para obtener más información, consulte [especificaciones de excepciones (throw)](../../cpp/exception-specifications-throw-cpp.md) .

Puede evitar esta advertencia mediante la [advertencia](../../preprocessor/warning.md) pragma:

```
#pragma warning( disable : 4290 )
```

Ejemplo de código siguiente genera C4290:

```
// C4290.cpp
// compile with: /EHs /W3 /c
void f1(void) throw(int) {}   // C4290

// OK
void f2(void) throw() {}
void f3(void) throw(...) {}
```