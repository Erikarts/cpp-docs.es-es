---
title: /volatile (interpretación de la palabra clave volatile)
ms.date: 11/04/2016
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
ms.openlocfilehash: 02871622242930d7419fda16f4d106fccb2056f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316644"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (interpretación de la palabra clave volatile)

Especifica cómo el [volátil](../../cpp/volatile-cpp.md) palabra clave es que interpretarse.

## <a name="syntax"></a>Sintaxis

> **/ volatile:**{**iso**|**ms**}

## <a name="arguments"></a>Argumentos

**/volatile:iso**<br/>
Selecciona strict `volatile` semántica como se define en el lenguaje estándar ISO C++. Adquisición y liberación de semántica no se garantiza en accesos volátiles. Si el compilador tiene como destino ARM, se trata de la interpretación predeterminada de `volatile`.

**/volatile:ms**<br/>
Selecciona extendidas de Microsoft `volatile` semántica, que agrega garantías más allá del lenguaje C++ estándar de ISO de ordenación de memoria. Adquisición o liberación de semántica se garantiza en accesos volátiles. Sin embargo, esta opción también hace que el compilador genere barreras de memoria de hardware, lo que podrían producir una sobrecarga significativa en ARM y otras arquitecturas de ordenación de memoria débiles. Si el compilador tiene como destino cualquier plataforma excepto la ARM, ésta es la interpretación predeterminada de `volatile`.

## <a name="remarks"></a>Comentarios

Se recomienda encarecidamente que utilice **/volatile: ISO** junto con primitivos explícitos de sincronización y funciones intrínsecas del compilador al tratar con memoria compartida entre subprocesos. Para obtener más información, consulte [volátil](../../cpp/volatile-cpp.md).

Si el código existente o cambiar esta opción en medio de un proyecto, puede ser útil habilitar la advertencia [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) para identificar las ubicaciones de código que se ven afectadas por la diferencia semántica.

No hay ningún `#pragma` equivalente para controlar esta opción.

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>Para establecer el /volatile opción del compilador en Visual Studio

1. Abra el **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. En el **opciones adicionales** , agregue **/volatile: ISO** o **/volatile: MS** y, a continuación, elija **Aceptar** o **aplicar** para guardar los cambios.

## <a name="see-also"></a>Vea también

[volatile](../../cpp/volatile-cpp.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
