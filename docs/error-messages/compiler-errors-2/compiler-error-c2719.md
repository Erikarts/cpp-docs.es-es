---
title: Error del compilador C2719
ms.date: 11/04/2016
f1_keywords:
- C2719
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
ms.openlocfilehash: d635601fbf8b36218fb47c09444f3f5d023c823e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383092"
---
# <a name="compiler-error-c2719"></a>Error del compilador C2719

'parameter': el parámetro formal con __declspec(align('#')) no se alineará

El [alinear](../../cpp/align-cpp.md) `__declspec` modificador no está permitido en parámetros de función. La alineación de los parámetros de función se controla mediante la convención de llamada que se utiliza. Para obtener más información, consulte [convenciones de llamada](../../cpp/calling-conventions.md).

El siguiente ejemplo genera el error C2719 y muestra cómo corregirlo:

```
// C2719.cpp
void func(int __declspec(align(32)) i);   // C2719
// try the following line instead
// void func(int i);
```