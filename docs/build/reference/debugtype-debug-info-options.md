---
title: /DEBUGTYPE (Opciones de información de depuración)
ms.date: 11/04/2016
f1_keywords:
- /debugtype
helpviewer_keywords:
- /DEBUGTYPE linker option
- DEBUGTYPE linker option
- -DEBUGTYPE linker option
ms.assetid: 1ddcb718-7fec-4f92-a319-3f70f04fe742
ms.openlocfilehash: 00e3cb61f8ec9aa707bb72aa9ff05a64f98d4e47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272300"
---
# <a name="debugtype-debug-info-options"></a>/DEBUGTYPE (Opciones de información de depuración)

La opción /DEBUGTYPE especifica los tipos de información de depuración generados por la opción /DEBUG.

```
/DEBUGTYPE:[CV | PDATA | FIXUP]
```

## <a name="arguments"></a>Argumentos

**CV**<br/>
Indica al enlazador que emita la información de depuración de símbolos, números de línea y demás información de compilación de objetos en el archivo PDB. De forma predeterminada, esta opción está habilitada cuando **/DEBUG** se especifica y **/DEBUGTYPE** no se especifica.

**PDATA**<br/>
Indica al enlazador que agregue entradas .pdata y .xdata a la información de flujo de depuración en el archivo PDB. De forma predeterminada, esta opción está habilitada cuando tanto el **/DEBUG** y **/DRIVER** se especifican opciones. Si **/DEBUGTYPE:PDATA** se especifica por sí mismo, el enlazador incluye automáticamente símbolos de depuración en el archivo PDB. Si **/DEBUGTYPE:PDATA, corrección** se especifica, el enlazador no incluye símbolos de depuración en el archivo PDB.

**FIXUP**<br/>
Indica al enlazador que agregue entradas de la tabla de reubicación a la información de flujo de depuración en el archivo PDB. De forma predeterminada, esta opción está habilitada cuando tanto el **/DEBUG** y **/PROFILE** se especifican opciones. Si **/DEBUGTYPE:FIXUP** o **/DEBUGTYPE:FIXUP, PDATA** se especifica, el enlazador no incluye símbolos de depuración en el archivo PDB.

Argumentos de **/DEBUGTYPE** se pueden combinar en cualquier orden separándolos con una coma. El **/DEBUGTYPE** opción y sus argumentos no distinguen mayúsculas de minúsculas.

## <a name="remarks"></a>Comentarios

Use la **/DEBUGTYPE** opción para especificar la inclusión de información de encabezado de datos o .pdata y .xdata para la tabla de reubicación en el flujo de depuración. Esto hace que el enlazador incluya información sobre el código de modo de usuario que está visible en un depurador de kernel cuando se produce una interrupción en el código en modo kernel. Para que los símbolos de depuración estén disponibles cuando **corrección** está especificado, incluya el **CV** argumento.

Para depurar el código en modo de usuario, que es típico para las aplicaciones, el **/DEBUGTYPE** opción no es necesario. De forma predeterminada, los modificadores de compilador que especifican la depuración de salida ([/Z7, / Zi, /ZI](z7-zi-zi-debug-information-format.md)) emiten toda la información necesaria de Visual Studio del depurador. Use **/DEBUGTYPE:PDATA** o **/, PDATA, corrección DEBUGTYPE: CV** para depurar el código que combina los componentes de modo de usuario y modo de núcleo, por ejemplo, una aplicación de configuración para un controlador de dispositivo. Para obtener más información acerca de los depuradores de modo kernel, vea [depuración herramientas para Windows (WinDbg, KD, CDB, NTSD)](/windows-hardware/drivers/debugger/index)

## <a name="see-also"></a>Vea también

[/DEBUG (Generar información de depuración)](debug-generate-debug-info.md)<br/>
[/DRIVER (Controlador de modo kernel de Windows NT)](driver-windows-nt-kernel-mode-driver.md)<br/>
[/PROFILE (Generador de perfiles de Herramientas de rendimiento)](profile-performance-tools-profiler.md)<br/>
[Herramientas de depuración para Windows (WinDbg, KD, CDB, NTSD)](/windows-hardware/drivers/debugger/index)
