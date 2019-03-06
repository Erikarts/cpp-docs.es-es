---
title: Descargar explícitamente un archivo DLL de carga retrasada
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:UNLOAD linker option
- DELAY:UNLOAD linker option
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 1c4c5172-fd06-45d3-9e4f-f12343176b3c
ms.openlocfilehash: f661694dd791ed8db3cd9f5b72a021c7470d17f3
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420458"
---
# <a name="explicitly-unloading-a-delay-loaded-dll"></a>Descargar explícitamente un archivo DLL de carga retrasada

El [/delay](../../build/reference/delay-delay-load-import-settings.md): opción del vinculador unload le permite descargar un archivo DLL de carga retrasada. De forma predeterminada, cuando el código descarga el archivo DLL (mediante/delay: unload y **__FUnloadDelayLoadedDLL2**), las importaciones de carga retrasada permanecen en la tabla de direcciones de importación (IAT). Sin embargo, si utiliza/Delay: Unload en la línea de comandos del vinculador, la función auxiliar admitirá la descarga explícita de la DLL, restablecer la IAT a su forma original; se sobrescribirán los punteros no son válidos ahora. La tabla IAT es un campo en el [ImgDelayDescr](../../build/reference/calling-conventions-parameters-and-return-type.md) que contiene la dirección de una copia de la tabla IAT original (si existe).

## <a name="example"></a>Ejemplo

### <a name="code"></a>Código

```
// link with /link /DELAYLOAD:MyDLL.dll /DELAY:UNLOAD
#include <windows.h>
#include <delayimp.h>
#include "MyDll.h"
#include <stdio.h>

#pragma comment(lib, "delayimp")
#pragma comment(lib, "MyDll")
int main()
{
    BOOL TestReturn;
    // MyDLL.DLL will load at this point
    fnMyDll();

    //MyDLL.dll will unload at this point
    TestReturn = __FUnloadDelayLoadedDLL2("MyDll.dll");

    if (TestReturn)
        printf_s("\nDLL was unloaded");
    else
        printf_s("\nDLL was not unloaded");
}
```

### <a name="comments"></a>Comentarios

Notas importantes sobre la descarga de un archivo DLL de carga retrasada:

- Puede encontrar la implementación de la **__FUnloadDelayLoadedDLL2** función en el archivo \VC7\INCLUDE\DELAYHLP. CPP.

- El parámetro de nombre de la **__FUnloadDelayLoadedDLL2** función debe coincidir exactamente (incluido el caso) lo que la biblioteca de importación (esa cadena se encuentra también en la tabla de importación en la imagen). Puede ver el contenido de la biblioteca de importación con [/Dependents DUMPBIN](../../build/reference/dependents.md). Si se desea una coincidencia de mayúsculas y minúsculas de cadena, puede actualizar **__FUnloadDelayLoadedDLL2** utilizar una de las funciones de cadena CRT o una llamada de API de Windows.

Consulte [descargar un archivo DLL de carga retrasada](../../build/reference/unloading-a-delay-loaded-dll.md) para obtener más información.

## <a name="see-also"></a>Vea también

[Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)
