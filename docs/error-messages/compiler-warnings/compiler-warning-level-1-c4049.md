---
title: Compilador advertencia (nivel 1) C4049
ms.date: 11/04/2016
f1_keywords:
- C4049
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
ms.openlocfilehash: a4958bb446b5f7e80ef2eef92b52a0f86cf6a134
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388768"
---
# <a name="compiler-warning-level-1-c4049"></a>Compilador advertencia (nivel 1) C4049

límite del compilador: finalizando la emisión de números de línea

El archivo contiene más de 16,777.215 (2<sup>24</sup>-1) líneas de código fuente. El compilador detiene la numeración en 16,777.215.

Para el código después de la línea 16,777.215:

- La imagen no contendrá ninguna información de depuración para los números de línea.

- Algunos diagnósticos pueden presentar con números de línea incorrecto.

- listas de .asm (/ FAs) pueden tener números de línea incorrecto.