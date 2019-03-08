---
title: Rutinas de depuración
ms.date: 04/10/2018
f1_keywords:
- c.debug
helpviewer_keywords:
- debugging [CRT], using macros
- macros, debugging with
- debug routines
- debug macros
- debugging [CRT], runtime routines
ms.assetid: cb4d2664-10f3-42f7-a516-595558075471
ms.openlocfilehash: e1281b578435086dc7de04c7962145c2b265277a
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51329474"
---
# <a name="debug-routines"></a>Rutinas de depuración

La versión de depuración de la biblioteca en tiempo de ejecución de C ofrece muchos servicios de diagnóstico que facilitan la depuración de programas y permiten a los desarrolladores:

- Usar directamente funciones en tiempo de ejecución durante la depuración

- Resolver aserciones, errores y excepciones

- Realizar el seguimiento de las asignaciones del montón y evitar pérdidas de memoria

- Proporcionar mensajes de depuración al usuario

## <a name="debug-versions-of-the-c-runtime-library-routines"></a>Versiones de depuración de las rutinas de la biblioteca en tiempo de ejecución de C

Para usar estas rutinas es necesario definir la marca [_DEBUG](../c-runtime-library/debug.md). Todas estas rutinas no hacen nada en una compilación comercial de una aplicación. Para obtener más información sobre cómo usar las nuevas rutinas de depuración, consulte [Técnicas de depuración de CRT](/visualstudio/debugger/crt-debugging-techniques).

