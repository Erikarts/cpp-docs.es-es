---
title: feclearexcept1
ms.date: 04/05/2018
api_name:
- feclearexcept
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- feclearexcept
- fenv/feclearexcept
helpviewer_keywords:
- feclearexcept function
ms.assetid: ef419da3-c248-4432-b53c-8e7a475d9533
ms.openlocfilehash: 9899d7068a289e7d5f71cb42a8373869d60c3070
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941268"
---
# <a name="feclearexcept"></a>feclearexcept

Intenta borrar las marcas de excepción de punto flotante especificadas por el argumento.

## <a name="syntax"></a>Sintaxis

```C
int feclearexcept(
   int excepts
);
```

### <a name="parameters"></a>Parámetros

*excepts*<br/>
Marcas de estado de excepción que se borran.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si *excepts* es cero o si todas las excepciones especificadas se borraron correctamente. De lo contrario, devuelve un valor distinto de cero.

## <a name="remarks"></a>Comentarios

La función **feclearexcept** intenta borrar las marcas de estado de excepción de punto flotante especificadas por *excepts*. La función admite estas macros de excepción, que se definen en fenv.h:

|Macro de excepción|DESCRIPCIÓN|
|---------------------|-----------------|
|FE_DIVBYZERO|Se ha producido un error de singularidad o de polo en una operación de punto flotante anterior; se ha creado un valor infinito.|
|FE_INEXACT|Se ha forzado la función a redondear el resultado almacenado de una operación de punto flotante anterior.|
|FE_INVALID|Se ha producido un error de dominio en una operación de punto flotante anterior.|
|FE_OVERFLOW|Se ha producido un error de intervalo; el resultado de una operación de punto flotante anterior era demasiado grande para representarse.|
|FE_UNDERFLOW|El resultado de una operación de punto flotante anterior era demasiado pequeño para representarlo con completa precisión; se ha creado un valor no normalizado.|
|FE_ALL_EXCEPT|Operación OR bit a bit de todas las excepciones de punto flotante admitidas.|

El argumento *excepts* puede ser cero, o la operación OR bit a bit de una o más de las macros de excepción admitidas. El resultado de cualquier otro valor de argumento es indefinido.

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**feclearexcept**|\<fenv.h>|\<cfenv>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
