---
title: Advertencia del compilador (nivel 1) C4407
ms.date: 11/04/2016
f1_keywords:
- C4407
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
ms.openlocfilehash: 2e47e293b650f64d2a6be91a837cc4195e073e8f
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447746"
---
# <a name="compiler-warning-level-1-c4407"></a>Advertencia del compilador (nivel 1) C4407

conversión entre diferentes representaciones de puntero a miembro, el compilador puede generar código incorrecto

Se detectó una conversión incorrecta.

C4407 pueden generarse debido a la del trabajo de conformidad del compilador efectuado en Visual Studio 2005. Puntero a miembro ahora requiere un nombre completo y el operador address-of (&).

C4407 puede producirse si puede convertir entre un varios herencia puntero a miembro a un herencia simple puntero a miembro. A veces esto puede funcionar, pero a veces no puede porque la representación de puntero a miembro de herencia única no contiene información suficiente. Compilar con la **/VMM** podría ayudar a (para obtener más información, consulte [/VMM, / VMs, /vmv (representación de propósito General)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)). También puede intentar volver a organizar las clases base. el compilador detecta una pérdida de información en la conversión porque es una clase base con un desplazamiento distinto de cero de la clase derivada.

El ejemplo siguiente genera la advertencia C4407:

```
// C4407.cpp
// compile with: /W1 /c
struct C1 {};
struct C2 {};
struct C3 : C1, C2 {};

typedef void(C3::*PMF_C3)();
typedef void(C2::*PMF_C2)();

PMF_C2 f1(PMF_C3 pmf) {
   return (PMF_C2)pmf;   // C4407, change type of cast,
   // or reverse base class inheritance of C3 (i.e. : C2, C1)
}
```