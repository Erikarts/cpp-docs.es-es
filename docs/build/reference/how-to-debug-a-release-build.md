---
title: Filtrar Depurar una versión de lanzamiento
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
ms.openlocfilehash: 61baaa827feb1abcc03a0296574e56c993ce1681
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412567"
---
# <a name="how-to-debug-a-release-build"></a>Filtrar Depurar una versión de lanzamiento

Puede depurar una versión de lanzamiento de una aplicación.

### <a name="to-debug-a-release-build"></a>Para depurar una versión de lanzamiento

1. Abra el **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en el **C o C++** nodo. Establecer **formato de información de depuración** a [compatible con C7 (/ Z7)](../../build/reference/z7-zi-zi-debug-information-format.md) o **base de datos de programa (/Zi)**.

1. Expanda **vinculador** y haga clic en el **General** nodo. Establecer **habilitar vinculación Incremental** a [No (/ INCREMENTAL: NO)](../../build/reference/incremental-link-incrementally.md).

1. Seleccione el **depuración** nodo. Establecer **generar información de depuración** a [Sí (/Debug)](../../build/reference/debug-generate-debug-info.md).

1. Seleccione el **optimización** nodo. Establecer **referencias** a [/OPT: ref](../../build/reference/opt-optimizations.md) y **Habilitar plegamiento de COMDAT** a [/OPT: ICF](../../build/reference/opt-optimizations.md).

1. Ahora puede depurar la aplicación de la compilación de versión. Para detectar un problema, paso a través del código (o la depuración Just-In-Time de uso) hasta que encuentre dónde se produce el error y, a continuación, determine los parámetros incorrectos o código.

   Si una aplicación funciona en una compilación de depuración, pero se produce un error en una versión de lanzamiento, una de las optimizaciones del compilador puede exponer un defecto en el código fuente. Para aislar el problema, deshabilitar las optimizaciones seleccionadas para cada archivo de código fuente hasta encontrar el archivo y la optimización que está causando el problema. (Para acelerar el proceso, puede dividir los archivos en dos grupos, deshabilite la optimización en un grupo y cuando encuentre un problema en un grupo, siga dividiendo hasta aislar el problema al archivo.)

   Puede usar [/RTC](../../build/reference/rtc-run-time-error-checks.md) para intentar exponer este tipo de errores en las compilaciones de depuración.

   Para obtener más información, consulte [optimizar el código](../../build/reference/optimizing-your-code.md).

## <a name="see-also"></a>Vea también

[Solucionar problemas de versiones de lanzamiento](../../build/reference/fixing-release-build-problems.md)
