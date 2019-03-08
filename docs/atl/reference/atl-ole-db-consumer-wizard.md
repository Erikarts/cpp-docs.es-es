---
title: Asistente para consumidores OLE DB ATL
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.consumer.overview
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- connection strings [C++], OLE DB consumers
- ATL OLE DB Consumer Wizard
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
ms.openlocfilehash: 59ad635f62ab7a20a31de7255ec4522136e102ec
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524136"
---
# <a name="atl-ole-db-consumer-wizard"></a>Asistente para consumidores OLE DB ATL

Este asistente configura una clase de consumidor OLE DB con los enlaces de datos necesario para tener acceso al origen de datos especificado a través del proveedor OLE DB especificado.

> [!NOTE]
> Este asistente requiere que haga clic en el **origen de datos** para seleccionar un origen de datos antes de escribir los nombres en el `Class` y **archivo .h** campos.

## <a name="uielement-list"></a>Lista de UIElement

- **Origen de datos**

   El **origen de datos** botón le permite configurar el origen de datos especificado mediante el proveedor OLE DB especificado. Al hacer clic en este botón, el **propiedades de vínculo de datos** aparece el cuadro de diálogo. Para obtener más información sobre la creación de cadenas de conexión y la **propiedades de vínculo de datos** cuadro de diálogo, vea [Introducción a la API de vínculo de datos](/previous-versions/windows/desktop/ms718102) en la documentación del SDK de Windows.

   La siguiente información adicional describe las pestañas en el **propiedades de vínculo de datos** cuadro de diálogo.

   - **Proveedor** ficha

      Seleccione el proveedor apropiado para administrar la conexión al origen de datos. El tipo de proveedor normalmente viene determinada por el tipo de base de datos al que se está conectando. Haga clic en el **siguiente** botón o haga clic en el **conexión** ficha.

   - **Conexión** ficha

      El contenido de esta pestaña depende del proveedor seleccionado. Aunque hay muchos tipos de proveedores, en esta sección se trata las conexiones para los dos más comunes: datos de SQL y ODBC. Los demás son similares variaciones en los campos que se describen aquí.

      Para los datos SQL:

      1. **Seleccione o escriba un nombre de servidor:** haga clic en el menú de lista desplegable para mostrar todos los servidores de datos registrados en la red y seleccionar uno.

      1. **Escriba la información para iniciar sesión en el servidor:** escriba un nombre de usuario y una contraseña para iniciar sesión en el servidor de datos.

         > [!NOTE]
         > Hay un problema de seguridad con la característica de "Permitir guardar contraseña" del cuadro de diálogo Propiedades de vínculo de datos. En "Especifique la información para iniciar sesión en el servidor", hay dos botones de opción:
         >
         > - **Usar seguridad integrada de Windows NT**
         > - **Usar un nombre de usuario específico y una contraseña**
         >
         > Si selecciona **utilizar un nombre de usuario específico y una contraseña**, tiene la opción de guardar la contraseña (mediante la casilla de verificación para "Permitir guardar contraseña"); sin embargo, esta opción no es segura. Se recomienda que seleccione **seguridad integrada de uso Windows NT**; esta opción es segura porque cifra la contraseña.
         > Puede haber situaciones en las que desea seleccionar "Permitir guardar contraseña". Por ejemplo, si está lanzando una biblioteca con una solución de base de datos privado, debe no tener acceso directamente a la base de datos pero en su lugar, use una aplicación de nivel intermedio para comprobar el usuario (a través de cualquier esquema de autenticación que elija) y, a continuación, limitar al tipo de datos disponible para el usuario.

      1. **Seleccione la base de datos en el servidor:** haga clic en el menú de lista desplegable para mostrar todas las instancias registradas de bases de datos en el servidor de datos y seleccione uno.

         \- o -

         **Adjuntar un archivo de base de datos como un nombre de base de datos:** especificar un archivo que se usará como la base de datos; escriba la ruta de acceso explícita.

      Para los datos ODBC:

      1. **Especifique el origen de datos:** puede usar un nombre de origen de datos o una cadena de conexión.

         **Nombre del origen de datos de uso:** esta lista desplegable muestra los orígenes de datos registrados en su equipo. Puede configurar los orígenes de datos antes de tiempo mediante el Administrador de orígenes de datos ODBC

         \- o -

         **Usar cadena de conexión:** escriba una cadena de conexión que ya ha obtenido o haga clic en el **compilar** botón; el **Seleccionar origen de datos** aparece el cuadro de diálogo. Seleccione un origen de datos de archivo o equipo y haga clic en **Aceptar**.

         > [!NOTE]
         > Puede obtener una cadena de conexión mediante la visualización de las propiedades de una conexión existente en **Explorador de servidores**, o bien puede crear una conexión haciendo doble clic en **Agregar conexión** en **Server Explorador**.

      1. **Escriba la información para iniciar sesión en el servidor:** escriba un nombre de usuario y una contraseña para iniciar sesión en el servidor de datos.

      1. Escriba el catálogo inicial que se usará.

      1. Haga clic en **Probar conexión**; si la prueba se realiza correctamente, haga clic en **Aceptar**. Si no es así, compruebe la información de inicio de sesión, intente otra base de datos o pruebe con otro servidor de datos.

   - **Advanced** ficha

      **Configuración de red:** especifique el **nivel de suplantación** (el nivel de suplantación que el servidor está autorizado para usar al suplantar al cliente; se corresponde directamente con los niveles de suplantación de RPC) y  **Nivel de protección** (el nivel de protección de datos enviados entre cliente y servidor; se corresponde directamente con los niveles de protección de RPC).

      **Sí:** en **Connect timeout**, especifique el número de segundos de tiempo de inactividad permitido antes de que se produce un tiempo de espera. En **permisos de acceso**, especifique los permisos de acceso en la conexión de datos.

      Para obtener más información acerca de las propiedades de inicialización avanzadas, consulte la documentación suministrada con cada proveedor OLE DB.

   - **Todos los** ficha

      Esta pestaña muestra un resumen de las propiedades de inicialización para el origen de datos y la conexión que ha especificado. Puede editar estos valores.

      Haga clic en **Aceptar** para finalizar. El **seleccionar un objeto de base de datos** aparece el cuadro de diálogo. En este cuadro de diálogo, seleccione la tabla, vista o procedimiento almacenado que se va a usar el consumidor.

