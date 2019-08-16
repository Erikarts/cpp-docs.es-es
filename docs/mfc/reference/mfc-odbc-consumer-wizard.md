---
title: Asistente para consumidores ODBC MFC
ms.date: 05/09/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: 2e8741677031ff9b12989d75243a13550d74b608
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707383"
---
# <a name="mfc-odbc-consumer-wizard"></a>Asistente para consumidores ODBC MFC

::: moniker range="vs-2019"

Este asistente no está disponible en Visual Studio de 2019 y versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

Este asistente configura una clase de conjunto de registros ODBC y los enlaces de datos necesario para tener acceso al origen de datos especificado.

## <a name="uielement-list"></a>Lista de UIElement

- **Origen de datos**

  El **origen de datos** botón le permite configurar el origen de datos especificado mediante el controlador ODBC especificado. Para obtener más información acerca de los archivos de origen de datos (DSN), consulte [orígenes de datos de archivo](/sql/odbc/reference/file-data-sources) en el SDK de ODBC.

  El **Seleccionar origen de datos** cuadro de diálogo tiene dos pestañas:

  - **Origen de datos de archivo** pestaña:

     El **buscar en** cuadro especifica el directorio en el que se va a seleccionar los archivos que se usarán como orígenes de datos. El valor predeterminado es \Program Files\Common Files\ODBC\Data Sources. Los orígenes de datos de archivo existente (archivos .dsn) aparecen en el cuadro de lista principal. Puede configurar los orígenes de datos antes de tiempo mediante la **DSN de archivo** ficha la [Administrador de orígenes de datos ODBC](/sql/odbc/admin/odbc-data-source-administrator), o crear otros nuevos mediante este cuadro de diálogo.

     Para crear un nuevo origen de datos de archivo desde este cuadro de diálogo, haga clic en `New` para especificar un nombre DSN; el **crear nuevo origen de datos** aparece el cuadro de diálogo. En el **crear nuevo origen de datos** diálogo cuadro, seleccione un controlador apropiado y haga clic en `Next`; haga clic en **examinar**y seleccione el nombre del archivo que se usará como un origen de datos (tiene que seleccionar "Todos los archivos" en vista que no sean archivos DSN, como los archivos .xls); Haga clic en `Next`y, a continuación, haga clic en **finalizar**. (Si ha seleccionado un archivo no DSN, obtendrá un cuadro de diálogo específico del controlador, como "ODBC Microsoft Excel Setup", que se convertirá el archivo a un DSN.)

     > [!NOTE]
     > También puede crear un nuevo origen de datos de archivo con antelación mediante el Administrador de orígenes de datos ODBC. Desde el **iniciar** menú, seleccione **configuración**, **Panel de Control**, **herramientas administrativas**, **deorígenesdedatos(ODBC)** y, a continuación, **Administrador de orígenes de datos ODBC**.

     El **nombre DSN** cuadro le permite especificar un nombre para el origen de datos de archivo. Debe asegurarse de que el nombre DSN termina con la extensión de archivo apropiado, como .xls para archivos de Excel o .mdb para acceder a los archivos.

     Para obtener más información acerca de DNS, consulte [orígenes de datos de archivo](/sql/odbc/reference/file-data-sources) en el SDK de ODBC.

  - **Máquina de origen de datos** pestaña:

     Esta pestaña muestra los orígenes de datos de usuario y del sistema. Orígenes de datos de usuario son específicos para un usuario en este equipo. Orígenes de datos del sistema se pueden usar todos los usuarios en este equipo o en un servicio en todo el sistema. Consulte [Machine orígenes de datos](/sql/odbc/reference/machine-data-sources) en el SDK de ODBC

     Para obtener más información sobre orígenes de datos ODBC, vea [orígenes de datos](/sql/odbc/reference/data-sources) en el SDK de ODBC.

  Haga clic en **Aceptar** para finalizar. El **seleccionar un objeto de base de datos** aparece el cuadro de diálogo. En este cuadro de diálogo, seleccione la tabla o ver que el consumidor usará. Tenga en cuenta que puede seleccionar varias tablas y vistas, mantenga presionada la tecla CTRL mientras hace clic en los elementos. Haga clic en **Aceptar** para finalizar.

- **Clase**

      The name of the consumer class, based by default on the name of the file or machine data source that you selected.

- **Archivo .h**

   El nombre del archivo de encabezado de clase de consumidor, según el nombre del origen de datos de archivo o equipo que ha seleccionado de forma predeterminada.

- **Archivo .cpp**

   El nombre del archivo de implementación de clase de consumidor, según el nombre del origen de datos de archivo o equipo que ha seleccionado de forma predeterminada.

- **Type**

   Especifica si el conjunto de registros es de tipo dinámico (predeterminado) o una instantánea.

   - **Dynaset**: Especifica que el conjunto de registros es de tipo dinámico. Tipo dinámico es el resultado de una consulta que proporciona una vista indizada en datos la base de consultada. Un conjunto de registros dinámicos almacena en caché sólo un índice entero para los datos originales y, por tanto, ofrece un rendimiento descanse una instantánea. El índice apunta directamente a cada registro encontrados como resultado de una consulta y se indica si se quita un registro. También tendrá acceso a la información actualizada en los registros consultados. Este es el valor predeterminado.

   - **Instantánea**: Especifica que el conjunto de registros es una instantánea. Una instantánea es el resultado de una consulta y es una vista en una base de datos en un momento dado. Todos los registros encontrados como resultado de la consulta se almacenan en caché, por lo que no verá los cambios realizados en los registros originales.

- **Enlazar todas las columnas**

   Especifica si todas las columnas de la tabla seleccionada están enlazadas. Si selecciona esta casilla (predeterminado), se enlazan todas las columnas; Si no selecciona esta casilla, no hay columnas se enlazan y debe enlazar manualmente en la clase de conjunto de registros.

::: moniker-end

## <a name="see-also"></a>Vea también

[Consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)
