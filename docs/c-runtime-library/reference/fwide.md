---
title: fwide
ms.date: 11/04/2016
api_name:
- fwide
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fwide
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
ms.openlocfilehash: 2e986ba5ab28072f4933e555eea32a5893c8df56
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956221"
---
# <a name="fwide"></a>fwide

Sin implementar.

## <a name="syntax"></a>Sintaxis

```C
int fwide(
   FILE *stream,
   int mode;
);
```

### <a name="parameters"></a>Parámetros

*stream*<br/>
Puntero a la estructura de **archivo** (omitido).

*mode*<br/>
Nuevo ancho de la secuencia: positivo para carácter ancho, negativo para byte, cero para dejarlo sin cambios. (Este valor se omite).

## <a name="return-value"></a>Valor devuelto

Esta función solo devuelve el *modo*.

## <a name="remarks"></a>Comentarios

La versión actual de esta función no cumple con el estándar.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fwide**|\<wchar.h>|

Para obtener más información, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).