- **Clase**

   Después de seleccionar un origen de datos, este cuadro se rellena con un nombre de clase predeterminado basado en la tabla o procedimiento almacenado que seleccionó (vea **seleccionar un origen de datos** a continuación). Puede editar el nombre de clase.

- **Archivo .h**

   Después de seleccionar un origen de datos, este cuadro se rellena con un nombre de clase de encabezado predeterminada en función de la tabla o procedimiento almacenado que seleccionó (vea **seleccionar un origen de datos** a continuación). Puede editar el nombre del archivo de encabezado o seleccionar un archivo de encabezado existente.

- **Con atributos**

   Esta opción especifica si el asistente creará clases de consumidor con atributos o definiciones de plantilla. Cuando se selecciona esta opción, el asistente utiliza atributos en lugar de declaraciones de plantilla (es decir, la opción predeterminada). Cuando se desactiva esta opción, el asistente utiliza las declaraciones de plantilla en lugar de atributos.

   - Si selecciona un consumidor **tipo** de **tabla**, usa el Asistente para la `db_source` y `db_table` atributos para crear la tabla y el descriptor de acceso de tabla declaraciones de clase y usa `db_column` a crear el mapa de columnas. Por ejemplo, crea este mapa:

        ```cpp
        // Inject table class and table accessor class declarations
        [db_source("<initialization_string>"), db_table("dbo.Orders")]
        ...
        // Column map
        [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;
        [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];
        ...
        ```

      en lugar de usar el `CTable` clase de plantilla para declarar la tabla y clase de descriptor de acceso de la tabla y las macros BEGIN_COLUMN_MAP y END_COLUMN_MAP para crear el mapa de columnas, como en este ejemplo:

        ```cpp
        // Table accessor class
            class COrdersAccessor; // Table class
            class COrders : public CTable<CAccessor<COrdersAccessor>>;
        // ...
        // Column map
            BEGIN_COLUMN_MAP(COrderDetailsAccessor)
                COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID, m_dwOrderIDLength, m_dwOrderIDStatus)
                COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID, m_dwCustomerIDLength, m_dwCustomerIDStatus)
                // ...
            END_COLUMN_MAP()
        ```

   - Si selecciona un consumidor **tipo** de **comando**, usa el Asistente para la `db_source` y `db_command` atributos y usa `db_column` para crear el mapa de columnas. Por ejemplo, crea este mapa:

        ```cpp
        [db_source("<initialization_string>"), db_command("SQL_command")]
        ...
        // Column map using db_column is the same as for consumer type of 'table'
        ```

      en lugar de usar el comando y declaraciones de clase de descriptor de acceso de comando en el archivo .h de la clase de comando, por ejemplo:

        ```cpp
        // Command accessor class:
            class CListOrdersAccessor;
        // Command class:
            class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;
        // ...
        // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
        // for consumer type of 'table'
        ```

      Consulte [mecanismos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md) para obtener más información.

- **Type**

   Seleccione uno de estos botones de radio para especificar si la clase de consumidor se derivará de `CTable` o `CCommand` (valor predeterminado).

   - **Table**

      Seleccione esta opción si desea usar `CTable` o `db_table` para crear la tabla y el descriptor de acceso de tabla de declaraciones de clase.

   - **Comando**

      Seleccione esta opción si desea usar `CCommand` o `db_command` para crear el comando y el descriptor de acceso de comando declaraciones de clase. Esta es la selección predeterminada.

- **Soporte técnico**

   Seleccione las casillas de verificación para especificar los tipos de actualizaciones que se aceptan en el consumidor (el valor predeterminado es none). Cada una de las siguientes acciones establecerá [DBPROP_IRowsetChange](/previous-versions/windows/desktop/ms715892) y las entradas adecuadas para [DBPROP_UPDATABILITY](/previous-versions/windows/desktop/ms722676) en la propiedad establece el mapa.

   - **Cambio**

      Especifica que el consumidor admiten las actualizaciones de datos de fila en el conjunto de filas.

   - **Insertar**

      Especifica que el consumidor acepta la inserción de filas en el conjunto de filas.

   - **Eliminar**

      Especifica que el consumidor admite la eliminación de filas del conjunto de filas.

## <a name="see-also"></a>Vea también

[Consumidor OLE DB ATL](../../atl/reference/adding-an-atl-ole-db-consumer.md)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Las cadenas de conexión y vínculos de datos (OLE DB)](/previous-versions/windows/desktop/ms718376)
