---
title: Plantillas, atributos y otras implementaciones de OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
ms.openlocfilehash: 0e6b5dbc97f6a7bea1df342d6a792ea43907ca33
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62283899"
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>Plantillas, atributos y otras implementaciones de OLE DB

## <a name="atl-ole-db-templates"></a>Plantillas OLE DB de ATL

Las plantillas OLE DB, que forman parte de ATL (Active Template Library), que la tecnología de base de datos de OLE DB de alto rendimiento más fácil usar al proporcionar clases que implementan muchas de las interfaces OLE DB más utilizadas. Junto con esta plantilla de biblioteca incluye compatibilidad de Asistente para crear aplicaciones de inicio de OLE DB.

Esta biblioteca de plantillas contiene dos partes:

- **Plantillas de consumidor OLE DB** usado para implementar una aplicación de cliente (consumidor) de OLE DB.

- **Plantillas de proveedores OLE DB** usado para implementar una aplicación de servidor (proveedor) de OLE DB.

Para usar las plantillas OLE DB, es necesario estar familiarizado con las plantillas de C++, COM y las interfaces OLE DB. Si no está familiarizado con OLE DB, consulte [referencia del programador de OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming).

Para obtener más información, hacer lo siguiente:

- Lea los temas sobre la [plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md) o [plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).

- Crear un [consumidor OLE DB](../../data/oledb/creating-an-ole-db-consumer.md) o [proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md).

- Ver la lista de [clases de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) o [clases de proveedor OLE DB](../../data/oledb/ole-db-provider-templates-reference.md).

- Ver la lista de [ejemplos de plantillas OLE DB](https://github.com/Microsoft/VCSamples).

- Consulte [referencia del programador OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) (en el SDK de Windows).

## <a name="ole-db-attributes"></a>Atributos de OLE DB

El [atributos de consumidor OLE DB](../../windows/ole-db-consumer-attributes.md) proporcionan una manera cómoda para crear consumidores OLE DB. Los atributos OLE DB insertan código basado en el [plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) para crear trabajo consumidores OLE DB y proveedores. Si tiene que especificar la funcionalidad no admitida por los atributos, puede usar las plantillas OLE DB junto con los atributos en el código.

## <a name="mfc-ole-db-classes"></a>Clases MFC OLE DB

La biblioteca MFC contiene una clase, [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), que muestra los registros de base de datos en controles. La vista es una vista de formulario conectada directamente a un `CRowset` de objetos y muestra los campos de la `CRowset` objeto en los controles de la plantilla de cuadro de diálogo. También proporciona una implementación predeterminada para desplazarse al primero, siguiente, anterior o el último registro y una interfaz para actualizar el registro actualmente en la vista. Para obtener más información, consulta `COleDBRecordView`.

## <a name="ole-db-sdk-interfaces"></a>Interfaces SDK de OLE DB

En los casos donde las plantillas OLE DB no admite la funcionalidad de OLE DB, deberá usar sus propias interfaces OLE DB. Para obtener más información, consulte [referencia del programador de OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Programación de OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Información general sobre la programación de OLE DB](../../data/oledb/ole-db-programming-overview.md)