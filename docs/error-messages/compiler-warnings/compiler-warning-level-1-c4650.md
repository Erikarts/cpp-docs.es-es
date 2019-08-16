---
title: Advertencia del compilador (nivel 1) C4650
ms.date: 11/04/2016
f1_keywords:
- C4650
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
ms.openlocfilehash: ea3f1b6e792239692960e74c8360c6c3a1323815
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393537"
---
# <a name="compiler-warning-level-1-c4650"></a>Advertencia del compilador (nivel 1) C4650

información de depuración no está en el encabezado precompilado; solo símbolos globales del encabezado estará disponibles

No se compiló el archivo de encabezado precompilado con información de depuración simbólica de Microsoft.

Cuando vincula, el archivo de biblioteca de vínculos dinámicos o ejecutable resultante no incluirá información de depuración para los símbolos locales contenidos en el encabezado precompilado.

Esta advertencia puede evitarse volviendo a compilar el archivo de encabezado precompilado con la [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) opción de línea de comandos.