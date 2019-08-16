---
title: Error del evaluador de expresiones CXX0015
ms.date: 11/04/2016
f1_keywords:
- CXX0015
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
ms.openlocfilehash: f73aef18563426d28a81b92b3c37d1b7e345d0d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397151"
---
# <a name="expression-evaluator-error-cxx0015"></a>Error del evaluador de expresiones CXX0015

expresión demasiado compleja (desbordamiento de pila)

La expresión especificado era demasiado compleja o demasiado anidada para almacenamiento disponible para el evaluador de expresiones de C.

Desbordamiento suele producirse debido a demasiados cálculos pendientes.

Reorganice la expresión para que pueda evaluarse cada componente de la expresión que se encuentre, en lugar de tener que esperar a otras partes de la expresión que se va a calcular.

Divida la expresión en varios comandos.

Este error es idéntico a CAN0015.