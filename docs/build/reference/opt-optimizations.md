---
title: /OPT (Optimizaciones)
ms.date: 05/18/2018
f1_keywords:
- VC.Project.VCLinkerTool.OptimizeReferences
- /opt
- VC.Project.VCLinkerTool.OptimizeForWindows98
- VC.Project.VCLinkerTool.EnableCOMDATFolding
- VC.Project.VCLinkerTool.OptimizeFolding
- VC.Project.VCLinkerTool.FoldingIterations
- VC.Project.VCLinkerTool.OptimizeFoldingIterations
helpviewer_keywords:
- LINK tool [C++], controlling optimizations
- -OPT linker option
- linker [C++], optimizations
- OPT linker option
- optimization, linker
- /OPT linker option
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
ms.openlocfilehash: fb59b861bc46c93a3f5fa1b6c6b8d1b73ddefc66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320251"
---
# <a name="opt-optimizations"></a>/OPT (Optimizaciones)

Controla las optimizaciones que efectúa LINK durante una compilación.

## <a name="syntax"></a>Sintaxis

> **/OPT:**{**REF** | **NOREF**}<br/>
> **/OPT:**{**ICF**[**=**_iterations_] | **NOICF**}<br/>
> **/OPT:**{**LBR** | **NOLBR**}

## <a name="arguments"></a>Argumentos

**REF** &#124; **NOREF**

**/ OPT: ref** elimina las funciones y datos que no se hace referencia a nunca; **/OPT: NOREF** conserva los datos que nunca se hace referencia y las funciones.

Cuando está habilitada/OPT: REF, LINK quita las funciones empaquetadas y datos, conocidos como *COMDAT*. Esta optimización se conoce como eliminación transitiva de COMDAT. El **/OPT: ref** opción también deshabilita la vinculación incremental.

Las funciones insertadas y funciones de miembro definidas dentro de una declaración de clase siempre son COMDAT. Todas las funciones en un archivo de objeto se convierten en COMDAT si se ha compilado mediante el uso de la [/Gy](gy-enable-function-level-linking.md) opción. Para colocar **const** datos en comdat, debe declarar mediante `__declspec(selectany)`. Para obtener información sobre cómo especificar los datos para su eliminación o el plegado, consulte [selectany](../../cpp/selectany.md).

De forma predeterminada, **/OPT: ref** está habilitada por el vinculador a menos que **/OPT: NOREF** o [/DEBUG](debug-generate-debug-info.md) se especifica. Para invalidar este comportamiento predeterminado y mantener las funciones COMDAT sin referencias en el programa, especifique **/OPT: NOREF**. Puede usar el [/INCLUDE](include-force-symbol-references.md) opción para reemplazar la eliminación de un símbolo concreto.

Si [/DEBUG](debug-generate-debug-info.md) se especifica, el valor predeterminado para **/OPT** es **NOREF**, y se conservan todas las funciones en la imagen. Para invalidar este comportamiento predeterminado y optimizar una compilación de depuración, especifique **/OPT: ref**. Esto puede reducir el tamaño del archivo ejecutable y puede ser que una optimización útil incluso en modo de depuración se compila. Se recomienda que también especifique **NOICF** conservar idénticos funciona en modo de depuración se compila. De este modo, resulta más fácil consultar los seguimiento de pila y establecer puntos de interrupción en las funciones que, de otro modo, estarían contraídas.

**ICF**\[**=**_iterations_] &#124; **NOICF**

Use **ICF**\[**=**_iteraciones_] para realizar un plegamiento idéntico de COMDAT. Las funciones COMDAT redundantes se pueden quitar de la salida del vinculador. El elemento opcional *iteraciones* parámetro especifica el número de veces que se recorren los símbolos para los duplicados. El número predeterminado de iteraciones es 1. En iteraciones adicionales es posible localizar más duplicados que no se han cubierto mediante el plegamiento de las iteraciones anteriores.

De forma predeterminada, **/OPT: ICF** está habilitada por el vinculador a menos que **NOICF** o [/DEBUG](debug-generate-debug-info.md) se especifica. Para invalidar este comportamiento predeterminado e impedir que las funciones COMDAT se dobla en el programa, especifique **NOICF**.

