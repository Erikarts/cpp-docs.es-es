---
title: Advertencia del compilador (nivel 1) C4036
ms.date: 11/04/2016
f1_keywords:
- C4036
helpviewer_keywords:
- C4036
ms.assetid: f0b15359-4d62-48ec-8cb1-a7b36587a47f
ms.openlocfilehash: 632e88bb64568c97e937e83e177598054a954f22
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151791"
---
# <a name="compiler-warning-level-1-c4036"></a>Advertencia del compilador (nivel 1) C4036

'type' sin nombre como parámetro real

No se proporciona ningún nombre de tipo para una estructura, unión, enumeración o clase usada como un parámetro real. Si usa [/Zg](../../build/reference/zg-generate-function-prototypes.md) para generar prototipos de función, el compilador emite esta advertencia y convierte en comentario el parámetro formal en el prototipo generado.

Especifique un nombre de tipo para resolver esta advertencia.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4036.

```
// C4036.c
// compile with: /Zg /W1
// D9035 expected
typedef struct { int i; } T;
void f(T* t) {}   // C4036

// OK
typedef struct MyStruct { int i; } T2;
void f2(T2 * t) {}
```