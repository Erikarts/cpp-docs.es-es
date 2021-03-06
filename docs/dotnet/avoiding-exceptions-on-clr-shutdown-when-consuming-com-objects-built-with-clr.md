---
title: Evitar las excepciones producidas por objetos COM compilados con - clr
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], CLR shutdown exceptions
- /clr compiler option [C++], CLR shutdown exceptions
- mixed assemblies [C++], CLR shutdown exceptions
- /clr compiler option [C++], COM objects
- interoperability [C++], CLR shutdown exceptions
- CLR shutdown exceptions [C++]
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
ms.openlocfilehash: 23af1d8b48a6579b8cc20261691c1f090dc858a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633446"
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>Evitar excepciones al apagar CLR cuando se utilizan objetos COM compilados con /clr

Una vez que common language runtime (CLR) entra en modo de apagado, las funciones nativas tienen acceso limitado a los servicios de CLR. Cuando se intenta llamar a Release en un objeto COM compilado con **/CLR**, el CLR realiza la transición a código nativo y, a continuación, vuelve al código administrado para atender la llamada de IUnknown:: Release (que se define en código administrado). El CLR impide que la devolución de llamada a código administrado, ya que resulta en modo de apagado.

Para resolver este problema, asegúrese de que los destructores se llama desde métodos versión sólo contienen código nativo.

## <a name="see-also"></a>Vea también

[Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)