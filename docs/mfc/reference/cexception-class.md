---
title: CException (clase)
ms.date: 11/04/2016
f1_keywords:
- CException
- AFX/CException
- AFX/CException::CException
- AFX/CException::Delete
- AFX/CException::ReportError
helpviewer_keywords:
- CException [MFC], CException
- CException [MFC], Delete
- CException [MFC], ReportError
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
ms.openlocfilehash: 689afa2ffbc27feec6f9e1704a6b295d5eabfaee
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270428"
---
# <a name="cexception-class"></a>CException (clase)

La clase base para todas las excepciones en la biblioteca MFC (Microsoft Foundation Class).

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE CException : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CException::CException](#cexception)|Construye un objeto `CException`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CException::Delete](#delete)|Elimina un `CException` objeto.|
|[CException::ReportError](#reporterror)|Informa de un mensaje de error en un cuadro de mensaje al usuario.|

## <a name="remarks"></a>Comentarios

Dado que `CException` es una clase base abstracta que no se puede crear `CException` objetos directamente, debe crear objetos de clases derivadas. Si tiene que crear las suyas propias `CException`-clase de estilo, use una de las clases derivadas mencionadas anteriormente como un modelo. Asegúrese de que su clase derivada también utiliza `IMPLEMENT_DYNAMIC`.

A continuación se enumeran las clases derivadas y sus descripciones:

|||
|-|-|
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|Una clase base para excepciones MFC recursos críticos|
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Condición de excepción de argumento no válido|
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Excepción de memoria insuficiente|
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Solicitud para una operación no admitida|
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|Excepción de archivo específico|
|[CFileException](../../mfc/reference/cfileexception-class.md)|Excepción de archivo específico|
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|Recursos de Windows no se encuentra o no se pueden crear|
|[COleException](../../mfc/reference/coleexception-class.md)|Excepciones OLE|
|[CDBException](../../mfc/reference/cdbexception-class.md)|Excepción de base de datos (es decir, las condiciones de excepción que se deriven de clases de base de datos MFC en función de conectividad abierta de base de datos)|
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|Excepción de envío (automatización) de OLE|
|[CUserException](../../mfc/reference/cuserexception-class.md)|Excepción que indica que no se pudo encontrar un recurso|
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|Excepción de objeto (es decir, las condiciones de excepción que se deriven de clases DAO) de acceso a datos|
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|Excepción de Internet (es decir, las condiciones de excepción que se deriven de clases de Internet).|

Estas excepciones están diseñadas para usarse con la [THROW](exception-processing.md#throw), [THROW_LAST](exception-processing.md#throw_last), [intente](exception-processing.md#try), [catch](exception-processing.md#catch), [and_catch](exception-processing.md#and_catch), y [end_catch](exception-processing.md#end_catch) macros. Para obtener más información sobre excepciones, vea [procesamiento de excepciones](exception-processing.md), o consulte el artículo [de control de excepciones (MFC)](../exception-handling-in-mfc.md).

Para detectar una excepción concreta, use la clase derivada adecuada. A catch todos los tipos de excepciones, use `CException`y, a continuación, usar [CObject:: IsKindOf](cobject-class.md#iskindof) para diferenciar los `CException`-las clases derivadas. Tenga en cuenta que `CObject::IsKindOf` funciona solo para las clases declaradas con el [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic) macro con el fin de aprovechar las ventajas de la comprobación de tipo dinámico. Cualquier `CException`-debe usar una clase derivada que cree el `IMPLEMENT_DYNAMIC` macro demasiado.

Puede notificar los detalles sobre las excepciones al usuario mediante una llamada a [GetErrorMessage](cfileexception-class.md#geterrormessage) o [ReportError](#reporterror), dos funciones miembro que funcionan con cualquiera de `CException`de las clases derivadas.

Si se detecta una excepción mediante una de las macros, la `CException` objeto se elimina automáticamente; no se elimina por sí mismo. Si se detecta una excepción mediante el uso de un **catch** palabra clave, no se elimina automáticamente. Consulte el artículo [de control de excepciones (MFC)](../exception-handling-in-mfc.md) para obtener más información sobre cuándo se debe eliminar un objeto de excepción.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](cobject-class.md)

`CException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="cexception"></a>  CException::CException

Esta función miembro construye un `CException` objeto.

```
explicit CException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parámetros

*b_AutoDelete*<br/>
Especifique "true" si la memoria para el `CException` se asignó el objeto en el montón. Esto hará que el `CException` objeto que se eliminará cuando el `Delete` función miembro se llama para eliminar la excepción. Especifique FALSE si el `CException` objeto está en la pila o es un objeto global. En este caso, el `CException` objeto no se podrá eliminar cuando el `Delete` se llama a la función miembro.

### <a name="remarks"></a>Comentarios

General, nunca necesitará llamar directamente a este constructor. Una función que produce una excepción debe crear una instancia de un `CException`-clase derivada y llamar a su constructor, o bien debe usar uno de MFC throw funciones, como [AfxThrowFileException](exception-processing.md#afxthrowfileexception), inicien un tipo predefinido. Esta documentación se ofrece únicamente por integridad.

##  <a name="delete"></a>  CException::Delete

Esta función comprueba si el `CException` se creó el objeto en el montón y, si es así, llama a la **eliminar** operador en el objeto.

```
void Delete();
```

### <a name="remarks"></a>Comentarios

Al eliminar un `CException` de objeto, utilice el `Delete` función miembro para eliminar la excepción. No utilice el **eliminar** operador directamente, porque el `CException` objeto puede ser un objeto global o se han creado en la pila.

Puede especificar si se debe eliminar el objeto cuando se construye el objeto. Para obtener más información, consulte [CException::CException](#cexception).

Solo necesita llamar a `Delete` si usas C++ **intente**- **catch** mecanismo. Si está utilizando las macros MFC **intente** y **CATCH**, a continuación, estas macros llamará automáticamente a esta función.

### <a name="example"></a>Ejemplo

```cpp
CFile* pFile = NULL;
// Constructing a CFile object with this override may throw
// a CFile exception, and won't throw any other exceptions.
// Calling CString::Format() may throw a CMemoryException,
// so we have a catch block for such exceptions, too. Any
// other exception types this function throws will be
// routed to the calling function.
// Note that this example performs the same actions as the
// example for CATCH, but uses C++ try/catch syntax instead
// of using the MFC TRY/CATCH macros. This sample must use
// CException::Delete() to delete the exception objects
// before closing the catch block, while the CATCH example
// implicitly performs the deletion via the macros.
try
{
   pFile = new CFile(_T("C:\\WINDOWS\\SYSTEM.INI"),
      CFile::modeRead | CFile::shareDenyNone);
   ULONGLONG ullLength = pFile->GetLength();
   CString str;
   str.Format(_T("Your SYSTEM.INI file is %u bytes long."), ullLength);
   AfxMessageBox(str);
}
catch(CFileException* pEx)
{
   // Simply show an error message to the user.
   pEx->ReportError();
   pEx->Delete();
}
catch(CMemoryException* pEx)
{
   // We can't recover from this memory exception, so we'll
   // just terminate the app without any cleanup. Normally, an
   // an application should do everything it possibly can to
   // clean up properly and _not_ call AfxAbort().
   pEx->Delete();
   AfxAbort();
}
// If an exception occurrs in the CFile constructor,
// the language will free the memory allocated by new
// and will not complete the assignment to pFile.
// Thus, our clean-up code needs to test for NULL.
if (pFile != NULL)
{
   pFile->Close();
   delete pFile;
}
```

##  <a name="reporterror"></a>  CException::ReportError

Llame a esta función miembro para el texto del error del informe en un cuadro de mensaje al usuario.

```
virtual int ReportError(
    UINT nType = MB_OK,
    UINT nMessageID = 0);
```

### <a name="parameters"></a>Parámetros

*nType*<br/>
Especifica el estilo del cuadro de mensaje. Aplicar cualquier combinación de la [estilos de cuadro de mensaje](styles-used-by-mfc.md#message-box-styles) al cuadro. Si no especifica este parámetro, el valor predeterminado es MB_OK.

*nMessageID*<br/>
Especifica el identificador de recurso (entrada de tabla de cadena) de un mensaje para mostrar si el objeto de excepción no tiene un mensaje de error. Si es 0, el mensaje "ningún mensaje de error está disponible" se muestra.

### <a name="return-value"></a>Valor devuelto

Un `AfxMessageBox` valor; en caso contrario, 0 si no hay memoria suficiente para mostrar el cuadro de mensaje. Consulte [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) para los posibles valores devueltos.

### <a name="example"></a>Ejemplo

Este es un ejemplo del uso de `CException::ReportError`. Para obtener otro ejemplo, vea el ejemplo de [CATCH](exception-processing.md#catch).

```cpp
CFile fileInput;
CFileException ex;

// try to open a file for reading.
// The file will certainly not
// exist because there are too many explicit
// directories in the name.

// if the call to Open() fails, ex will be
// initialized with exception
// information.  the call to ex.ReportError() will
// display an appropriate
// error message to the user, such as
// "\Too\Many\Bad\Dirs.DAT contains an
// invalid path."  The error message text will be
// appropriate for the
// file name and error condition.

if (!fileInput.Open(_T("\\Too\\Many\\Bad\\Dirs.DAT"), CFile::modeRead, &ex))
{
  ex.ReportError();
}
else
{
  // the file was opened, so do whatever work
  // with fileInput we were planning...

  fileInput.Close();
}
```

## <a name="see-also"></a>Vea también

[CObject (clase)](cobject-class.md)<br/>
[Gráfico de jerarquías](../hierarchy-chart.md)<br/>
[Procesamiento de excepciones](exception-processing.md)<br/>
[¿Cómo lo hago?: Crear mis propias clases de excepción personalizada](http://go.microsoft.com/fwlink/p/?linkid=128045)