|Rutina|Uso|
|-------------|---------|
|[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Evalúa una expresión y genera un informe de depuración cuando el resultado es FALSE|
|[_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Parecida a **_ASSERT**, pero incluye la expresión del error en el informe generado|
|[_CrtCheckMemory](../c-runtime-library/reference/crtcheckmemory.md)|Confirma la integridad de los bloques de memoria asignados en el montón de depuración|
|[_CrtDbgBreak](../c-runtime-library/reference/crtdbgbreak.md)|Establece un punto de interrupción|
|[_CrtDbgReport, _CrtDbgReportW](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)|Genera un informe de depuración con un mensaje de usuario y envía el informe a tres destinos posibles|
|[_CrtDoForAllClientObjects](../c-runtime-library/reference/crtdoforallclientobjects.md)|Llama a una función suministrada por la aplicación para todos los tipos de **_CLIENT_BLOCK** del montón|
|[_CrtDumpMemoryLeaks](../c-runtime-library/reference/crtdumpmemoryleaks.md)|Vuelca todos los bloques de memoria del montón de depuración cuando se ha producido una fuga de memoria significativa|
|[_CrtIsMemoryBlock](../c-runtime-library/reference/crtismemoryblock.md)|Comprueba que un bloque de memoria especificado está en el montón local y que tiene un identificador válido de tipo de bloque de montón de depuración|
|[_CrtIsValidHeapPointer](../c-runtime-library/reference/crtisvalidheappointer.md)|Comprueba que un puntero especificado está en el montón local|
|[_CrtIsValidPointer](../c-runtime-library/reference/crtisvalidpointer.md)|Comprueba que un intervalo de memoria especificado es válido para lectura y escritura|
|[_CrtMemCheckpoint](../c-runtime-library/reference/crtmemcheckpoint.md)|Obtiene el estado actual del montón de depuración y lo almacena en una estructura de **_CrtMemState** proporcionada por la aplicación|
|[_CrtMemDifference](../c-runtime-library/reference/crtmemdifference.md)|Compara si dos estados de memoria tienen diferencias significativas y devuelve los resultados|
|[_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md)|Vuelca la información sobre objetos del montón desde que se tomó un punto de comprobación especificado o desde que se empezó a ejecutar el programa|
|[_CrtMemDumpStatistics](../c-runtime-library/reference/crtmemdumpstatistics.md)|Vuelca la información de encabezado de depuración para un estado de memoria especificado con un formato legible para el usuario|
|[_CrtReportBlockType](../c-runtime-library/reference/crtreportblocktype.md)|Devuelve el tipo o subtipo de bloque asociado a un puntero de bloque especificado del montón de depuración.|
|[_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md)|Instala una función de asignación definida por el cliente enlazándola al proceso de asignación de memoria de depuración en tiempo de ejecución de C|
|[_CrtSetBreakAlloc](../c-runtime-library/reference/crtsetbreakalloc.md)|Establece un punto de interrupción en un número de orden especificado de la asignación de objetos|
|[_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md)|Recupera o modifica el estado de la marca **_crtDbgFlag** para controlar el comportamiento de asignación del administrador del montón de depuración|
|[_CrtSetDumpClient](../c-runtime-library/reference/crtsetdumpclient.md)|Instala una función definida por la aplicación a la que se llama cada vez que se llama a una función de volcado de depuración para volcar los bloques de memoria de tipo **_CLIENT_BLOCK**|
|[_CrtSetReportFile](../c-runtime-library/reference/crtsetreportfile.md)|Identifica el archivo o la secuencia que se va a usar como destino de un tipo de informe concreto mediante **_CrtDbgReport**|
|[_CrtSetReportHook](../c-runtime-library/reference/crtsetreporthook.md)|Instala una función de creación de informes definida por el cliente enlazándola al proceso de creación de informes de depuración en tiempo de ejecución de C|
|[_CrtSetReportHook2, _CrtSetReportHookW2](../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)|Instala o desinstala una función de generación de informes definida por el cliente enlazándola al proceso de creación de informes de depuración en tiempo de ejecución de C|
|[_CrtSetReportMode](../c-runtime-library/reference/crtsetreportmode.md)|Especifica los destinos generales de un tipo específico de informe generado por **_CrtDbgReport**|
|[_RPT&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|Realiza el seguimiento del progreso de la aplicación al generar un informe de depuración mediante una llamada a **_CrtDbgReport** con una cadena de formato y un número variable de argumentos. No proporciona información sobre el archivo de código fuente y el número de línea.|
|[_RPTF&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|Es parecida a las macros de **_RPTn**, pero proporciona el nombre del archivo de código fuente y el número de línea donde se originó la solicitud de informe|
|[_calloc_dbg](../c-runtime-library/reference/calloc-dbg.md)|Asigna un número especificado de bloques de memoria del montón con espacio adicional para un encabezado de depuración y búferes de sobrescritura|
|[_expand_dbg](../c-runtime-library/reference/expand-dbg.md)|Cambia el tamaño de un bloque de memoria especificado del montón, expandiendo o contrayendo el bloque|
|[_free_dbg](../c-runtime-library/reference/free-dbg.md)|Libera un bloque de memoria del montón|
|[_fullpath_dbg, _wfullpath_dbg](../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md)|Crea un nombre de ruta de acceso absoluta o completa para el nombre de ruta de acceso relativa especificado, usando [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) para asignar memoria.|
|[_getcwd_dbg, _wgetcwd_dbg](../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md)|Obtiene el directorio de trabajo actual, usando [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) para asignar memoria.|
|[_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md)|Asigna un bloque de memoria del montón con espacio adicional para un encabezado de depuración y búferes de sobrescritura|
|[_msize_dbg](../c-runtime-library/reference/msize-dbg.md)|Calcula el tamaño de un bloque de memoria del montón|
|[_realloc_dbg](../c-runtime-library/reference/realloc-dbg.md)|Reasigna un bloque de memoria especificado en el montón, para lo que lo mueve o lo cambia de tamaño|
|[_strdup_dbg, _wcsdup_dbg](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md)|Duplica una cadena, usando [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) para asignar memoria.|
|[_tempnam_dbg, _wtempnam_dbg](../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md)|Genera nombres que se pueden usar para crear archivos temporales, usando [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) para asignar memoria.|

## <a name="c-runtime-routines-that-are-not-available-in-source-code-form"></a>Rutinas en tiempo de ejecución de C no disponibles en formato de código fuente

El depurador se puede usar para recorrer el código fuente de la mayoría de rutinas en tiempo de ejecución de C durante el proceso de depuración. No obstante, Microsoft considera que alguna tecnología es de su propiedad y, por consiguiente, no proporciona el código fuente de un subconjunto de estas rutinas. La mayoría de estas rutinas pertenecen a los grupos de control de excepciones o de procesamiento de punto flotante, pero también se incluyen algunas otras. En la siguiente tabla se enumeran estas rutinas.

||||
|-|-|-|
|[acos](../c-runtime-library/reference/acos-acosf-acosl.md)|[acosh](../c-runtime-library/reference/acosh-acoshf-acoshl.md)|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|
|[asinh](../c-runtime-library/reference/asinh-asinhf-asinhl.md)|[atan, atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[atanh](../c-runtime-library/reference/atanh-atanhf-atanhl.md)|
|[Funciones Bessel](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|[_cabs](../c-runtime-library/reference/cabs.md)|[ceil](../c-runtime-library/reference/ceil-ceilf-ceill.md)|
|[_chgsign](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|[_clear87, _clearfp](../c-runtime-library/reference/clear87-clearfp.md)|[_control87, _controlfp](../c-runtime-library/reference/control87-controlfp-control87-2.md)|
|[copysign](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|[cos](../c-runtime-library/reference/cos-cosf-cosl.md)|[cosh](../c-runtime-library/reference/cosh-coshf-coshl.md)|
|[Exp](../c-runtime-library/reference/exp-expf.md)|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[_finite](../c-runtime-library/reference/finite-finitef.md)|
|[floor](../c-runtime-library/reference/floor-floorf-floorl.md)|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[_fpclass](../c-runtime-library/reference/fpclass-fpclassf.md)|
|[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|[_fpreset](../c-runtime-library/reference/fpreset.md)|[frexp](../c-runtime-library/reference/frexp.md)|
|[_hypot](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|[_isnan](../c-runtime-library/reference/isnan-isnan-isnanf.md)|[ldexp](../c-runtime-library/reference/ldexp.md)|
|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[_logb](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|
|[longjmp](../c-runtime-library/reference/longjmp.md)|[_matherr](../c-runtime-library/reference/matherr.md)|[modf](../c-runtime-library/reference/modf-modff-modfl.md)|
|[_nextafter](../c-runtime-library/reference/nextafter-functions.md)|[pow](../c-runtime-library/reference/pow-powf-powl.md)|[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|
|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[_scalb](../c-runtime-library/reference/scalb.md)|[scanf_s](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|
|[scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)|[setjmp](../c-runtime-library/reference/setjmp.md)|[sin](../c-runtime-library/reference/sin-sinf-sinl.md)|
|[sinh](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|[_status87, _statusfp](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|
|[tan](../c-runtime-library/reference/tan-tanf-tanl.md)|[tanh](../c-runtime-library/reference/tanh-tanhf-tanhl.md)||

Aunque hay código fuente disponible para la mayor parte de las rutinas **printf** y **scanf**, realizan una llamada interna a otra rutina para la que no se proporciona código fuente.

## <a name="routines-that-behave-differently-in-a-debug-build-of-an-application"></a>Rutinas que se comportan de manera diferente en una compilación de depuración de una aplicación

Ciertas funciones en tiempo de ejecución de C y algunos operadores de C++ se comportan de manera diferente cuando se les llama desde una versión de depuración de una aplicación. (Observe que una compilación de depuración de una aplicación se puede generar definiendo la marca `_DEBUG` o vinculándola a una versión de depuración de la biblioteca en tiempo de ejecución de C). Las diferencias de comportamiento suelen tener relación con características adicionales o información proporcionada por la rutina para posibilitar el proceso de depuración. En la siguiente tabla se enumeran estas rutinas.

|||
|-|-|
|[abort](../c-runtime-library/reference/abort.md) (Rutina) de C|[delete](../cpp/delete-operator-cpp.md) (Operador) de C++|
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md) (Rutina) de C|[new](../cpp/new-operator-cpp.md) (Operador) de C++|

## <a name="see-also"></a>Vea también

[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Comprobar errores en tiempo de ejecución](../c-runtime-library/run-time-error-checking.md)<br/>
