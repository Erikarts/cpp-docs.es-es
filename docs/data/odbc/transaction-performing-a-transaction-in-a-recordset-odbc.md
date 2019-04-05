---
title: 'Transacción: Realizar una transacción en un conjunto de registros (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: 9e06d61d3d86233e136b0b3fe78f149a6778649b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035246"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>Transacción: Realizar una transacción en un conjunto de registros (ODBC)

En este tema se explica cómo realizar una transacción en un conjunto de registros.

> [!NOTE]
>  Se admite sólo un nivel de transacciones; no se pueden anidar transacciones.

#### <a name="to-perform-a-transaction-in-a-recordset"></a>Para realizar una transacción en un conjunto de registros

1. Llame a la `CDatabase` del objeto `BeginTrans` función miembro.

1. Si no ha implementado la obtención masiva de filas, llame a la `AddNew/Update`, `Edit/Update`, y `Delete` las funciones miembro de uno o más objetos de conjunto de registros de la misma base de datos tantas veces como sea necesario. Para obtener más información, consulte [conjunto de registros: Agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md). Si ha implementado la obtención masiva de filas, debe escribir sus propias funciones para actualizar el origen de datos.

1. Por último, llame a la `CDatabase` del objeto `CommitTrans` función miembro. Si se produce un error en una de las actualizaciones o si decide cancelar los cambios, llame a su `Rollback` función miembro.

El ejemplo siguiente utiliza dos conjuntos de registros para eliminar la inscripción de un estudiante de una base de datos de registro de escuela, quitando los estudiantes de todas las clases en el que está inscrito el alumno. Dado que el `Delete` deben completarse correctamente las llamadas en ambos conjuntos de registros, se requiere una transacción. En el ejemplo se presupone la existencia de `m_dbStudentReg`, una variable de miembro de tipo `CDatabase` ya conectado al origen de datos y las clases de conjunto de registros `CEnrollmentSet` y `CStudentSet`. El `strStudentID` variable contiene un valor obtenido del usuario.

```
BOOL CEnrollDoc::RemoveStudent( CString strStudentID )
{
    // remove student from all the classes
    // the student is enrolled in

    if ( !m_dbStudentReg.BeginTrans( ) )
        return FALSE;

    CEnrollmentSet rsEnrollmentSet(&m_dbStudentReg);
    rsEnrollmentSet.m_strFilter = "StudentID = " + strStudentID;

    if ( !rsEnrollmentSet.Open(CRecordset::dynaset) )
        return FALSE;

    CStudentSet rsStudentSet(&m_dbStudentReg);
    rsStudentSet.m_strFilter = "StudentID = " + strStudentID;

    if ( !rsStudentSet.Open(CRecordset::dynaset) )
        return FALSE;

    TRY
    {
        while ( !rsEnrollmentSet.IsEOF( ) )
        {
            rsEnrollmentSet.Delete( );
            rsEnrollmentSet.MoveNext( );
        }

        // delete the student record
        rsStudentSet.Delete( );

        m_dbStudentReg.CommitTrans( );
    }

    CATCH_ALL(e)
    {
        m_dbStudentReg.Rollback( );
        return FALSE;
    }
    END_CATCH_ALL

    rsEnrollmentSet.Close( );
    rsStudentSet.Close( );

    return TRUE;

}
```

> [!NOTE]
>  Una llamada a `BeginTrans` nuevo sin llamar a `CommitTrans` o `Rollback` es un error.

## <a name="see-also"></a>Vea también

[Transacción (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transacción: Cómo afectan las transacciones a las actualizaciones (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[CDatabase (clase)](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)