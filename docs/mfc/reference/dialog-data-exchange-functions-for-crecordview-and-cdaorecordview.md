---
title: Funciones de intercambio de datos de cuadro de diálogo para CRecordView y CDaoRecordView
ms.date: 11/04/2016
f1_keywords:
- AFXDAO/DDX_FieldCBIndex
- AFXDAO/DDX_FieldCBString
- AFXDAO/DDX_FieldCBStringExact
- AFXDAO/DDX_FieldCheck
- AFXDAO/DDX_FieldLBIndex
- AFXDAO/DDX_FieldLBString
- AFXDAO/DDX_FieldLBStringExact
- AFXDAO/DDX_FieldRadio
- AFXDAO/DDX_FieldScroll
- AFXDAO/DDX_FieldText
helpviewer_keywords:
- DDX_Field functions [MFC]
- ODBC [MFC], dialog data exchange (DDX) support
- DDX (dialog data exchange) [MFC], database support
- DDX (dialog data exchange) [MFC], functions
- databases [MFC], dialog data exchange (DDX) support
- DAO [MFC], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
ms.openlocfilehash: 2a794d16b2f94bf8ba66b6c0398dec262d8829e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322558"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>Funciones de intercambio de datos de cuadro de diálogo para CRecordView y CDaoRecordView

Este tema enumeran las funciones DDX_Field utilizadas para intercambiar datos entre un [CRecordset](../../mfc/reference/crecordset-class.md) y un [CRecordView](../../mfc/reference/crecordview-class.md) formulario o un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) y un [ CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) formulario.

> [!NOTE]
>  DDX_Field (funciones) son como las DDX funciones que intercambian datos con controles en un formulario. Pero a diferencia de DDX, que intercambian datos con los campos del objeto de conjunto de registros asociado de la vista en lugar de con campos de la vista del registro. Para obtener más información, vea clases `CRecordView` y `CDaoRecordView`.

### <a name="ddxfield-functions"></a>DDX_Field (funciones)

