---
title: Determinar qué tipo de descriptor de acceso se debe utilizar
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
ms.openlocfilehash: 98234852d0577e581135980d6b8e525aeead5dc2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175374"
---
# <a name="determining-which-type-of-accessor-to-use"></a>Determinar qué tipo de descriptor de acceso se debe utilizar

Puede determinar los tipos de datos en un conjunto de filas en tiempo de compilación o en tiempo de ejecución.

Si necesita determinar los tipos de datos en tiempo de compilación, utilice un descriptor de acceso estático (como `CAccessor`). Puede determinar los tipos de datos manualmente o mediante el **el Asistente para consumidores OLE DB ATL**.

Si necesita determinar los tipos de datos en tiempo de ejecución, utilice un dinámico (`CDynamicAccessor` o sus elementos secundarios) o un descriptor de acceso manual (`CManualAccessor`). En estos casos, puede llamar a `GetColumnInfo` en el conjunto de filas para devolver la información de enlace de columna desde la que se pueden determinar los tipos.

En la tabla siguiente se enumera los tipos de descriptores de acceso proporcionadas en las plantillas de consumidor. Cada descriptor de acceso tiene ventajas y desventajas. Dependiendo de su situación, un tipo de descriptor de acceso debe adaptarse a sus necesidades.

|Clase de descriptor de acceso|Enlaces|Parámetro|Comentario|
|--------------------|-------------|---------------|-------------|
|`CAccessor`|Cree un registro de usuario con macros COLUMN_ENTRY. Las macros de enlazan a un miembro de datos de ese registro al descriptor de acceso. Cuando se crea el conjunto de filas, columnas no se pudo enlazar.|Sí, mediante el uso de una entrada de macro PARAM_MAP. Una vez enlazado, no se pudo enlazar parámetros.|Descriptor de acceso más rápido debido a una cantidad pequeña de código.|
|`CDynamicAccessor`|Automático.|No.|Resulta útil si desconoce el tipo de datos en un conjunto de filas.|
|`CDynamicParameterAccessor`|Automático, pero puede ser [invalidar](../../data/oledb/overriding-a-dynamic-accessor.md).|Sí, si el proveedor admite `ICommandWithParameters`. Los parámetros se enlazan automáticamente.|Más lento que `CDynamicAccessor` pero útil para llamar a procedimientos almacenados genéricos.|
|`CDynamicStringAccessor[A,W]`|Automático.|No.|Recupera los datos que se obtiene acceso desde el almacén de datos como datos de cadena.|
|`CManualAccessor`|Manual utilizando `AddBindEntry`.|Manualmente mediante `AddParameterEntry`.|Fast; parámetros y columnas de una sola vez enlazan. Determinar el tipo de datos que se va a usar. (Consulte [DBVIEWER](https://github.com/Microsoft/VCSamples) ejemplo para obtener un ejemplo.) Requiere más código que `CDynamicAccessor` o `CAccessor`. Es más parecida a llamar directamente a OLE DB.|
|`CXMLAccessor`|Automático.|No.|Recupera los datos que se obtiene acceso desde el almacén de datos como datos de cadena y formatos de datos etiquetado como XML.|

## <a name="see-also"></a>Vea también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)