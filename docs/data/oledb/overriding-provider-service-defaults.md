---
title: Reemplazar los valores predeterminados de servicio de un proveedor
ms.date: 10/29/2018
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
ms.openlocfilehash: 08011f65ca220885e124e5ad6072244e4ad6e80d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62282954"
---
# <a name="overriding-provider-service-defaults"></a>Reemplazar los valores predeterminados de servicio de un proveedor

Se devuelve el valor del proveedor del registro para OLEDB_SERVICES como el valor predeterminado para el [DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898(v=vs.85)) propiedad de inicialización en el objeto de origen de datos.

Siempre y cuando la entrada del registro existe, se agregan los objetos del proveedor. El usuario puede invalidar configuración predeterminada del proveedor para servicios habilitados estableciendo la propiedad DBPROP_INIT_OLEDBSERVICES antes de la inicialización. Para habilitar o deshabilitar un servicio determinado, el usuario obtiene el valor actual de la propiedad DBPROP_INIT_OLEDBSERVICES, Establece o borra el bit habilitar o deshabilitar la propiedad determinada y restablece la propiedad. DBPROP_INIT_OLEDBSERVICES puede establecerse directamente en OLE DB o en la cadena de conexión pasada a ADO o `IDataInitialize::GetDatasource`. Los valores correspondientes para habilitar o deshabilitar servicios individuales se muestran en la tabla siguiente.

|Servicios predeterminados habilitados|Valor de la propiedad DBPROP_INIT_OLEDBSERVICES|Valor de cadena de conexión|
|------------------------------|------------------------------------------------|--------------------------------|
|Todos los servicios (valor predeterminado)|DBPROPVAL_OS_ENABLEALL|"Servicios OLE DB = -1;"|
|Todos excepto la agrupación y AutoEnlistment|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|"Servicios OLE DB = -4;"|
|Todos excepto el Cursor de cliente|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"Servicios OLE DB = -5;"|
|Todos excepto Pooling, AutoEnlistment y Cursor de cliente|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"Servicios OLE DB = -7;"|
|No hay servicios|`~DBPROPVAL_OS_ENABLEALL`|"Servicios OLE DB = 0;"|

Si no existe la entrada del registro para el proveedor, los administradores de componentes no recopilar los objetos del proveedor. No hay servicios se activará, incluso si se solicita explícitamente por el usuario.

## <a name="see-also"></a>Vea también

[Agrupación de recursos](/previous-versions/windows/desktop/ms713655(v=vs.85))<br/>
[Cómo los consumidores utilizan la agrupación de recursos](/previous-versions/windows/desktop/ms715907(v=vs.85))<br/>
[Funcionan de proveedores de forma eficaz con la agrupación de recursos](/previous-versions/windows/desktop/ms714906(v=vs.85))<br/>
[Habilitar y deshabilitar servicios OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)<br/>