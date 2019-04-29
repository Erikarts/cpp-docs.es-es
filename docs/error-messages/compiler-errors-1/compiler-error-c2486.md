---
title: Error del compilador C2486
ms.date: 11/04/2016
f1_keywords:
- C2486
helpviewer_keywords:
- C2486
ms.assetid: 436da349-6461-4e32-bfca-4f3e620108e2
ms.openlocfilehash: 8d745c03530f331da83b45c765a2cb4bb7d76d8e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364355"
---
# <a name="compiler-error-c2486"></a>Error del compilador C2486

'__LOCAL_SIZE' solo se permite en la función con el atributo 'naked'

En las funciones de ensamblado alineado, el nombre `__LOCAL_SIZE` está reservado para las funciones declaradas con el [naked](../../cpp/naked-cpp.md) atributo.

El ejemplo siguiente genera C2486:

```
// C2486.cpp
// processor: x86
void __declspec(naked) f1() {
   __asm {
      mov   eax,   __LOCAL_SIZE
   }
}
void f2() {
   __asm {
      mov   eax,   __LOCAL_SIZE   // C2486
   }
}
```