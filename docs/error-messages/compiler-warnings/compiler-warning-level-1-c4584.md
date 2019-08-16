---
title: Advertencia del compilador (nivel 1) C4584
ms.date: 11/04/2016
f1_keywords:
- C4584
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
ms.openlocfilehash: 3c60575e766ea3490a40711fe26c3e402c41fbdd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397255"
---
# <a name="compiler-warning-level-1-c4584"></a>Advertencia del compilador (nivel 1) C4584

'class1': clase base 'clase2' ya es una clase base de 'Clase3'

La clase definida se hereda de dos clases, uno de los cuales hereda de la otra. Por ejemplo:

```
// C4584.cpp
// compile with: /W1 /LD
class A {
};

class B : public A {
};

class C : public A, public B { // C4584
};
```

En este caso, podría generarse una advertencia en la clase C, ya que hereda de una clase y clase B, que también se hereda de la clase A. Esta advertencia sirve como recordatorio de que debe calificar totalmente el uso de los miembros de estas clases base o se generará un error del compilador debido a la ambigüedad en cuanto a qué miembro de clase se hace referencia.