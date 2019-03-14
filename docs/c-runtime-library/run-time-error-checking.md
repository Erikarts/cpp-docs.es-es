---
title: Comprobar errores en tiempo de ejecución
ms.date: 11/04/2016
f1_keywords:
- c.runtime
helpviewer_keywords:
- run-time error checking
- run-time errors, checking
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
ms.openlocfilehash: ec07b9b0c6aa52187c3c24bff4cc51712dbf9fc8
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746466"
---
# <a name="run-time-error-checking"></a>Comprobar errores en tiempo de ejecución

La biblioteca de tiempo de ejecución de C contiene las funciones que admiten las comprobaciones de errores en tiempo de ejecución. La comprobación de errores en tiempo de ejecución permite compilar el programa de manera que se notifiquen determinados tipos de errores en tiempo de ejecución. El usuario especifica cómo se notifican los errores y qué tipos de errores se notifican. Para obtener más información, vea [Cómo: Uso de comprobaciones nativas en tiempo de ejecución](/visualstudio/debugger/how-to-use-native-run-time-checks).

Utilice las siguientes funciones para personalizar la forma en que el programa realiza la comprobación de errores en tiempo de ejecución.

## <a name="run-time-error-checking-functions"></a>Funciones de comprobación de errores en tiempo de ejecución

|Función|Usar|
|--------------|---------|
|[_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md)|Devuelve una breve descripción de un tipo de comprobación de error en tiempo de ejecución.|
|[_RTC_NumErrors](../c-runtime-library/reference/rtc-numerrors.md)|Devuelve el número total de errores que se pueden detectar mediante las comprobaciones de errores en tiempo de ejecución.|
|[_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)|Designa una función como el controlador para notificar comprobaciones de errores en tiempo de ejecución.|
|[_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)|Asocia un error que se detecta mediante comprobaciones de errores en tiempo de ejecución con un tipo.|

## <a name="see-also"></a>Vea también

[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
[/RTC (Comprobaciones de errores en tiempo de ejecución)](../build/reference/rtc-run-time-error-checks.md)<br/>
[runtime_checks](../preprocessor/runtime-checks.md)<br/>
[Rutinas de depuración](../c-runtime-library/debug-routines.md)<br/>
