---
title: Nombres de entorno
ms.date: 11/04/2016
ms.assetid: 9af409a5-e724-465a-9a21-88d3586c2e92
ms.openlocfilehash: 43e1254b4c1ee61a92fbb6499d9396e8b15a3047
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234132"
---
# <a name="environment-names"></a>Nombres de entorno

**ANSI 4.10.4.4** El conjunto de nombres de entorno y el método para modificar la lista de entorno utilizada por la función [getenv](../c-runtime-library/reference/getenv-wgetenv.md)

El conjunto de nombres de entorno es ilimitado.

Para cambiar las variables de entorno desde un programa de C, se debe llamar a la función [_putenv](../c-runtime-library/reference/putenv-wputenv.md). Para cambiar variables de entorno desde la línea de comandos de Windows, utilice el comando SET (por ejemplo, SET LIB = D: LIBS).

Las variables de entorno establecidas desde un programa de C solo existen mientras la copia del host del shell de comandos del sistema operativo está ejecutando (CMD.EXE o COMMAND.COM). Por ejemplo, la línea

```
system( SET LIB = D:\LIBS );
```

ejecutaría una copia del shell de comandos (CMD.EXE), establecería la variable de entorno LIB y volvería al programa de C, saliendo de la copia secundaria de CMD.EXE. Cuando se sale de esa copia de CMD.EXE, se quita la variable de entorno temporal LIB.

Igualmente, los cambios realizados por la función `_putenv` solo duran hasta que el programa finaliza.

## <a name="see-also"></a>Vea también

[Funciones de la biblioteca](../c-language/library-functions.md)<br/>
[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)
