---
title: _STATIC_ASSERT (Macro)
ms.date: 11/04/2016
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
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _STATIC_ASSERT
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
ms.openlocfilehash: 5d3aa1d9665b48a0690d8eb62353fc98c5a550f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62354704"
---
# <a name="staticassert-macro"></a>_STATIC_ASSERT (Macro)

Evalúa una expresión en tiempo de compilación y generar un error cuando el resultado es **FALSE**.

## <a name="syntax"></a>Sintaxis

```C
_STATIC_ASSERT(
    booleanExpression
);
```

### <a name="parameters"></a>Parámetros

*booleanExpression*<br/>
Expresión (incluidos los punteros) que se evalúa como distinto de cero a (**TRUE**) o 0 (**FALSE**).

## <a name="remarks"></a>Comentarios

Esta macro es similar a la [macros _ASSERT y _ASSERTE](assert-asserte-assert-expr-macros.md), salvo que *booleanExpression* se evalúa en tiempo de compilación en lugar de en tiempo de ejecución. Si *booleanExpression* se evalúa como **FALSE** (0), [Error del compilador C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) se genera.

## <a name="example"></a>Ejemplo

En este ejemplo, comprobamos si el [sizeof](../../c-language/sizeof-operator-c.md) una **int** es mayor que o igual a 2 bytes y si el [sizeof](../../c-language/sizeof-operator-c.md) un **largo** es de 1 byte. El programa no se compilará y generará [Error del compilador C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) porque un **largo** es mayor que 1 byte.

```C
// crt__static_assert.c

#include <crtdbg.h>
#include <stdio.h>

_STATIC_ASSERT(sizeof(int) >= 2);
_STATIC_ASSERT(sizeof(long) == 1);  // C2466

int main()
{
    printf("I am sure that sizeof(int) will be >= 2: %d\n",
        sizeof(int));
    printf("I am not so sure that sizeof(long) == 1: %d\n",
        sizeof(long));
}
```

## <a name="requirements"></a>Requisitos

|Macro|Encabezado necesario|
|-----------|---------------------|
|**_STATIC_ASSERT**|\<crtdbg.h>|

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR (macros)](assert-asserte-assert-expr-macros.md)<br/>
