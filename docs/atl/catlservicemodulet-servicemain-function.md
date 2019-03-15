---
title: 'Función CAtlServiceModuleT:: ServiceMain'
ms.date: 11/04/2016
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
ms.openlocfilehash: 81cd8fcbdf275063b243e215301eff504a2b5cc6
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811906"
---
# <a name="catlservicemoduletservicemain-function"></a>Función CAtlServiceModuleT:: ServiceMain

El Administrador de control de servicios (SCM) llama a `ServiceMain` al abrir la aplicación del Panel de Control de servicios, seleccione el servicio y haga clic en **iniciar**.

Después de la SCM llama `ServiceMain`, un servicio debe darle el SCM una función de controlador. Esta función permite al SCM obtener el estado del servicio y pasar instrucciones específicas (por ejemplo, pausar o detener). El SCM obtiene esta función cuando el servicio pasa `_Handler` a la función de la API de Win32, [RegisterServiceCtrlHandler](/windows/desktop/api/winsvc/nf-winsvc-registerservicectrlhandlera). (`_Handler` es una función miembro estática que llama a la función miembro no estática [controlador](../atl/reference/catlservicemodulet-class.md#handler).)

En el inicio, un servicio también debe informar al SCM de su estado actual. Para ello, pasa SERVICE_START_PENDING a la función de la API de Win32, [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).

`ServiceMain` a continuación, llama a `CAtlExeModuleT::InitializeCom`, que llama a la función de la API Win32 [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex). De forma predeterminada, `InitializeCom` pasa el indicador COINIT_MULTITHREADED a la función. Esta marca indica que el programa sea un servidor de subprocesamiento libre.

Ahora, `CAtlServiceModuleT::Run` se llama para realizar el trabajo principal del servicio. `Run` continúa ejecutándose hasta que el servicio está detenido.

## <a name="see-also"></a>Vea también

[Servicios](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)
