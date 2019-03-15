---
title: Error del compilador C3284
ms.date: 11/04/2016
f1_keywords:
- C3284
helpviewer_keywords:
- C3284
ms.assetid: e582f316-e9db-4d27-9c70-fdfa737a9d5f
ms.openlocfilehash: acefcac849b9ce36bcf24d45f3ce85ba220b3698
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807785"
---
# <a name="compiler-error-c3284"></a>Error del compilador C3284

las restricciones del parámetro genérico 'parámetro' de la función 'función' deben coincidir con las restricciones correspondientes al parámetro genérico 'parámetro' de la función 'función'.

Una función genérica virtual debe usar las mismas restricciones que una función virtual con el mismo nombre y conjunto de argumentos de la clase base.

El ejemplo siguiente genera la advertencia C3284:

```
// C3284.cpp
// compile with: /clr /c
// C3284 expected
public interface class IGettable {
   int Get();
};

public interface class B {
   generic<typename T>
   where T : IGettable
   virtual int mf(T t);
};

public ref class D : public B {
public:
   generic<typename T>
   // Uncomment the following line to resolve.
   // where T : IGettable
   virtual int mf(T t) {
      return 4;
   }
};
```