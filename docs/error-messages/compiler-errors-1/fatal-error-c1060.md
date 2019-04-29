---
title: Error irrecuperable C1060
ms.date: 11/04/2016
f1_keywords:
- C1060
helpviewer_keywords:
- C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
ms.openlocfilehash: 876ae7a368d2d1a1ee94a04fc9ecf50d0f4b8d78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364238"
---
# <a name="fatal-error-c1060"></a>Error irrecuperable C1060

espacio de montón insuficiente en el compilador

El sistema operativo o la biblioteca en tiempo de ejecución no pueden satisfacer una solicitud de memoria.

### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>Para corregir este error pruebe las siguientes soluciones

1. Si el compilador también emite errores [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) y [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md), utilice el [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) opción del compilador para reducir el límite de asignación de memoria. Habrá más espacio de montón disponible para la aplicación si reduce la asignación de memoria restante.

   Si el [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) ya está establecida, pruebe a quitarla. El espacio de montón podría agotarse si el límite de asignación de memoria especificado en la opción es demasiado alto. El compilador utilizará un límite predeterminado si quita el [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) opción.

1. Si está compilando en una plataforma de 64 bits, utilice el conjunto de herramientas del compilador de 64 bits. Para obtener información, vea [Cómo: Habilitar un Toolset de 64 bits Visual C++ en la línea de comandos](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. En Windows de 32 bits, pruebe a usar el [/3 GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) conmutador de boot.ini.

1. Aumente el tamaño del archivo de intercambio de Windows.

1. Cierre los demás programas que se estén ejecutando.

1. Elimine los archivos de inclusión innecesarios.

1. Elimine las variables globales que no son necesarias, por ejemplo, asignando memoria dinámicamente, en lugar de declarar una matriz grande.

1. Elimine las declaraciones que no utilice.

9. Divida el archivo actual en archivos más pequeños.