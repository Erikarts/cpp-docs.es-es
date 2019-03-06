---
title: Variables de entorno de CL
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 47d6966cdc821cee4bd9ffd61b36c0c79143b6c2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412463"
---
# <a name="cl-environment-variables"></a>Variables de entorno de CL

La herramienta CL usa las siguientes variables de entorno:

- CL y \_CL\_, si ha definido. La herramienta CL antepone las opciones y argumentos definidos en la variable de entorno de CL a los argumentos de línea de comandos y anexa las opciones y argumentos definan en \_CL\_, antes del procesamiento.

- INCLUDE, que debe señalar al subdirectorio \include de la instalación de Visual C++.

- LIBPATH, que especifica los directorios donde buscar archivos de metadatos al que hace referencia con [#using](../../preprocessor/hash-using-directive-cpp.md). Para obtener más información sobre LIBPATH, vea `#using`.

Puede establecer la CL o \_CL\_ variable de entorno mediante la sintaxis siguiente:

> ESTABLECER CL = [[*opción*]... [*archivo*]...] [/ link *vínculo-opt* ...] ESTABLECER \_CL\_= [[*opción*]... [*archivo*]...] [/ link *vínculo-opt* ...]

Para obtener más información sobre los argumentos de la CL y \_CL\_ las variables de entorno, vea [sintaxis de línea de comandos del compilador](../../build/reference/compiler-command-line-syntax.md).

Puede usar estas variables de entorno para definir los archivos y las opciones que usa con más frecuencia, y puede usar la línea de comandos para definir archivos y opciones específicos para fines específicos. La CL y \_CL\_ variables de entorno están limitadas a 1024 caracteres (el límite de entrada de línea de comandos).

No puede usar la opción /D para definir un símbolo que use un signo igual (=). Puede sustituir el signo de número (#) por un signo igual. De este modo, puede usar el CL o \_CL\_ variables de entorno para definir constantes de preprocesador con valores explícitos, por ejemplo, `/DDEBUG#1` para definir `DEBUG=1`.

Para obtener información relacionada, consulte [establecer Variables de entorno](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Ejemplos

Este es un ejemplo de configuración de la variable de entorno de CL:

> SET CL=/Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ

Cuando se establece esta variable de entorno, si escribe `CL INPUT.C` en la línea de comandos, este es el comando eficaz:

> CL /Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ INPUT.C

En el ejemplo siguiente, un comando de CL sin formato compila los archivos de código fuente FILE1.c y FILE2.c y, a continuación, vincula los archivos objeto FILE1.obj, FILE2.obj y FILE3.obj:

> CONJUNTO DE CL = FILE1. C FILE2. SET C \_CL\_= FILE3. CL OBJ

Esto tiene el mismo efecto que la línea de comandos siguiente:

> CL FILE1.C FILE2.C FILE3.OBJ

## <a name="see-also"></a>Vea también

[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)
