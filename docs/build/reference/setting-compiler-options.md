---
title: Establecer las opciones del compilador
ms.date: 11/04/2016
helpviewer_keywords:
- compiler options, setting
- cl.exe compiler, setting options
ms.assetid: 4b079f5b-0017-4124-aad6-0d2b58e427e0
ms.openlocfilehash: cc1d4a4a6c782a8ec07cfebfc1905f3c3f8872cf
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416298"
---
# <a name="setting-compiler-options"></a>Establecer las opciones del compilador

Las opciones del compilador de C y C++ pueden definirse en el entorno de desarrollo o en la línea de comandos.

## <a name="in-the-development-environment"></a>En el entorno de desarrollo

Puede establecer opciones del compilador para cada proyecto en su **páginas de propiedades** cuadro de diálogo. En el panel izquierdo, seleccione **propiedades de configuración**, **C o C++** y, a continuación, elija la categoría de opción del compilador. En el tema de cada opción del compilador se describe cómo puede definirse y dónde se encuentra en el entorno de desarrollo. Consulte [opciones del compilador](../../build/reference/compiler-options.md) para obtener una lista completa.

## <a name="outside-the-development-environment"></a>Fuera del entorno de desarrollo

Las opciones del compilador (CL.exe) pueden definirse:

- [En la línea de comandos](../../build/reference/compiler-command-line-syntax.md)

- [En los archivos de comandos](../../build/reference/cl-command-files.md)

- [En la variable de entorno de CL](../../build/reference/cl-environment-variables.md)

Las opciones especificadas en la variable de entorno de CL se usan cada vez que se invoca CL. Si se menciona un archivo de comandos en la variable de entorno de CL o en la línea de comandos, se usarán las opciones especificadas en dicho archivo. A diferencia de la línea de comandos o la variable de entorno de CL, un archivo de comandos permite utilizar varias líneas de opciones y nombres de archivo.

Las opciones del compilador se procesan "de izquierda a derecha" y, si se detecta un conflicto, tiene prioridad la última opción (la que está situada más a la derecha). La variable de entorno de CL se procesa antes que la línea de comandos, por lo que siempre tendrá prioridad en caso de conflicto con la línea de comandos.

## <a name="additional-compiler-topics"></a>Temas adicionales relacionados con el compilador

- [Compilación rápida](../../build/reference/fast-compilation.md)

- [CL invoca el vinculador](../../build/reference/cl-invokes-the-linker.md)

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)
