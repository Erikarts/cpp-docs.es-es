---
title: _purecall
ms.date: 11/04/2016
apiname:
- _purecall
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ntoskrnl.exe
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- purecall
- _purecall
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
ms.openlocfilehash: a7a6db42dc4b8d9b2962a66c7866aae9db55eb3b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62231980"
---
# <a name="purecall"></a>_purecall

Controlador de errores predeterminado de llamadas de función virtual pura. El compilador genera un código para llamar a esta función cuando se llama a una función miembro virtual pura.

## <a name="syntax"></a>Sintaxis

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Comentarios

El **_purecall** función es un detalle de implementación específico de Microsoft de Microsoft Visual C++ compilador. Esta función no está diseñada para ser llamada directamente por el código; además, no tiene ninguna declaración de encabezado pública. Se documenta aquí porque se trata de una exportación pública de la biblioteca en tiempo de ejecución de C.

Una llamada a una función virtual pura es un error, porque no tiene ninguna implementación. El compilador genera código para invocar la **_purecall** función de controlador de error cuando se llama a una función virtual pura. De forma predeterminada, **_purecall** finaliza el programa. Antes de finalizar, el **_purecall** función invoca un **_purecall_handler** funcionando si uno se ha establecido para el proceso. Puede instalar su propia función de controlador de errores para llamadas de función virtual pura, para capturarlas con fines informativos o de depuración. Para usar su propio controlador de errores, cree una función que tiene el **_purecall_handler** firma, a continuación, usar [_set_purecall_handler](get-purecall-handler-set-purecall-handler.md) para convertirlo en el controlador actual.

## <a name="requirements"></a>Requisitos

El **_purecall** función no tiene ninguna declaración de encabezado. El **_purecall_handler** typedef se define en \<stdlib.h >.

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler, _set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
