---
title: Utilizar marcadores
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
ms.openlocfilehash: 579e67151858904e877a34bf30467e3cb97fe2c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388961"
---
# <a name="using-bookmarks"></a>Utilizar marcadores

Antes de abrir el conjunto de filas, se debe indicar al proveedor que desea utilizar marcadores. Para ello, establezca el `DBPROP_BOOKMARKS` propiedad **true** en conjunto de sus propiedades. El proveedor recupera los marcadores como columna cero, lo que debe usar la macro especial BOOKMARK_ENTRY y `CBookmark` clase si está usando un descriptor de acceso estático. `CBookmark` es una clase de plantilla donde el argumento es la longitud en bytes del búfer del marcador. La longitud del búfer necesario para un marcador depende del proveedor. Si usa el proveedor OLE DB de ODBC, como se muestra en el ejemplo siguiente, el búfer debe ser de 4 bytes.

```cpp
class CProducts
{
public:
   CBookmark<4> bookmark;

   BEGIN_COLUMN_MAP(CProducts)
      BOOKMARK_ENTRY(bookmark)
   END_COLUMN_MAP()
};
```

A continuación, usa el código siguiente:

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_BOOKMARKS, true);

CTable<CAccessor<CProducts>> product;
CSession session;
product.Open(session, "Products", &propset);
```

Si usa `CDynamicAccessor`, el búfer se establece dinámicamente en tiempo de ejecución. En este caso, puede usar una versión especializada de `CBookmark` para el que no se especifica una longitud de búfer. Use la función `GetBookmark` para recuperar el marcador del registro actual, como se muestra en este ejemplo de código:

```cpp
CTable<CDynamicAccessor> product;
CBookmark<> bookmark;
CDBPropSet propset(DBPROPSET_ROWSET);
CSession session;

propset.AddProperty(DBPROP_BOOKMARKS, true);
product.Open(session, "Products", &propset);
product.MoveNext();
product.GetBookmark(&bookmark);
```

Para obtener información sobre la compatibilidad con marcadores en proveedores, vea [proveedor de compatibilidad con los marcadores](../../data/oledb/provider-support-for-bookmarks.md).

## <a name="see-also"></a>Vea también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)