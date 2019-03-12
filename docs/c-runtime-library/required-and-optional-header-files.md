---
title: Archivos de encabezado requeridos y opcionales
ms.date: 11/04/2016
f1_keywords:
- c.headers
helpviewer_keywords:
- include files, required in run time
- header files, required in run time
ms.assetid: f64d0bf5-e2c3-4b42-97d0-443b3d901d9f
ms.openlocfilehash: 06f7ced45f8def05219d8869708f555a78f73cd3
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744526"
---
# <a name="required-and-optional-header-files"></a>Archivos de encabezado requeridos y opcionales

La descripción de cada rutina de tiempo de ejecución incluye una lista de archivos de encabezado (.H) requeridos y opcionales para dicha rutina. Los archivos de encabezado requeridos deben incluirse para obtener la declaración de función de la rutina o una definición utilizada por otra rutina a la que se llama internamente. Los archivos de encabezado opcionales se suelen incluir para aprovechar las ventajas de las contantes, las definiciones de tipo o las macros alineadas predefinidas. En la tabla siguiente se indican algunos ejemplos de contenido de los archivos de encabezado opcionales:

|de esquema JSON|Ejemplo|
|----------------|-------------|
|Definición de macro|Si una rutina de la biblioteca se implementa como una macro, la definición de macro puede estar en un archivo de encabezado que no sea el archivo de encabezado de la rutina original. Por ejemplo, la macro `_toupper` está definida en el archivo de encabezado CTYPE.H, mientras que la función `toupper` está declarada en STDLIB.H.|
|Constante predefinida|Muchas rutinas de la biblioteca hacen referencia a las constantes que se definen en archivos de encabezado. Por ejemplo, la rutina `_open` utiliza constantes como `_O_CREAT`, que se define en el archivo de encabezado FCNTL.H.|
|Definición de tipo|Algunas rutinas de la biblioteca devuelven una estructura o adoptan una estructura como argumento. Por ejemplo, las rutinas de entrada/salida de secuencias utilizan una estructura de tipo `FILE`, que se define en STDIO.H.|

Los archivos de encabezado de la biblioteca en tiempo de ejecución proporcionan declaraciones de función en el estilo recomendado de ANSI/ISO C estándar. El compilador realiza la comprobación de tipos en cualquier referencia a rutinas que se produce después de su declaración de función asociada. Las declaraciones de función son especialmente importantes para las rutinas que devuelven un valor de algún tipo distinto de `int`, que es el valor predeterminado. El compilador considerará como valor devuelvo `int` en caso de que las rutinas no especifiquen su valor devuelto apropiado en su declaración, un comportamiento que puede generar resultados inesperados. Vea [Comprobación de tipos](../c-runtime-library/type-checking-crt.md) para obtener más información.

## <a name="see-also"></a>Vea también

[Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)
