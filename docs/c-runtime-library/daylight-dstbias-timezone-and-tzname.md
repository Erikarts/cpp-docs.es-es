---
title: _daylight, _dstbias, _timezone y _tzname
ms.date: 11/04/2016
f1_keywords:
- tzname
- _timezone
- timezone
- _daylight
- _tzname
- daylight
helpviewer_keywords:
- time zones
- time adjustments
- timezone variables
- _tzname function
- _daylight function
- _timezone function
- daylight function
- local time adjustments
- timezone function
- tzname function
- time-zone variables
ms.assetid: d06c7292-6b99-4aba-b284-16a96570c856
ms.openlocfilehash: ad28ce701a4c6aa60208ed0cefe8f7dc06ef55a7
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51325922"
---
# <a name="daylight-dstbias-timezone-and-tzname"></a>_daylight, _dstbias, _timezone y _tzname

`_daylight`, `_dstbias`, `_timezone` y `_tzname` se usan en algunas rutinas de fecha y hora para realizar ajustes de hora local. Estas variables globales han quedado en desuso en las versiones funcionales más seguras, que deben usarse en lugar de la variables globales.

|Variable global|Equivalentes funcionales|
|---------------------|---------------------------|
|`_daylight`|[_get_daylight](../c-runtime-library/reference/get-daylight.md)|
|`_dstbias`|[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)|
|`_timezone`|[_get_timezone](../c-runtime-library/reference/get-timezone.md)|
|`_tzname`|[_get_tzname](../c-runtime-library/reference/get-tzname.md)|

Se declaran en Time.h como sigue.

## <a name="syntax"></a>Sintaxis

```
extern int _daylight;
extern int _dstbias;
extern long _timezone;
extern char *_tzname[2];
```

## <a name="remarks"></a>Comentarios

En una llamada a `_ftime`, `localtime` o `_tzset`, los valores de `_daylight`, `_dstbias`, `_timezone` y `_tzname` se determinan a partir del valor de la variable de entorno `TZ`. Si no establece explícitamente el valor de `TZ`, `_tzname[0]` y `_tzname[1]` contienen la configuración predeterminada de "PST" y "PDT" respectivamente.  Las funciones de manipulación horaria ([_tzset](../c-runtime-library/reference/tzset.md), [_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md) y [localtime](../c-runtime-library/reference/localtime-localtime32-localtime64.md)) intentan establecer los valores de `_daylight`, `_dstbias` y `_timezone` consultando el sistema operativo para obtener el valor predeterminado de cada variable. En la siguiente tabla se muestran los valores de variable global de la zona horaria.

|Variable|Valor|
|--------------|-----------|
|`_daylight`|Distinto de cero si la zona de horario de verano (DST) se especifica en `TZ` o se determina a partir del sistema operativo; en caso contrario, 0. El valor predeterminado es 1.|
|`_dstbias`|Diferencia del horario de verano.|
|`_timezone`|Diferencia en segundos entre la hora universal coordinada y la hora local. El valor predeterminado es 28.800.|
|`_tzname[0]`|El nombre de zona horaria se deriva de la variable de entorno `TZ`. El valor predeterminado es "PST".|
|`_tzname[1]`|El nombre de la zona de DST se deriva de la variable de entorno `TZ`. El valor predeterminado es "PDT" (horario de verano del Pacífico).|

## <a name="see-also"></a>Vea también

[Variables globales](../c-runtime-library/global-variables.md)<br/>
[_get_daylight](../c-runtime-library/reference/get-daylight.md)<br/>
[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)<br/>
[_get_timezone](../c-runtime-library/reference/get-timezone.md)<br/>
[_get_tzname](../c-runtime-library/reference/get-tzname.md)