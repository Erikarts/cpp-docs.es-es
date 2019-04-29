---
title: Error del evaluador de expresiones CXX0022
ms.date: 11/04/2016
f1_keywords:
- CXX0022
helpviewer_keywords:
- CXX0022
- CAN0022
ms.assetid: f6b299ac-a4ee-492c-bd9f-6fff005bc537
ms.openlocfilehash: ac726c60d30a13d6458636d31dda6a8fb2cbd02d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359870"
---
# <a name="expression-evaluator-error-cxx0022"></a>Error del evaluador de expresiones CXX0022

llamada de función antes de _main

El evaluador de expresiones de C no puede evaluar una función antes de que el depurador haya entrado en la función **_main**. No se ha inicializado correctamente el programa hasta **_main** se ha llamado.

Este error es idéntico a CAN0022.