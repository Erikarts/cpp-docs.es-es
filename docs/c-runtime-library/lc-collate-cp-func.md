---
title: ___lc_collate_cp_func
ms.date: 11/04/2016
apiname:
- ___lc_collate_cp_func
apilocation:
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- ___lc_collate_cp_func
helpviewer_keywords:
- ___lc_collate_cp_func
ms.assetid: 46ccc084-7ac9-4e5d-9138-e12cb5845615
ms.openlocfilehash: fac8b7ba2e9568dd53509e5cccbb96a6b2f1df8d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738884"
---
# <a name="lccollatecpfunc"></a>___lc_collate_cp_func

Función de CRT interna. Recupera la página de código de intercalación actual del subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>Valor devuelto

Página de código de intercalación actual del subproceso.

## <a name="remarks"></a>Comentarios

`___lc_collate_cp_func` es una función de CRT interna a la que recurren otras funciones de CRT para obtener la página de código de intercalación actual del almacén local de subprocesos de datos de CRT. Esta información también se puede obtener mediante la función [_get_current_locale](../c-runtime-library/reference/get-current-locale.md).

Las funciones de CRT internas son específicas de la implementación y están sujetas a cambio en cada versión. Se desaconseja usarlas en el código.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`___lc_collate_cp_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Vea también

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
