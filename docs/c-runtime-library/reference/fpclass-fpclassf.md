---
title: _fpclass, _fpclassf
ms.date: 04/05/2018
apiname:
- _fpclass
- _fpclassf
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fpclass
- _fpclass
- _fpclassf
- math/_fpclass
- float/_fpclass
- math/_fpclassf
helpviewer_keywords:
- fpclass function
- floating-point numbers, IEEE representation
- _fpclass function
- _fpclassf function
ms.assetid: 2774872d-3543-446f-bc72-db85f8b95a6b
ms.openlocfilehash: 987c87cc7a03f4a24e47654ae52e8a2416a15184
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333227"
---
# <a name="fpclass-fpclassf"></a>_fpclass, _fpclassf

Devuelve un valor que indica la clasificación de punto flotante del argumento.

## <a name="syntax"></a>Sintaxis

```C
int _fpclass(
   double x
);

int _fpclassf(
   float x
); /* x64 only */
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor de punto flotante que se va a probar.

## <a name="return-value"></a>Valor devuelto

El **_fpclass** y **_fpclassf** funciones devuelven un valor entero que indica la clasificación de punto flotante del argumento *x*. Es posible que la clasificación tenga uno de los valores siguientes, que se definen en \<float.h>.

|Valor|Descripción|
|-----------|-----------------|
|**_FPCLASS_SNAN**|NaN de señalización|
|**_FPCLASS_QNAN**|NaN reservado|
|**_FPCLASS_NINF**|Infinito negativo (-INF)|
|**_FPCLASS_NN**|Negativo normalizado distinto de cero|
|**_FPCLASS_ND**|Negativo no normalizado|
|**_FPCLASS_NZ**|Cero negativo (- 0)|
|**_FPCLASS_PZ**|Cero positivo (+0)|
|**_FPCLASS_PD**|Positivo no normalizado|
|**_FPCLASS_PN**|Positivo normalizado distinto de cero|
|**_FPCLASS_PINF**|Infinito positivo (+INF)|

## <a name="remarks"></a>Comentarios

El **_fpclass** y **_fpclassf** funciones son específicas de Microsoft. Son similares a [fpclassify](fpclassify.md), pero devuelven información más detallada sobre el argumento. El **_fpclassf** función sólo está disponible cuando se compila para la x64 plataforma.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fpclass**, **_fpclassf**|\<float.h>|

Para obtener más información sobre compatibilidad y conformidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[fpclassify](fpclassify.md)<br/>