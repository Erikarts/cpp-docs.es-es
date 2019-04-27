---
title: Opciones, Asistente para componentes de páginas Active Server ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.options
helpviewer_keywords:
- ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
ms.openlocfilehash: 7e9740a67f265484c349a4df644be882dba30c13
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197372"
---
# <a name="options-atl-active-server-page-component-wizard"></a>Opciones, Asistente para componentes de páginas Active Server ATL

Use esta página del Asistente para componentes de páginas Active Server ATL para el diseño para una mayor eficiencia y soporte técnico de error para el objeto.

Para obtener más información sobre los proyectos ATL y clases COM de ATL, vea [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md).

- **Modelo de subprocesos**

   Indica el método de administración de subprocesos. De forma predeterminada, el proyecto usa **apartamento** subprocesamiento.

   Consulte [especificar el modelo de subprocesamiento del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) para obtener más información.

   |Opción|Descripción|
   |------------|-----------------|
   |**Single**|Especifica que el objeto utiliza el modelo de subprocesamiento único. En el modelo de subprocesamiento único, un objeto siempre se ejecuta en el subproceso COM principal. Consulte [contenedores uniproceso](/windows/desktop/com/single-threaded-apartments) y [InprocServer32](/windows/desktop/com/inprocserver32) para obtener más información.|
   |**Apartment**|Especifica que el objeto utiliza el apartamento de subproceso. Apartamento de subproceso equivalente al único. Se asigna a cada objeto de un componente de subprocesamiento controlado un apartamento de subproceso, durante la vida del objeto; Sin embargo, varios subprocesos pueden usarse para varios objetos. Cada contenedor está asociado a un subproceso concreto y tiene un bombeo de mensajes de Windows (valor predeterminado).<br /><br /> Consulte [contenedores uniproceso](/windows/desktop/com/single-threaded-apartments) para obtener más información.|
   |**Ambos**|Especifica que el objeto puede usar apartamento o subprocesamiento libre, dependiendo del tipo de un subproceso creado.|
   |**Free**|Especifica que el objeto usa el subprocesamiento libre. Subprocesamiento libre es equivalente a un modelo de apartamento multiproceso. Consulte [apartamentos multiproceso](/windows/desktop/com/multithreaded-apartments) para obtener más información.|
   |**Neutral**|Especifica que el objeto sigue las directrices para apartamentos multiproceso, pero pueden ejecutar en cualquier tipo de subproceso.|

- **Agregación**

   Indica si el objeto usa [agregación](/windows/desktop/com/aggregation). El objeto agregado elige qué interfaces se expondrán a los clientes y las interfaces se exponen como si el objeto agregado implementarlos. Los clientes del objeto agregado comunicarse solo con el objeto agregado.

   |Opción|Descripción|
   |------------|-----------------|
   |**Sí**|Especifica que se puede agregar el objeto. El valor predeterminado.|
   |**No**|Especifica que no se agrega el objeto.|
   |**Solo**|Especifica que debe agregarse el objeto.|

- **Soporte técnico**

   Opciones de soporte adicionales:

   |Opción|Descripción|
   |------------|-----------------|
   |**ISupportErrorInfo**|Crea la compatibilidad con la [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) interfaz para que el objeto puede devolver información de error al cliente.|
   |**Puntos de conexión**|Permite a los puntos de conexión para el objeto mediante la realización de derivar de la clase del objeto [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|
   |**Contador de referencias de subprocesamiento libre**|Crea un objeto de contador de referencias de subprocesamiento libre para calcular referencias de punteros de interfaz eficazmente entre los subprocesos en el mismo proceso. Disponible para el objeto que especifica ya sea **ambos** o **gratis** como el modelo de subprocesos.|

## <a name="see-also"></a>Vea también

[Asistente para componentes de páginas Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[Componente de páginas Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)
