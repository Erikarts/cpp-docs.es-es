---
title: Instrucciones de iteración (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
ms.openlocfilehash: 72f81e2fc58a31db0c4cd3f77ba182bd8b8152a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366581"
---
# <a name="iteration-statements-c"></a>Instrucciones de iteración (C++)

Las instrucciones de iteración producen instrucciones (o instrucciones compuestas) que se ejecutarán cero o más veces, según determinados criterios de la finalización de bucle. Cuando estas instrucciones son instrucciones compuestas, se ejecutan en orden, excepto cuando ya sea el [salto](../cpp/break-statement-cpp.md) instrucción o el [continuar](../cpp/continue-statement-cpp.md) se encuentra la instrucción.

C++ proporciona cuatro instrucciones de iteración: [mientras](../cpp/while-statement-cpp.md), [hacer](../cpp/do-while-statement-cpp.md), [para](../cpp/for-statement-cpp.md), y [basada en intervalo para](../cpp/range-based-for-statement-cpp.md). Cada uno de estos se repite hasta que la expresión de finalización se evalúa como cero (false), o hasta que se fuerza la finalización de bucle con un **salto** instrucción. En la tabla siguiente se resumen estas instrucciones y sus acciones; cada una se explica detalladamente en las secciones siguientes.

### <a name="iteration-statements"></a>Instrucciones de iteración

|Instrucción|Se evalúa en|Inicialización|Incremento|
|---------------|------------------|--------------------|---------------|
|**while**|Principio del bucle|No|No|
|**do**|Final del bucle|No|No|
|**for**|Principio del bucle|Sí|Sí|
|**en función de rangos para**|Principio del bucle|Sí|Sí|

La parte de instrucción de una instrucción de iteración no puede ser una declaración. Sin embargo, puede ser una instrucción compuesta que contenga una declaración.

## <a name="see-also"></a>Vea también

[Información general sobre las instrucciones de C++](../cpp/overview-of-cpp-statements.md)