|||
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|Transfiere datos enteros entre un miembro de datos del campo de conjunto de registros y el índice de la selección actual en un cuadro combinado en un [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md).|
|[DDX_FieldCBString](#ddx_fieldcbstring)|Las transferencias `CString` cuadro datos entre un miembro de datos del campo de conjunto de registros y el control de edición de un cuadro combinado un `CRecordView` o `CDaoRecordView`. Al mover datos desde el conjunto de registros para el control, esta función selecciona el elemento en el cuadro combinado que comienza con los caracteres de la cadena especificada.|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|Las transferencias `CString` cuadro datos entre un miembro de datos del campo de conjunto de registros y el control de edición de un cuadro combinado un `CRecordView` o `CDaoRecordView`. Al mover datos desde el conjunto de registros para el control, esta función selecciona el elemento en el cuadro combinado que coincida exactamente con la cadena especificada.|
|[DDX_FieldCheck](#ddx_fieldcheck)|Transfiere datos Boolean entre un miembro de datos del campo de conjunto de registros y una casilla en un `CRecordView` o `CDaoRecordView`.|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|Transfiere datos enteros entre un miembro de datos del campo de conjunto de registros y el índice de la selección actual en un cuadro de lista en un `CRecordView` o `CDaoRecordView`.|
|[DDX_FieldLBString](#ddx_fieldlbstring)|Administra la transferencia de [CString](../../atl-mfc-shared/reference/cstringt-class.md) datos entre un control de cuadro de lista y los miembros de datos de campo de un conjunto de registros. Al mover datos desde el conjunto de registros para el control, esta función selecciona el elemento en el cuadro de lista que comienza con los caracteres de la cadena especificada.|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|Administra la transferencia de `CString` datos entre un control de cuadro de lista y los miembros de datos de campo de un conjunto de registros. Al mover datos desde el conjunto de registros para el control, esta función selecciona el primer elemento que coincida exactamente con la cadena especificada.|
|[DDX_FieldRadio](#ddx_fieldradio)|Transfiere datos enteros entre un miembro de datos del campo de conjunto de registros y un grupo de botones de radio en un `CRecordView` o `CDaoRecordView`.|
|[DDX_FieldScroll](#ddx_fieldscroll)|Establece u obtiene la posición de desplazamiento de un control de barra de desplazamiento en un `CRecordView` o `CDaoRecordView`. Llamar desde su [DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) función.|
|[DDX_FieldSlider](#ddx_fieldslider)|Sincroniza la posición del control de posición de un control deslizante en una vista de registros y un `int` miembro de datos de campo de un conjunto de registros. |
|[DDX_FieldText](#ddx_fieldtext)|Están disponibles para transferir versiones sobrecargadas `int`, **UINT**, **largo**, `DWORD`, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float** , **doble**, **corto**, [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md), y [COleCurrency](../../mfc/reference/colecurrency-class.md) datos entre un miembro de datos del campo de conjunto de registros y una edición cuadro un `CRecordView` o `CDaoRecordView`.|

##  <a name="ddx_fieldcbindex"></a>  DDX_FieldCBIndex

El `DDX_FieldCBIndex` función sincroniza el índice del elemento seleccionado en el control de cuadro de lista de un control de cuadro combinado en una vista de registros y un `int` miembro de datos de campo de un conjunto de registros asociado con la vista de registros.

```
void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*index*<br/>
Una referencia a un miembro de datos de campo en el asociado `CRecordset` o `CDaoRecordset` objeto.

*pRecordset*<br/>
Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos del objeto.

### <a name="remarks"></a>Comentarios

Al mover datos desde el conjunto de registros para el control, esta función establece la selección del control en función del valor especificado en *índice*. En una transferencia desde el conjunto de registros para el control, si el campo de conjunto de registros es Null, MFC establece el valor del índice en 0. En la transferencia del control al conjunto de registros, si el control está vacío o si se selecciona ningún elemento, el campo de conjunto de registros se establece en 0.

Si está trabajando con las clases basadas en ODBC, utilice la primera versión. Use la segunda versión, si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, consulte el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. El ejemplo también serían similar `DDX_FieldCBIndex`.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

##  <a name="ddx_fieldcbstring"></a>  DDX_FieldCBString

El `DDX_FieldCBString` administra la transferencia de la función [CString](../../atl-mfc-shared/reference/cstringt-class.md) datos entre el control de edición de un control de cuadro combinado en una vista de registros y un `CString` miembro de datos de campo de un conjunto de registros asociado con la vista de registros.

```
void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*value*<br/>
Una referencia a un miembro de datos de campo en el asociado `CRecordset` o `CDaoRecordset` objeto.

*pRecordset*<br/>
Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos del objeto.

### <a name="remarks"></a>Comentarios

Al mover datos desde el conjunto de registros para el control, esta función establece la selección actual en el cuadro combinado a la primera fila que comienza con los caracteres de la cadena especificada en *valor*. En una transferencia desde el conjunto de registros para el control, si el campo de conjunto de registros es Null, se quita cualquier selección de cuadro combinado y el control de edición del cuadro combinado está establecido como vacío. En la transferencia del control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en Null si el campo lo permite.

Si está trabajando con las clases basadas en ODBC, utilice la primera versión. Use la segunda versión, si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, consulte el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. El ejemplo incluye una llamada a `DDX_FieldCBString`.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

## <a name="ddx_fieldcbstringexact"></a>  DDX_FieldCBStringExact

El `DDX_FieldCBStringExact` administra la transferencia de la función [CString](../../atl-mfc-shared/reference/cstringt-class.md) datos entre el control de edición de un control de cuadro combinado en una vista de registros y un `CString` miembro de datos de campo de un conjunto de registros asociado con la vista de registros.

```
void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*value*<br/>
Una referencia a un miembro de datos de campo en el asociado `CRecordset` o `CDaoRecordset` objeto.

*pRecordset*<br/>
Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos del objeto.

### <a name="remarks"></a>Comentarios

Al mover datos desde el conjunto de registros para el control, esta función establece la selección actual en el cuadro combinado a la primera fila que coincida exactamente con la cadena especificada en *valor*. En una transferencia desde el conjunto de registros para el control, si el campo de conjunto de registros es NULL, se quita cualquier selección de cuadro combinado y el cuadro de edición del cuadro combinado está establecido como vacío. En la transferencia del control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en NULL.

Si está trabajando con las clases basadas en ODBC, utilice la primera versión. Use la segunda versión, si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, consulte el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las llamadas a `DDX_FieldCBStringExact` sería similar.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

##  <a name="ddx_fieldcheck"></a>  DDX_FieldCheck

El `DDX_FieldCheck` administra la transferencia de la función **int** datos entre un control de casilla de verificación en un cuadro de diálogo, vista de formulario o el objeto de vista de control y un **int** miembro de datos del cuadro de diálogo, vista de formulario o control objeto de vista.

```
void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de recurso del control de casilla de verificación asociado con la propiedad del control.

*value*<br/>
Una referencia a una variable de miembro del cuadro de diálogo, vista de formulario o con la que se intercambian los datos de objeto de vista de control.

*pRecordset*<br/>
Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos del objeto.

### <a name="remarks"></a>Comentarios

Cuando `DDX_FieldCheck` se llama, *valor* está establecido en el estado actual del control de casilla de verificación, o el estado del control está establecido en *valor*, según la dirección de la transferencia.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

##  <a name="ddx_fieldlbindex"></a>  DDX_FieldLBIndex

El `DDX_FieldLBIndex` función sincroniza el índice del elemento seleccionado en un control de cuadro de lista en una vista de registros y un **int** miembro de datos de campo de un conjunto de registros asociado con la vista de registros.

```
void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*index*<br/>
Una referencia a un miembro de datos de campo en el asociado `CRecordset` o `CDaoRecordset` objeto.

*pRecordset*<br/>
Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos del objeto.

### <a name="remarks"></a>Comentarios

Al mover datos desde el conjunto de registros para el control, esta función establece la selección del control en función del valor especificado en *índice*. En una transferencia desde el conjunto de registros para el control, si el campo de conjunto de registros es Null, MFC establece el valor del índice en 0. En la transferencia del control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en 0.

Si está trabajando con las clases basadas en ODBC, utilice la primera versión. Use la segunda versión, si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, consulte el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

##  <a name="ddx_fieldlbstring"></a>  DDX_FieldLBString

El `DDX_FieldLBString` copia la selección actual de un control de cuadro de lista en una vista de registros a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) miembro de datos de campo de un conjunto de registros asociado con la vista de registros.

```
void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*value*<br/>
Una referencia a un miembro de datos de campo en el asociado `CRecordset` o `CDaoRecordset` objeto.

*pRecordset*<br/>
Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos del objeto.

### <a name="remarks"></a>Comentarios

En la dirección inversa, esta función establece la selección actual en el cuadro de lista a la primera fila que comienza con los caracteres de la cadena especificada por *valor*. En una transferencia desde el conjunto de registros para el control, si el campo de conjunto de registros es Null, se quita cualquier selección en el cuadro de lista. En la transferencia del control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en Null.

Si está trabajando con las clases basadas en ODBC, utilice la primera versión. Use la segunda versión, si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, consulte el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las llamadas a `DDX_FieldLBString` sería similar.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

##  <a name="ddx_fieldlbstringexact"></a>  DDX_FieldLBStringExact

El `DDX_FieldLBStringExact` función copia la selección actual de un control de cuadro de lista en una vista de registros a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) miembro de datos de campo de un conjunto de registros asociado con la vista de registros.

```
void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*value*<br/>
Una referencia a un miembro de datos de campo en el asociado `CRecordset` o `CDaoRecordset` objeto.

*pRecordset*<br/>
Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos del objeto.

### <a name="remarks"></a>Comentarios

En la dirección inversa, esta función establece la selección actual en el cuadro de lista a la primera fila que coincida exactamente con la cadena especificada en *valor*. En una transferencia desde el conjunto de registros para el control, si el campo de conjunto de registros es Null, se quita cualquier selección en el cuadro de lista. En la transferencia del control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en Null.

Si está trabajando con las clases basadas en ODBC, utilice la primera versión. Use la segunda versión, si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, consulte el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las llamadas a `DDX_FieldLBStringExact` sería similar.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

##  <a name="ddx_fieldradio"></a>  DDX_FieldRadio

El `DDX_FieldRadio` función asocia basado en cero **int** variable miembro del conjunto de registros de una vista de registros con el botón de radio seleccionado actualmente en un grupo de botones de radio en la vista de registros.

```
void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de la primera de un grupo (con el estilo WS_GROUP) de los controles de botón de radio adyacentes en la [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*value*<br/>
Una referencia a un miembro de datos de campo en el asociado `CRecordset` o `CDaoRecordset` objeto.

*pRecordset*<br/>
Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos del objeto.

### <a name="remarks"></a>Comentarios

Cuando se transfieren desde el campo de conjunto de registros a la vista, esta función se enciende el *enésimo* botón de radio (basado en cero) y se desactivan los otros botones. En la dirección inversa, esta función establece el campo de conjunto de registros en el número ordinal del botón de radio que se encuentra actualmente en (activado). En una transferencia desde el conjunto de registros para el control, si el campo de conjunto de registros es Null, no se selecciona ningún botón. En la transferencia del control al conjunto de registros, si no se selecciona ningún control, el campo de conjunto de registros se establece en Null si el campo lo permite.

Si está trabajando con las clases basadas en ODBC, utilice la primera versión. Use la segunda versión, si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, consulte el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las llamadas a `DDX_FieldRadio` sería similar.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

##  <a name="ddx_fieldscroll"></a>  DDX_FieldScroll

El `DDX_FieldScroll` función sincroniza la posición de desplazamiento de un control de barra de desplazamiento en una vista de registros y un **int** miembro de datos de campo de un conjunto de registros asociado a la vista de registros (o elija para asignarlo a cualquier variable de entero) .

```
void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de la primera de un grupo (con el estilo WS_GROUP) de los controles de botón de radio adyacentes en la [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*value*<br/>
Una referencia a un miembro de datos de campo en el asociado `CRecordset` o `CDaoRecordset` objeto.

*pRecordset*<br/>
Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos del objeto.

### <a name="remarks"></a>Comentarios

Al mover datos desde el conjunto de registros para el control, esta función establece la posición de desplazamiento de la barra de desplazamiento al valor especificado en *valor*. En una transferencia desde el conjunto de registros para el control, si el campo de conjunto de registros es Null, el control de barra de desplazamiento se establece en 0. En la transferencia del control al conjunto de registros, si el control está vacío, el valor del campo de conjunto de registros es 0.

Si está trabajando con las clases basadas en ODBC, utilice la primera versión. Use la segunda versión, si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, consulte el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las llamadas a `DDX_FieldScroll` sería similar.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

  ## <a name="ddx_fieldslider"></a>  DDX_FieldSlider
El `DDX_FieldSlider` función sincroniza la posición del control de posición de un control deslizante en una vista de registros y un **int** miembro de datos de campo de un conjunto de registros asociado a la vista de registros (o elija para asignarlo a cualquier variable de entero).

### <a name="syntax"></a>Sintaxis

  ```
   void AFXAPI DDX_FieldSlider(
       CDataExchange* pDX,
       int nIDC,
       int& value,
       CRecordset* pRecordset );

void AFXAPI DDX_FieldSlider(
   CDataExchange* pDX,
   int nIDC,
   int& value,
   CDaoRecordset* pRecordset );
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de recurso del control deslizante.

*value*<br/>
Una referencia al valor que se van a intercambiar. Este parámetro contiene o se usará para establecer la posición de control de posición actual del control deslizante.

*pRecordset*<br/>
Un puntero a la categoría asociada `CRecordset` o `CDaoRecordset` con el que se intercambian los datos del objeto.

### <a name="remarks"></a>Comentarios

Al mover datos desde el conjunto de registros para el control deslizante, esta función establece la posición del control deslizante al valor especificado en *valor*. En una transferencia desde el conjunto de registros para el control, si el campo de conjunto de registros es Null, posición del control deslizante se establece en 0. En una transferencia desde el control al conjunto de registros, si el control está vacío, el valor del campo de conjunto de registros es 0.

`DDX_FieldSlider` no se intercambian información de intervalo con los controles deslizantes capaces de configurar un intervalo en lugar de simplemente una posición.

Utilice el primer reemplazo de la función si está trabajando con las clases basadas en ODBC. Utilice el segundo reemplazo con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para `CRecordView` y `CDaoRecordView` campos, consulte [vistas de registros](../../data/record-views-mfc-data-access.md). Para obtener información acerca de los controles deslizantes, consulte [usar CSliderCtrl](../using-csliderctrl.md).

### <a name="example"></a>Ejemplo

Consulte [DDX_FieldText](#ddx_fieldtext) para obtener un ejemplo de DDX_Field general. Las llamadas a `DDX_FieldSlider` sería similar.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

##  <a name="ddx_fieldtext"></a>  DDX_FieldText

El `DDX_FieldText` administra la transferencia de la función **int**, **corto**, **largo**, DWORD, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **doble**, **BOOL**, o **bytes** datos entre un control de cuadro de edición y los miembros de datos de campo de un conjunto de registros.

```
void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    UINT& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    short& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BOOL& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*nIDC*<br/>
El identificador de un control en el [CRecordView](../../mfc/reference/crecordview-class.md) o [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objeto.

*value*<br/>
Una referencia a un miembro de datos de campo en el asociado `CRecordset` o `CDaoRecordset` objeto. El tipo de datos del valor depende de cuál de las versiones sobrecargadas de `DDX_FieldText` utilice.

*pRecordset*<br/>
Un puntero a la [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) con el que se intercambian los datos del objeto. This (puntero) permite `DDX_FieldText` para detectar y establecer los valores Null.

### <a name="remarks"></a>Comentarios

Para [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objetos, `DDX_FieldText` también administra la transferencia de [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md), y [COleCurrency](../../mfc/reference/colecurrency-class.md) valores. Un control de cuadro de edición vacío indica un valor Null. En una transferencia desde el conjunto de registros para el control, si el campo de conjunto de registros es Null, el cuadro de edición se establece como vacío. En la transferencia del control al conjunto de registros, si el control está vacío, el campo de conjunto de registros se establece en Null.

Usar las versiones con [CRecordset](../../mfc/reference/crecordset-class.md) parámetros si está trabajando con las clases basadas en ODBC. Usar las versiones con [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) parámetros si está trabajando con las clases basadas en DAO.

Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../../mfc/dialog-data-exchange-and-validation.md). Para obtener ejemplos y obtener más información sobre DDX para [CRecordView](../../mfc/reference/crecordview-class.md) y [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) campos, consulte el artículo [vistas de registros](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Ejemplo

La siguiente `DoDataExchange` funcionar para un [CRecordView](../../mfc/reference/crecordview-class.md) contiene `DDX_FieldText` función se llama para tres tipos de datos: `IDC_COURSELIST` es un cuadro combinado; los otros dos controles son cuadros de edición. Para la programación de DAO, el *m_pSet* parámetro es un puntero a un [CRecordset](../../mfc/reference/crecordset-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](mfc-macros-and-globals.md)
