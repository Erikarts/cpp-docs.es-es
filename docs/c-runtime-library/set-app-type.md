---
title: _set_app_type
ms.date: 11/04/2016
apiname:
- _set_app_type
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
ms.openlocfilehash: 5a29fd94cca7fdbf6bbb24699b7f510bf1465f15
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749196"
---
# <a name="setapptype"></a>_set_app_type

Función interna que se usa en el inicio para indicar a CRT si la aplicación es de consola o de interfaz gráfica de usuario.

## <a name="syntax"></a>Sintaxis

```cpp
typedef enum _crt_app_type
{
    _crt_unknown_app,
    _crt_console_app,
    _crt_gui_app
} _crt_app_type;

void __cdecl _set_app_type(
    _crt_app_type appType
    );
```

## <a name="parameters"></a>Parámetros

*appType*<br/>
Valor que indica el tipo de aplicación. Los valores posibles son:

|Valor|Descripción|
|----------------|-----------------|
|_crt_unknown_app|Tipo de aplicación desconocido.|
|_crt_console_app|Aplicación de consola (línea de comandos).|
|_crt_gui_app|Aplicación GUI (Windows).|

## <a name="remarks"></a>Comentarios

Normalmente, no es necesario llamar a esta función. Forma parte del código de inicio en tiempo de ejecución de C que se ejecuta antes de llamar a `main` en la aplicación.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|_set_app_type|process.h|