En una compilación de depuración, debe especificar explícitamente **/OPT: ICF** para habilitar el plegamiento de COMDAT. Sin embargo, dado que **/OPT: ICF** puede combinar funciones o datos idénticos, puede cambiar los nombres de función que aparecen en los seguimientos de pila. También puede hacer que Imposible establecer puntos de interrupción en algunas funciones o examinar algunos datos en el depurador lo que puede podría mostrarle funciones inesperadas al paso a paso a través de su código. El comportamiento del código es idéntico, pero la presentación del depurador puede resultar muy confusa. Por lo tanto, no se recomienda que utilice **/OPT: ICF** en modo de depuración, compilaciones, a menos que estas desventajas superan a las ventajas de un código más pequeño.

> [!NOTE]
> Dado que **/OPT: ICF** puede provocar la misma dirección que se asignará a las distintas funciones o miembros de datos de solo lectura (es decir, **const** variables al compilar con **/Gy**), puede interrumpir un programa que dependa de direcciones únicas para las funciones o miembros de datos de solo lectura. Para obtener más información, consulte [/Gy (Habilitar vinculación en el nivel de función)](gy-enable-function-level-linking.md).

**LBR** &#124; **NOLBR**

El **/OPT:LBR** y **/OPT:NOLBR** opciones se aplican sólo a los archivos binarios ARM. Dado que algunas instrucciones de bifurcación del procesador de ARM tienen un intervalo limitado, si el vinculador detecta un salto a una dirección fuera del intervalo, reemplaza la dirección de destino de la instrucción de bifurcación por la dirección de una "isla" de código que contiene una instrucción de bifurcación que apunta al destino real. Puede usar **/OPT:LBR** para optimizar la detección de instrucciones de bifurcación largas y la posición de islas de código intermedio para minimizar el tamaño total del código. **/OPT:NOLBR** indica al vinculador que genere islas de código para obtener instrucciones de bifurcación largas tal como se encuentren, sin la optimización.

De forma predeterminada, el **/OPT:LBR** opción se establece cuando no está habilitada la vinculación incremental. Especifique si desea un vínculo no incremental pero no las optimizaciones de bifurcación largas, **/OPT:NOLBR**. El **/OPT:LBR** opción deshabilita la vinculación incremental.

## <a name="remarks"></a>Comentarios

Cuando se usa en la línea de comandos, el vinculador tiene como valor predeterminado **LBR/OPT: REF, Firewall de Windows,**. Si **/DEBUG** se especifica, el valor predeterminado es **NOLBR/OPT: NOREF NOICF,**.

El **/OPT** optimizaciones generalmente disminuir el tamaño de imagen y aumentar la velocidad del programa. Estas mejoras pueden ser considerables en programas más grandes, motivo por el que están habilitadas de forma predeterminada para las compilaciones comerciales.

Optimización de vinculador tarda un tiempo adicional por adelantado, pero el código optimizado también ahorra tiempo cuando el vinculador tiene menos reubicaciones corregir y crea una imagen más pequeña final, y se guarda incluso más tiempo cuando tiene menos información de depuración para procesar y escribir en el archivo PDB. Cuando se habilita la optimización, puede producir un tiempo de vinculación más rápido en general, como el pequeño coste adicional en el análisis puede ser más que compensado por el tiempo de ahorro en el vinculador pasa a través de los archivos binarios más pequeños.

El **/OPT** argumentos se pueden especificar juntos, separados por comas. Por ejemplo, en lugar de **/OPT: REF NOICF**, puede especificar **/OPT: REF, NOICF**.

Puede usar el [/VERBOSE](verbose-print-progress-messages.md) opción del vinculador para ver las funciones que se quitan mediante **/OPT: ref** y las funciones que se han plegado mediante **/OPT: ICF**.

El **/OPT** argumentos a menudo se establecen para los proyectos creados mediante el uso de la **nuevo proyecto** cuadro de diálogo en el IDE de Visual Studio, y normalmente tienen valores diferentes para la depuración y la configuración de lanzamiento. Si se establece ningún valor para estas opciones del vinculador en el proyecto, a continuación, puede obtener los valores predeterminados del proyecto, que pueden ser diferentes de los valores predeterminados usados por el enlazador en la línea de comandos.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Para establecer la opción del vinculador OPT:ICF u OPT:REF en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **optimización** página de propiedades.

1. Modifique una de estas propiedades:

   - **Habilitar plegamiento de COMDAT**

   - **Referencias**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Para establecer la opción del vinculador OPT:LBR en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Especifique la opción de **opciones adicionales**:

   `/opt:lbr` o `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea las propiedades <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A>.

## <a name="see-also"></a>Vea también

- [Referencia del enlazador MSVC](linking.md)
- [Opciones del enlazador MSVC](linker-options.md)
