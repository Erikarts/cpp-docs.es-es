---
title: Mostrar y manipular datos en un formulario
ms.date: 11/04/2016
helpviewer_keywords:
- forms [C++], displaying data
- displaying data [C++], forms
- ODBC [C++], forms
- record views [C++], displaying data
- data [MFC]
- data [MFC], displaying in a form
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
ms.openlocfilehash: e50c433e701fbae2e607d79d7abb34efe8eba5b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395916"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>Mostrar y manipular datos en un formulario

Muchas aplicaciones de acceso a datos seleccione datos y mostrarlos en los campos de un formulario. La clase base de datos [CRecordView](../../mfc/reference/crecordview-class.md) le ofrece un [CFormView](../../mfc/reference/cformview-class.md) objeto conectado directamente a un objeto de conjunto de registros. La vista de registros usa [intercambio de datos de cuadro de diálogo (DDX)](../../mfc/dialog-data-exchange-and-validation.md) para mover los valores de los campos del registro actual del conjunto de registros a los controles del formulario y devolver la información actualizada para el conjunto de registros. El conjunto de registros, a su vez, usa intercambio de campos de registros (RFX) para mover datos entre sus miembros de datos de campo y las columnas correspondientes de una tabla en el origen de datos.

Puede usar el Asistente para aplicaciones MFC o **Agregar clase** (como se describe en [agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) para crear la clase de vista y su clase de conjunto de registros asociado conjuntamente.

La vista de registros y su conjunto de registros se destruyen al cerrar el documento. Para obtener más información acerca de las vistas de registros, vea [vistas de registros](../../data/record-views-mfc-data-access.md). Para obtener más información sobre RFX, consulte [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Vea también

[ODBC y MFC](../../data/odbc/odbc-and-mfc.md)