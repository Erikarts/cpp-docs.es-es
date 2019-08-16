---
title: Error del compilador C2696
ms.date: 11/04/2016
f1_keywords:
- C2696
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
ms.openlocfilehash: 340a5d0596160b6c9c7bcfc78aed812f8c5f3fa3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367608"
---
# <a name="compiler-error-c2696"></a>Error del compilador C2696

No se puede crear un objeto temporal de un tipo administrado 'type'

Las referencias a `const` en un programa no administrado que el compilador llame al constructor y cree un objeto temporal en la pila. Sin embargo, nunca puede crearse una clase administrada en la pila.

Solo es accesible a través de la opción del compilador obsoleto C2696 **/CLR: oldSyntax**.
