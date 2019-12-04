---
title: Error del compilador C3116
ms.date: 11/04/2016
f1_keywords:
- C3116
helpviewer_keywords:
- C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
ms.openlocfilehash: d0c8e7cab936171f89b33c90b4134a97c40b2c81
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741188"
---
# <a name="compiler-error-c3116"></a>Error del compilador C3116

' especificador de almacenamiento ': clase de almacenamiento no válida para el método de interfaz

Usó `typedef`, `register`o `static` como clase de almacenamiento para un método de interfaz. Estas clases de almacenamiento no se permiten en los miembros de la interfaz.

En el ejemplo siguiente se genera C3116:

```cpp
// C3116.cpp
__interface ImyInterface
{
   static void myFunc();   // C3116
};
```
