---
title: __RTDynamicCast
ms.date: 11/04/2016
api_name:
- __RTDynamicCast
api_location:
- msvcr90.dll
- msvcr110.dll
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __RTDynamicCast
helpviewer_keywords:
- __RTDynamicCast
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
ms.openlocfilehash: c4b0caadf20d6c5494acf47ee5a788b5ee009c47
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957342"
---
# <a name="__rtdynamiccast"></a>__RTDynamicCast

Implementación en tiempo de ejecución del operador [dynamic_cast](../cpp/dynamic-cast-operator.md).

## <a name="syntax"></a>Sintaxis

```cpp
PVOID __RTDynamicCast (
   PVOID inptr,
   LONG VfDelta,
   PVOID SrcType,
   PVOID TargetType,
   BOOL isReference
   ) throw(...)
```

#### <a name="parameters"></a>Parámetros

*inptr*<br/>
Puntero a un objeto polimórfico.

*VfDelta*<br/>
Desplazamiento del puntero de función virtual en el objeto.

*SrcType*<br/>
Tipo estático del objeto al que apunta el parámetro `inptr`.

*TargetType*<br/>
Resultado previsto de la conversión.

*isReference*<br/>
**true** si la entrada es una referencia, **false** si es un puntero.

## <a name="return-value"></a>Valor devuelto

Puntero para el objeto secundario adecuado, si es correcto; en caso contrario, **NULL**.

## <a name="exceptions"></a>Excepciones

`bad_cast()` si la entrada `dynamic_cast<>` es una referencia y se produce un error en la conversión.

## <a name="remarks"></a>Comentarios

Convierte `inptr` en un objeto de tipo `TargetType`. El tipo de `inptr` debe ser un puntero si `TargetType` es un puntero, o un valor L si `TargetType` es una referencia. `TargetType` debe ser un puntero o una referencia a un tipo de clase definido previamente o un puntero a void.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|__RTDynamicCast|rtti.h|