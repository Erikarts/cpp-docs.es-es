---
title: Generar excepciones de software
ms.date: 11/04/2016
helpviewer_keywords:
- run-time errors, treating as exceptions
- exception handling [C++], errors as exceptions
- exceptions [C++], flagging errors as exceptions
- errors [C++], treating as exceptions
- exception handling [C++], detecting errors
- structured exception handling [C++], errors as exceptions
- exceptions [C++], software
- RaiseException function
- software exceptions [C++]
- formats [C++], exception codes
ms.assetid: be1376c3-c46a-4f52-ad1d-c2362840746a
ms.openlocfilehash: 49ee800bafff017c29b73c5f6fd64318009a140a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403469"
---
# <a name="raising-software-exceptions"></a>Generar excepciones de software

El sistema no marca como excepciones algunos de los orígenes de errores de programa más comunes. Por ejemplo, si intenta asignar un bloque de memoria pero no hay memoria insuficiente, el tiempo de ejecución o la función de API no provoca una excepción, sino que devuelve un código de error.

Sin embargo, puede tratar cualquier condición como excepción detectando esa condición en el código y comunicándolo a continuación mediante una llamada a la [RaiseException](https://msdn.microsoft.com/library/windows/desktop/ms680552) función. Si marca los errores de esta manera, puede aportar las ventajas del control de excepciones estructurado a cualquier tipo de error en tiempo de ejecución.

Para usar el control de excepciones estructurado con errores:

- Defina su propio código de excepción para el evento.

- Llamar a `RaiseException` cuando se detecte un problema.

- Use filtros de control de excepciones para probar el código de excepción definido.

El \<winerror.h > archivo muestra el formato de los códigos de excepción. Para asegurarse de que no define un código en conflicto con un código de excepción existente, establezca el tercer bit más significativo en 1. Los cuatro bits más significativos se deben establecer como se muestra en la tabla siguiente.

|Bits|Valor binario recomendado|Descripción|
|----------|--------------------------------|-----------------|
|31-30|11|Estos dos bits describen el estado básico del código:  11 = error, 00 = correcto, 01 = informativo, 10 = advertencia.|
|29|1|Bit de cliente. Establézcalo en 1 para los códigos definido por el usuario.|
|28|0|Bit reservado. (Déjelo establecido en 0).|

Puede establecer los dos primeros bits en un valor distinto del binario 11 si lo desea, aunque el valor de “error” es adecuado para la mayoría de las excepciones. Lo importante es recordar establecer los bits 29 y 28 como se muestra en la tabla anterior.

El código de error resultante, por tanto, debe tener los cuatro bits superiores establecido en e hexadecimal. Por ejemplo, las definiciones siguientes definen códigos de excepción que no entren en conflicto con los códigos de excepción de Windows. (Es posible, no obstante, que deba comprobar qué códigos usan los archivos DLL de terceros).

```cpp
#define STATUS_INSUFFICIENT_MEM       0xE0000001
#define STATUS_FILE_BAD_FORMAT        0xE0000002
```

Después de definir un código de excepción, puede usarlo para provocar una excepción. Por ejemplo, el código siguiente genera la `STATUS_INSUFFICIENT_MEM` excepción en respuesta a un problema de asignación de memoria:

```cpp
lpstr = _malloc( nBufferSize );
if (lpstr == NULL)
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);
```

Si desea generar simplemente una excepción, puede establecer los tres últimos parámetros en 0. Los tres últimos parámetros son útiles para pasar información adicional y establecer una marca que evite que los controladores continúen la ejecución. Consulte la [RaiseException](https://msdn.microsoft.com/library/windows/desktop/ms680552) función en el SDK de Windows para obtener más información.

En los filtros de control de excepciones, puede probar los códigos que haya definido. Por ejemplo:

```cpp
__try {
    ...
}
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )
```

## <a name="see-also"></a>Vea también

[Escribir un controlador de excepciones](../cpp/writing-an-exception-handler.md)<br/>
[Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)