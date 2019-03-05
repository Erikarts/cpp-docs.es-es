---
title: Macros y variables globales de MFC
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros
helpviewer_keywords:
- MFC, global functions and variables
- MFC, macros
- global functions, MFC
- macros, MFC
- global functions [MFC]
- global variables, MFC
- Afx naming convention
- macros
ms.assetid: add4e33f-0e62-4d27-be14-896cb8675d22
ms.openlocfilehash: 27664d4e48c0c4e09439f9e970ded9f2a630d90d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268192"
---
# <a name="mfc-macros-and-globals"></a>Macros y variables globales de MFC

La biblioteca Microsoft Foundation Class puede dividirse en dos secciones principales: (1) las clases MFC y (2) macros y variables globales. Si una función o una variable no es miembro de una clase, es una función o una variable global.

La biblioteca MFC y Active Template Library (ATL) comparten macros de conversión de cadenas. Para obtener más información, consulte [Macros de conversión de cadena](../../atl/reference/string-conversion-macros.md) en la documentación del ATL.

Las macros y funciones globales de MFC proporcionan funcionalidad en las categorías siguientes.

## <a name="general-mfc"></a>MFC general

- [Tipos de datos](data-types-mfc.md)

- [Conversión de tipos de objetos de clase MFC](type-casting-of-mfc-class-objects.md)

- [Servicios del modelo de objeto de tiempo de ejecución](run-time-object-model-services.md)

- [Servicios de diagnóstico](diagnostic-services.md)

- [Procesamiento de excepciones](exception-processing.md)

- [Formato CString y presentación del cuadro de mensaje](cstring-formatting-and-message-box-display.md)

- [Mapas de mensajes](message-map-macros-mfc.md)

- [Asignaciones de interfaz y delegado](delegate-and-interface-maps.md)

- [Módulos y archivos DLL](extension-dll-macros.md)

- [Administración y la información de la aplicación](application-information-and-management.md)

- [Identificadores de comando y de ventana estándar](standard-command-and-window-ids.md)

- [Aplicaciones auxiliares de clase de colección](collection-class-helpers.md)

- [Funciones de mapa de bits grises o interpoladas](gray-and-dithered-bitmap-functions.md)

- [Rutinas de intercambio (DDX) de datos de cuadro de diálogo estándar](standard-dialog-data-exchange-routines.md)

- [Rutinas de validación (DDV) de datos de cuadro de diálogo estándar](standard-dialog-data-validation-routines.md)

- [Mensajes AFX](afx-messages.md)

- [Estilos de control ToolBar](toolbar-control-styles.md)

- [CMFCImagePaintArea::IMAGE_EDIT_MODE (enumeración)](cmfcimagepaintarea-image-edit-mode-enumeration.md)

## <a name="database"></a>Base de datos

- [Las funciones de intercambio de campos (RFX) de registro](record-field-exchange-functions.md) y [funciones de intercambio masivo de campos de registro (RFX masivo)](record-field-exchange-functions.md) para las clases ODBC de MFC

- [Las funciones de intercambio (DFX) de campo de registro](record-field-exchange-functions.md) para las clases DAO de MFC

- [Funciones de intercambio de datos de cuadro de diálogo (DDX) para CRecordView y CDaoRecordView](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md) (clases DAO y ODBC de MFC)

- [Funciones de intercambio (DDX) de datos de cuadro de diálogo para controles OLE](dialog-data-exchange-functions-for-ole-controls.md)

- [Macros y funciones globales para ayudar a llamar directamente a funciones API de Open Database Connectivity (ODBC)](database-macros-and-globals.md)

- [Inicialización del motor de base de datos DAO y terminación](dao-database-engine-initialization-and-termination.md)

## <a name="internet"></a>Internet

- [Funciones globales de análisis de dirección URL de Internet](internet-url-parsing-globals.md)

## <a name="dhtml--dhtml-event-maps"></a>Mapas de eventos DHTML y DHTML

- [Macros de aplicación auxiliar (DDX) de intercambio de datos de cuadro de diálogo DHTML](ddx-dhtml-helper-macros.md)

- [Mapas de eventos DHTML](dhtml-event-maps.md)

## <a name="ole"></a>OLE

- [Inicialización de OLE](ole-initialization.md)

- [Control de la aplicación](application-control.md)

- [Mapas de envío](dispatch-maps.md)

Además, MFC proporciona una función denominada [AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer) que habilita cualquier contenedor OLE desarrollado con MFC 4.0 para poder admitir los controles OLE incrustados.

## <a name="ole-controls"></a>Controles OLE

- [Constantes de tipo de parámetro Variant](variant-parameter-type-constants.md)

- [Acceso a la biblioteca de tipos](type-library-access.md)

- [Páginas de propiedades](property-pages-mfc.md)

- [Mapas de eventos](event-maps.md)

- [Mapas de receptor de eventos](event-sink-maps.md)

- [Mapas de conexiones](connection-maps.md)

- [Registrar controles OLE](registering-ole-controls.md)

- [Los generadores de clases y licencias](class-factories-and-licensing.md)

- [Persistencia de los controles OLE](persistence-of-ole-controls.md)

En la primera parte de esta sección se explica brevemente cada una de las categorías anteriores y se enumera las funciones globales y macros de la categoría, junto con una descripción breve de la funcionalidad. A continuación se encuentran las descripciones de las funciones globales, las variables globales y las macros en la biblioteca MFC.

> [!NOTE]
>  Muchas funciones globales comienzan con el prefijo “Afx”, pero algunas, por ejemplo, las funciones de intercambio de datos de cuadro de diálogo (DDX) y muchas de las funciones de base de datos, no siguen esta convención. Todas las variables globales comienzan con el prefijo "afx". Las macros no comienzan con ningún prefijo concreto, sino que se escriben en letras mayúsculas.

## <a name="see-also"></a>Vea también

[Información general de clases](../../mfc/class-library-overview.md)
