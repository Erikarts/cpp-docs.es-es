---
title: Error en tiempo de ejecución de C R6030
ms.date: 11/04/2016
f1_keywords:
- R6030
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
ms.openlocfilehash: 7f5c61d9b39b1d655bcbf3d42ea870370ddf2842
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400024"
---
# <a name="c-runtime-error-r6030"></a>Error en tiempo de ejecución de C R6030

CRT no inicializado

> [!NOTE]
> Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema interno. Este problema suele deberse algunos programas de software de seguridad o con poca frecuencia, por un error en el programa.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - El software de seguridad puede tener instrucciones específicas para mitigar este problema. Compruebe el sitio Web de su proveedor de software de seguridad para obtener más información. Como alternativa, busque las versiones actualizadas de su software de seguridad o pruebe el software de seguridad diferente.
> - Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> - Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este error se produce si está usando el tiempo de ejecución de C (CRT), pero no se ha ejecutado el código de inicio de CRT. Es posible obtener este error si el modificador de vinculador [/Entry](../../build/reference/entry-entry-point-symbol.md) se usa para invalidar el valor predeterminado a partir de direcciones, normalmente **mainCRTStartup**, **wmainCRTStartup** para un consola EXE, **WinMainCRTStartup** o **wWinMainCRTStartup** para un archivo EXE de Windows, o **_DllMainCRTStartup** para un archivo DLL. A menos que se llama a uno de las funciones anteriores al inicio, el tiempo de ejecución de C no se inicializarán. Estas funciones de inicio normalmente se denominan de forma predeterminada, al vincular a la biblioteca en tiempo de ejecución de C y usar el valor normal a **principal**, **wmain**, **WinMain**, o  **DllMain** puntos de entrada.

También es posible obtener este error cuando otro programa usa técnicas de inyección de código para interceptar ciertas llamadas de biblioteca DLL. Algunos programas de seguridad intrusivo utilizan esta técnica. En las versiones de Visual C++ antes de Visual Studio 2015, es posible usar una biblioteca de CRT vinculado estáticamente para solucionar el problema, pero esto no se recomienda por motivos de seguridad y aplicación de actualizaciones. Cómo corregir este problema puede requerir la acción del usuario final.