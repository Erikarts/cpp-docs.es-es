---
title: Comandos en un archivo MAKE
ms.date: 11/04/2016
helpviewer_keywords:
- commands, makefiles
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
ms.openlocfilehash: 8b640e8a7a1773e69792453de6cb70bcb09c988f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668239"
---
# <a name="commands-in-a-makefile"></a>Comandos en un archivo MAKE

Una regla de inferencia o bloques de descripción Especifica un bloque de comandos que se ejecutarán si la dependencia no está actualizada. NMAKE muestra cada comando antes de ejecutarlo, a menos que/s, **. SILENCIOSA**, **! CMDSWITCHES**, o \@ se utiliza. NMAKE busca una regla de inferencia coincidente si un bloque de descripción no va seguido de un bloque de comandos.

Un bloque de comandos contiene uno o más comandos, cada uno en su propia línea. Ninguna línea en blanco puede aparecer entre la dependencia o la regla y el bloque de comandos. Sin embargo, puede aparecer una línea que contiene solo espacios o tabulaciones; Esta línea se interpreta como un comando null y se produce ningún error. Se permiten las líneas en blanco entre las líneas de comandos.

Una línea de comandos comienza con uno o más espacios o tabulaciones. Una barra inversa (\) seguida por un carácter de nueva línea se interpreta como un espacio en el comando; Use una barra diagonal inversa al final de una línea para continuar un comando en la línea siguiente. NMAKE interpreta la barra diagonal inversa literalmente si cualquier otro carácter, incluido un espacio o tabulación, sigue a la barra diagonal inversa.

Un comando precedido por un punto y coma (;) puede aparecer en una regla de inferencia o línea de dependencia, si sigue un bloque de comandos:

```
project.obj : project.c project.h ; cl /c project.c
```

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

[Modificadores de comandos](../build/command-modifiers.md)

[Sintaxis de partes del nombre de archivo](../build/filename-parts-syntax.md)

[Archivos insertados en un archivo MAKE](../build/inline-files-in-a-makefile.md)

## <a name="see-also"></a>Vea también

[Referencia de NMAKE](../build/nmake-reference.md)