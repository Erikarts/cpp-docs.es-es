---
title: Obtener datos
ms.date: 10/19/2018
helpviewer_keywords:
- data [C++], fetching
- rowsets [C++], fetching
- fetching
- OLE DB consumer templates [C++], fetching data
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
ms.openlocfilehash: 441f036d1677806e81bc419ec6a45e810e63a34f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409064"
---
# <a name="fetching-data"></a>Obtener datos

Después de abrir el origen de datos, sesión y los objetos de conjunto de filas, puede capturar datos. Según el tipo de descriptor de acceso que se usa, es posible que deba enlazar las columnas.

## <a name="to-fetch-data"></a>Para capturar los datos

1. Abra el conjunto de filas mediante el correspondiente **abierto** comando.

1. Si usa `CManualAccessor`, enlazar las columnas de salida si aún no lo ha hecho. En el siguiente ejemplo se toma de la [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer) ejemplo. Para enlazar las columnas, llame a `GetColumnInfo`y, a continuación, cree un descriptor de acceso con los enlaces, tal como se muestra en el ejemplo siguiente:

    ```cpp
    // From the DBViewer Sample CDBTreeView::OnQueryEdit
    // Get the column information
    ULONG ulColumns       = 0;
    DBCOLUMNINFO* pColumnInfo  = NULL;
    LPOLESTR pStrings      = NULL;
    if (rs.GetColumnInfo(&ulColumns, &pColumnInfo, &pStrings) != S_OK)
        ThrowMyOLEDBException(rs.m_pRowset, IID_IColumnsInfo);
    struct MYBIND* pBind = new MYBIND[ulColumns];
    rs.CreateAccessor(ulColumns, &pBind[0], sizeof(MYBIND)*ulColumns);
    for (ULONG l=0; l<ulColumns; l++)
    rs.AddBindEntry(l+1, DBTYPE_STR, sizeof(TCHAR)*40, &pBind[l].szValue, NULL, &pBind[l].dwStatus);
    rs.Bind();
    ```

1. Escribir un **mientras** bucle para recuperar los datos. En el bucle, llame a `MoveNext` para avanzar el cursor y probar el valor devuelto de S_OK, como se muestra en el ejemplo siguiente:

    ```cpp
    while (rs.MoveNext() == S_OK)
    {
        // Add code to fetch data here
        // If you are not using an auto accessor, call rs.GetData()
    }
    ```

1. Dentro de la **mientras** bucle, se pueden recuperar los datos según el tipo de descriptor de acceso.

   - Si usas el [CAccessor](../../data/oledb/caccessor-class.md) (clase), debe tener un registro de usuario que contiene los miembros de datos. Puede tener acceso a los datos de uso de esos miembros de datos, como se muestra en el ejemplo siguiente:

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members directly. In this case, m_nFooID
            // is declared in a user record that derives from
            // CAccessor
            wsprintf_s("%d", rs.m_nFooID);
        }
        ```

   - Si usas el `CDynamicAccessor` o `CDynamicParameterAccessor` (clase), se pueden recuperar datos mediante el uso de las funciones de acceso `GetValue` y `GetColumn`, como se muestra en el ejemplo siguiente. Si desea determinar el tipo de datos que está usando, use `GetType`.

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the dynamic accessor functions to retrieve your data.

            ULONG ulColumns = rs.GetColumnCount();
            for (ULONG i=0; i<ulColumns; i++)
            {
                rs.GetValue(i);
            }
        }
        ```

   - Si usa `CManualAccessor`, debe especificar sus propios miembros de datos, enlazar usted mismo y tener acceso a ellos directamente, como se muestra en el ejemplo siguiente:

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members you specified in the calls to
            // AddBindEntry.

            wsprintf_s("%s", szFoo);
        }
        ```

## <a name="see-also"></a>Vea también

[Trabajar con plantillas de consumidor OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
