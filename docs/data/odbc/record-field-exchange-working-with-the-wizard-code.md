---
title: 'Intercambio de campos de registro: Trabajar con el código de Asistente'
ms.date: 11/04/2016
helpviewer_keywords:
- DoFieldExchange method, overriding
- Unicode, with database classes
- field data members, declaring
- RFX (ODBC), wizard code
- RFX (ODBC), implementing
- field data members
- ODBC, RFX
- m_nParams data member, initializing
- m_nFields data member
- m_nParams data member
- overriding, DoFieldExchange
- m_nFields data member, initializing
ms.assetid: f00d882a-ff1b-4a75-9717-98d8762bb237
ms.openlocfilehash: 82f0d946cac3429150250e2df5d1bfd674ec30ee
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041298"
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>Intercambio de campos de registro: Trabajar con el código de Asistente

En este tema se explica el código que el Asistente para aplicaciones MFC y **Agregar clase** (como se describe en [agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) para la compatibilidad con RFX y cómo desea modificar ese código.

> [!NOTE]
>  En este tema se aplica a las clases derivadas de `CRecordset` en qué fila de forma masiva captura no se ha implementado. Si usas la obtención masiva de filas, se implementa el intercambio masivo de campos de registros (RFX masivo). RFX masivo es similar a RFX. Para comprender las diferencias, consulte [conjunto de registros: Obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Cuando crea una clase de conjunto de registros con el Asistente para aplicaciones MFC o **Agregar clase**, el asistente escribe los siguientes elementos relacionados con RFX para usted, basándose en el origen de datos, tabla y opciones de columna que se realice en el Asistente para:

- Declaraciones de los miembros de datos del campo de conjunto de registros en la clase de conjunto de registros

- Una invalidación de `CRecordset::DoFieldExchange`

- Inicialización de miembros de datos de campo de conjunto de registros en el constructor de clase de conjunto de registros

##  <a name="_core_the_field_data_member_declarations"></a> Declaraciones de miembro de datos de campo

El asistente escribe una declaración de clase de conjunto de registros en un archivo .h que es similar al siguiente para la clase `CSections`:

```cpp
class CSections : public CRecordset
{
public:
   CSections(CDatabase* pDatabase = NULL);
   DECLARE_DYNAMIC(CSections)

// Field/Param Data
   CString   m_strCourseID;
   CString   m_strInstructorID;
   CString   m_strRoomNo;
   CString   m_strSchedule;
   CString   m_strSectionNo;

// Overrides
   // Wizard generated virtual function overrides
   protected:
   virtual CString GetDefaultConnect();  // Default connection string
   virtual CString GetDefaultSQL();      // Default SQL for Recordset
   virtual void DoFieldExchange(CFieldExchange* pFX);  // RFX support

// Implementation
#ifdef _DEBUG
   virtual void AssertValid() const;
   virtual void Dump(CDumpContext& dc) const;
#endif

};
```

Si agrega nuevos miembros de datos de campo que enlazan a usted mismo o de los miembros de datos de parámetro, agregue después los generados por el asistente.

Además, tenga en cuenta que el asistente reemplaza el `DoFieldExchange` función miembro de clase `CRecordset`.

##  <a name="_core_the_dofieldexchange_override"></a> Reemplazo de DoFieldExchange

[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) es la esencia de RFX. Las llamadas de framework `DoFieldExchange` siempre que necesita para mover datos de origen de datos al conjunto de registros o de conjunto de registros al origen de datos. `DoFieldExchange` también admite la obtención de información acerca de campo miembros de datos a través de la [IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty) y [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull) funciones miembro.

La siguiente `DoFieldExchange` invalidación es para el `CSections` clase. El asistente escribe la función en el archivo .cpp para la clase de conjunto de registros.

```cpp
void CSections::DoFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   RFX_Text(pFX, "CourseID", m_strCourseID);
   RFX_Text(pFX, "InstructorID", m_strInstructorID);
   RFX_Text(pFX, "RoomNo", m_strRoomNo);
   RFX_Text(pFX, "Schedule", m_strSchedule);
   RFX_Text(pFX, "SectionNo", m_strSectionNo);
}
```

Tenga en cuenta las siguientes características clave de la función:

- En esta sección de la función se llama a la asignación de campo.

- Una llamada a `CFieldExchange::SetFieldType`, mediante el `pFX` puntero. Esta llamada especifica que todas las llamadas de función RFX al final de `DoFieldExchange` o la siguiente llamada a `SetFieldType` columnas de salida. Para obtener más información, consulte [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

- Varias llamadas a la `RFX_Text` función global, una por cada miembro de datos de campo (todas de las cuales se `CString` variables en el ejemplo). Estas llamadas especifican la relación entre un nombre de columna en el origen de datos y un miembro de datos de campo. Las funciones de RFX realizan la transferencia de datos reales. La biblioteca de clases proporciona funciones RFX para todos los tipos de datos comunes. Para obtener más información acerca de las funciones RFX, consulte [intercambio de campos de registro: Uso de las funciones de RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md).

    > [!NOTE]
    >  El orden de las columnas del conjunto de resultados debe coincidir con el orden de las llamadas de función RFX de `DoFieldExchange`.

- El `pFX` puntero a un [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objeto que el marco de trabajo pasa al llamar a `DoFieldExchange`. El `CFieldExchange` objeto especifica la operación que `DoFieldExchange` consiste en llevar a cabo, la dirección de la transferencia y otra información de contexto.

##  <a name="_core_the_recordset_constructor"></a> Constructor de conjunto de registros

El constructor del conjunto de registros que escriben los asistentes contiene dos elementos relacionados con RFX:

- Código de inicialización para cada miembro de datos de campo

- Código de inicialización para la [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) miembro de datos que contiene el número de miembros de datos de campo

El constructor para la `CSections` ejemplo de conjunto de registros tiene este aspecto:

```cpp
CSections::CSections(CDatabase* pdb)
   : CRecordset(pdb)
{
   m_strCourseID = "";
   m_strInstructorID = "";
   m_strRoomNo = "";
   m_strSchedule = "";
   m_strSectionNo = "";
   m_nFields = 5;
}
```

> [!NOTE]
>  Si agrega miembros de datos de campo manualmente, como es posible enlazar nuevas columnas dinámicamente, debe incrementar `m_nFields`. Puede hacerlo agregando la siguiente línea de código, como:

```cpp
m_nFields += 3;
```

Este es el código para agregar tres nuevos campos. Si agrega miembros de datos de parámetro, debe inicializar el [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) miembro de datos que contiene el número de miembros de datos de parámetro. Coloque el `m_nParams` inicialización fuera de las llaves.

## <a name="see-also"></a>Vea también

[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)