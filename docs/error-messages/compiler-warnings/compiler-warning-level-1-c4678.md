---
title: Advertencia del compilador (nivel 1) C4678
ms.date: 11/04/2016
f1_keywords:
- C4678
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
ms.openlocfilehash: 9e61d919f08bbbf4f3e74da7ba4f2388516d3152
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374526"
---
# <a name="compiler-warning-level-1-c4678"></a>Advertencia del compilador (nivel 1) C4678

la clase base 'base_type' es menos accesible que 'derived_type'

Un tipo público se deriva de un tipo privado. Si se crea una instancia del tipo público en un ensamblado al que se ha hecho referencia, los miembros del tipo base privado no estarán accesibles.

Solo es accesible a través de la opción del compilador obsoleto C4678 **/CLR: oldSyntax**. Es un error al usar **/CLR**, para que tenga una clase base que es menos accesible que su clase derivada.
