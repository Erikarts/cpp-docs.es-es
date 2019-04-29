---
title: Especificar el modelo de subprocesos de un proyecto (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- _ATL_FREE_THREADED macro
- _ATL_APARTMENT_THREADED macro
- ATL, multithreading
- threading [ATL], models
- _ATL_SINGLE_THREADED macro
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
ms.openlocfilehash: 69c1c80bba0b09ce69e0b9b9b27296ef2508e60b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275222"
---
# <a name="specifying-the-threading-model-for-a-project-atl"></a>Especificar el modelo de subprocesos de un proyecto (ATL)

Las macros siguientes están disponibles para especificar el modelo de subprocesos de un proyecto ATL:

|Macro|Directrices para usar|
|-----------|--------------------------|
|_ATL_SINGLE_THREADED|Define si todos los objetos utilizan el modelo de subprocesamiento único.|
|_ATL_APARTMENT_THREADED|Define si uno o varios de los objetos utilizan el apartamento de subproceso.|
|_ATL_FREE_THREADED|Define si uno o varios de los objetos utilizan el subprocesamiento libre o neutra. El código existente puede contener referencias a la macro equivalente [_ATL_MULTI_THREADED](reference/compiler-options-macros.md#_atl_multi_threaded).|

Si no se define ninguna de estas macros para el proyecto, activa _ATL_FREE_THREADED entrará en vigor.

Las macros de afectar al rendimiento de tiempo de ejecución como sigue:

- Especificación de la macro que corresponde a los objetos en el proyecto puede mejorar el rendimiento de tiempo de ejecución.

- Especificar un nivel más alto de la macro, por ejemplo, si se especifica _ATL_APARTMENT_THREADED cuando todos los objetos tienen un únicos subproceso, ligeramente degradar el rendimiento de tiempo de ejecución.

- Especificar un nivel inferior de la macro, por ejemplo, si especifica _ATL_SINGLE_THREADED cuando uno o varios de los objetos usar apartamento de subproceso o subprocesamiento libre, puede hacer que la aplicación producirá un error en tiempo de ejecución.

Consulte [opciones, Asistente para objetos simples de ATL](../atl/reference/options-atl-simple-object-wizard.md) para obtener una descripción de los subprocesos, los modelos disponibles para un objeto ATL.

## <a name="see-also"></a>Vea también

[Conceptos](../atl/active-template-library-atl-concepts.md)
