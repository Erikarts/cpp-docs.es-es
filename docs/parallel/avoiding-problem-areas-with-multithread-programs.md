---
title: Evitar áreas de riesgo en programas multiproceso
ms.date: 11/04/2016
helpviewer_keywords:
- multithreading [C++], troubleshooting
- errors [C++], multithreaded programs
- threading [C++], troubleshooting
- troubleshooting [C++], multithreading
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
ms.openlocfilehash: 3ceae832599243ffa0aad2b6fa67148e7ea30510
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288195"
---
# <a name="avoiding-problem-areas-with-multithread-programs"></a>Evitar áreas de riesgo en programas multiproceso

Hay varios problemas que pueden surgir en crear, vincular o ejecutar un programa multiproceso en C. Algunos de los problemas más comunes se describen en la tabla siguiente. (Para obtener una discusión similar desde el punto de vista MFC, vea [Multithreading: Sugerencias de programación](multithreading-programming-tips.md).)

|Problema|Causa probable|
|-------------|--------------------|
|Obtendrá un cuadro de mensaje que muestra que el programa ha provocado una infracción de la protección.|Muchos errores de programación de Win32 provocar infracciones de protección. Una causa común de las infracciones de protección es la asignación indirecta de datos a punteros null. Debido a esto da como resultado el programa intenta obtener acceso a memoria que no pertenecen a ella, se emite una infracción de la protección.<br /><br /> Una manera fácil de detectar la causa de una infracción de la protección consiste en compilar el programa con información de depuración y, a continuación, ejecútelo mediante el depurador en el entorno de Visual C++. Cuando se produce el error de protección, Windows transfiere el control al depurador y el cursor se coloca en la línea que produjo el problema.|
|El programa genera muchos errores de compilación y vinculación.|Puede eliminar muchos posibles problemas mediante el establecimiento de nivel de advertencia del compilador a uno de sus valores más altos y puesta en marcha de los mensajes de advertencia. Al usar el nivel 3 o las opciones de nivel de advertencia de nivel 4, puede detectar las conversiones de datos accidental, prototipos de función que faltan y uso de características que no sean ANSI.|

## <a name="see-also"></a>Vea también

[Multithreading con C y Win32](multithreading-with-c-and-win32.md)
