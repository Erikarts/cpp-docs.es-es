---
title: _setjmp3
ms.date: 11/04/2016
apiname:
- _setjmp3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- setjmp3
- _setjmp3
helpviewer_keywords:
- _setjmp3 function
- setjmp3 function
ms.assetid: 6129c2f3-8bac-4fdb-a827-44e1eebba500
ms.openlocfilehash: e2c89acf1de88b831d70a0f438cdf14148a48632
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741809"
---
# <a name="setjmp3"></a>_setjmp3

Función de CRT interna. Nueva implementación de la función `setjmp`.

## <a name="syntax"></a>Sintaxis

```
int _setjmp3(
   OUT jmp_buf env,
   int count,
   (optional parameters)
);
```

#### <a name="parameters"></a>Parámetros

*env*<br/>
[out] Dirección del búfer para almacenar la información de estado.

*count*<br/>
[in] Número de `DWORD` de información adicionales que hay almacenados en los `optional parameters`.

*optional parameters*<br/>
[in] Datos adicionales insertados por la función intrínseca `setjmp`. El primer `DWORD` es un puntero de función que sirve para desenredar datos extra y regresar a un estado de registro no volatile. El segundo `DWORD` es el nivel de intento que se va a restaurar. Cualquier otro dato extra se guarda en la matriz de datos genéricos de `jmp_buf`.

## <a name="return-value"></a>Valor devuelto

Siempre devuelve 0.

## <a name="remarks"></a>Comentarios

No use esta función en un programa de C++. Se trata de una función intrínseca que no admite C++. Para más información sobre cómo usar `setjmp`, vea [Usar setjmp/longjmp](../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[setjmp](../c-runtime-library/reference/setjmp.md)
