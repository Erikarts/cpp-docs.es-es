---
title: Advertencia del compilador (nivel 4) C4232
ms.date: 11/04/2016
f1_keywords:
- C4232
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
ms.openlocfilehash: dee087b73bf032a68daf0527ea584efcc7579361
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401090"
---
# <a name="compiler-warning-level-4-c4232"></a>Advertencia del compilador (nivel 4) C4232

ha utilizado una extensión no estándar: 'identifier': la dirección de dllimport 'dllimport' no es estática, no garantiza la identidad

Con las extensiones de Microsoft (/Ze), puede indicar un valor no estático como la dirección de una función declarada con el **dllimport** modificador. La compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), esto produce un error.

El ejemplo siguiente genera C4232:

```
// C4232.c
// compile with: /W4 /Ze /c
int __declspec(dllimport) f();
int (*pfunc)() = &f;   // C4232
```