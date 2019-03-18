---
title: Categorías de configuración regional
ms.date: 11/04/2016
f1_keywords:
- LC_MAX
- LC_MIN
- LC_MONETARY
- LC_TIME
- LC_NUMERIC
- LC_COLLATE
- LC_CTYPE
- LC_ALL
helpviewer_keywords:
- LC_MIN constant
- LC_MONETARY constant
- LC_CTYPE constant
- locale constants
- LC_MAX constant
- LC_ALL constant
- LC_TIME constant
- LC_NUMERIC constant
- LC_COLLATE constant
ms.assetid: 868f1493-fe5d-4722-acab-bfcd374a063a
ms.openlocfilehash: 434500dab0c68aa9475f54e930b91da0b1cd2fc9
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749807"
---
# <a name="locale-categories"></a>Categorías de configuración regional

## <a name="syntax"></a>Sintaxis

```
#include <locale.h>
```

## <a name="remarks"></a>Comentarios

Las categorías de configuración regional son constantes de manifiesto utilizadas por las rutinas de localización para especificar qué parte de la información de configuración regional de un programa se usará. La configuración regional hace referencia al lugar o país/región para el que se pueden personalizar algunos aspectos del programa. Entre las áreas dependientes de la configuración regional se encuentran, por ejemplo, el formato de fechas o el formato de presentación de valores de moneda.

|Categoría de configuración regional|Partes del programa afectadas|
|---------------------|-------------------------------|
|`LC_ALL`|Todos los comportamientos específicos de la configuración regional (todas las categorías)|
|`LC_COLLATE`|Comportamiento de las funciones `strcoll` y `strxfrm`|
|`LC_CTYPE`|Comportamiento de las funciones de control de caracteres (excepto `isdigit`, `isxdigit`, `mbstowcs` y `mbtowc`, que no se ven afectadas)|
|`LC_MAX`|Igual a `LC_TIME`|
|`LC_MIN`|Igual a `LC_ALL`|
|`LC_MONETARY`|Información de formato de moneda devuelta por la función `localeconv`|
|`LC_NUMERIC`|Carácter de separador decimal para las rutinas de salida con formato (por ejemplo, `printf`), para las rutinas de conversión de datos y para la información de formato no monetaria devuelta por la función `localeconv`|
|`LC_TIME`|Comportamiento de la función `strftime`|

Vea [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener un ejemplo.

## <a name="see-also"></a>Vea también

[localeconv](../c-runtime-library/reference/localeconv.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[strcoll (funciones)](../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
