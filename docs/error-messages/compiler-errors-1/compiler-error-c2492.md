---
title: Error del compilador C2492
ms.date: 11/04/2016
f1_keywords:
- C2492
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
ms.openlocfilehash: e2b08ef3e46681147c4efd77cbffadb096bbfc16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360715"
---
# <a name="compiler-error-c2492"></a>Error del compilador C2492

'*variable*': los datos con duración de almacenamiento de subproceso no pueden tener una interfaz dll

La variable se declara con el [subproceso](../../cpp/thread.md) de atributo y con el archivo DLL de interfaz. La dirección de la `thread` variable no se conoce hasta el tiempo de ejecución, por lo que no se puede vincular a una DLL importación o exportación.

El ejemplo siguiente genera C2492:

```
// C2492.cpp
// compile with: /c
class C {
public:
   char   ch;
};

__declspec(dllexport) __declspec(thread) C c_1;   // C2492
__declspec(thread) C c_1;   // OK
```