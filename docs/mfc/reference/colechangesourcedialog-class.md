---
title: COleChangeSourceDialog (clase)
ms.date: 11/04/2016
f1_keywords:
- COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::DoModal
- AFXODLGS/COleChangeSourceDialog::GetDisplayName
- AFXODLGS/COleChangeSourceDialog::GetFileName
- AFXODLGS/COleChangeSourceDialog::GetFromPrefix
- AFXODLGS/COleChangeSourceDialog::GetItemName
- AFXODLGS/COleChangeSourceDialog::GetToPrefix
- AFXODLGS/COleChangeSourceDialog::IsValidSource
- AFXODLGS/COleChangeSourceDialog::m_cs
helpviewer_keywords:
- COleChangeSourceDialog [MFC], COleChangeSourceDialog
- COleChangeSourceDialog [MFC], DoModal
- COleChangeSourceDialog [MFC], GetDisplayName
- COleChangeSourceDialog [MFC], GetFileName
- COleChangeSourceDialog [MFC], GetFromPrefix
- COleChangeSourceDialog [MFC], GetItemName
- COleChangeSourceDialog [MFC], GetToPrefix
- COleChangeSourceDialog [MFC], IsValidSource
- COleChangeSourceDialog [MFC], m_cs
ms.assetid: d0e08be7-21ef-45e1-97af-fe27d99e3bac
ms.openlocfilehash: 1d118b132fc110402967e9c7f2b1d74a2164d7c8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304618"
---
# <a name="colechangesourcedialog-class"></a>COleChangeSourceDialog (clase)

Se utiliza en el cuadro de diálogo Cambiar origen de OLE.

## <a name="syntax"></a>Sintaxis

```
class COleChangeSourceDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[COleChangeSourceDialog::COleChangeSourceDialog](#colechangesourcedialog)|Construye un objeto `COleChangeSourceDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleChangeSourceDialog::DoModal](#domodal)|Muestra el cuadro de diálogo origen de OLE cambio.|
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|Obtiene el nombre para mostrar código fuente completo.|
|[COleChangeSourceDialog::GetFileName](#getfilename)|Obtiene el nombre de archivo desde el nombre de origen.|
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|Obtiene el prefijo de origen anterior.|
|[COleChangeSourceDialog::GetItemName](#getitemname)|Obtiene el nombre del elemento desde el nombre de origen.|
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|Obtiene el prefijo del nuevo origen|
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|Indica si el origen es válido.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[COleChangeSourceDialog::m_cs](#m_cs)|Una estructura que controla el comportamiento del cuadro de diálogo.|

## <a name="remarks"></a>Comentarios

Crear un objeto de clase `COleChangeSourceDialog` cuando desee llamar a este cuadro de diálogo. Después de un `COleChangeSourceDialog` se ha construido el objeto, puede usar el [m_cs](#m_cs) estructura para inicializar los valores o los Estados de los controles en el cuadro de diálogo. El `m_cs` estructura es de tipo [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea). Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea el [DoModal](#domodal) función miembro.

Para obtener más información, consulte el [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) estructura en el SDK de Windows.

Para obtener más información acerca de los cuadros de diálogo específicos de OLE, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeSourceDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs.h

##  <a name="colechangesourcedialog"></a>  COleChangeSourceDialog::COleChangeSourceDialog

Esta función construye un `COleChangeSourceDialog` objeto.

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero a la que está vinculada [COleClientItem](../../mfc/reference/coleclientitem-class.md) cuyo origen es necesario actualizar.

*pParentWnd*<br/>
Señala al objeto de ventana principal o propietaria (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establecerá en la ventana principal de la aplicación.

### <a name="remarks"></a>Comentarios

Para mostrar el cuadro de diálogo, llame a la [DoModal](#domodal) función.

Para obtener más información, consulte el [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) estructura y [OleUIChangeSource](/windows/desktop/api/oledlg/nf-oledlg-oleuichangesourcea) función en el SDK de Windows.

##  <a name="domodal"></a>  COleChangeSourceDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo origen de OLE cambio.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:

- IDOK si el cuadro de diálogo se mostró correctamente.

- IDCANCEL si el usuario canceló el cuadro de diálogo.

- IDABORT si se produjo un error. Si se devuelve IDABORT, llame a la [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea el [OleUIChangeSource](/windows/desktop/api/oledlg/nf-oledlg-oleuichangesourcea) función en el SDK de Windows.

### <a name="remarks"></a>Comentarios

Si desea inicializar los distintos controles de cuadro de diálogo mediante el establecimiento de los miembros de la [m_cs](#m_cs) estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, se puede llamar a funciones miembro para recuperar la configuración proporcionada por el usuario o la información desde el cuadro de diálogo. La siguiente lista enumera las funciones de consulta típica:

- [GetFileName](#getfilename)

- [GetDisplayName](#getdisplayname)

- [GetItemName](#getitemname)

##  <a name="getdisplayname"></a>  COleChangeSourceDialog::GetDisplayName

Llame a esta función para recuperar el nombre para mostrar completo para el elemento vinculado del cliente.

```
CString GetDisplayName();
```

### <a name="return-value"></a>Valor devuelto

El nombre para mostrar código fuente completo (moniker de) la [COleClientItem](../../mfc/reference/coleclientitem-class.md) especificado en el constructor.

##  <a name="getfilename"></a>  COleChangeSourceDialog::GetFileName

Llame a esta función para recuperar la parte del moniker de archivo del nombre para mostrar para el elemento vinculado del cliente.

```
CString GetFileName();
```

### <a name="return-value"></a>Valor devuelto

La parte del moniker de archivo del nombre para mostrar código fuente para el [COleClientItem](../../mfc/reference/coleclientitem-class.md) especificado en el constructor.

### <a name="remarks"></a>Comentarios

El moniker del archivo junto con el moniker del elemento proporciona el nombre de pantalla completa.

##  <a name="getfromprefix"></a>  COleChangeSourceDialog::GetFromPrefix

Llame a esta función para obtener la cadena de prefijo anterior para el origen.

```
CString GetFromPrefix();
```

### <a name="return-value"></a>Valor devuelto

La cadena de prefijo anterior del origen.

### <a name="remarks"></a>Comentarios

Llamada a esta función solo después de [DoModal](#domodal) devuelve IDOK.

Este valor proviene directamente de la `lpszFrom` miembro de la [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) estructura.

Para obtener más información, consulte el [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) estructura en el SDK de Windows.

##  <a name="getitemname"></a>  COleChangeSourceDialog::GetItemName

Llame a esta función para recuperar la parte de moniker del elemento del nombre para mostrar para el elemento vinculado del cliente.

```
CString GetItemName();
```

### <a name="return-value"></a>Valor devuelto

La parte de moniker del elemento del nombre para mostrar código fuente para el [COleClientItem](../../mfc/reference/coleclientitem-class.md) especificado en el constructor.

### <a name="remarks"></a>Comentarios

El moniker del archivo junto con el moniker del elemento proporciona el nombre de pantalla completa.

##  <a name="gettoprefix"></a>  COleChangeSourceDialog::GetToPrefix

Llame a esta función para obtener la nueva cadena de prefijo para el origen.

```
CString GetToPrefix();
```

### <a name="return-value"></a>Valor devuelto

La nueva cadena de prefijo del origen.

### <a name="remarks"></a>Comentarios

Llamada a esta función solo después de [DoModal](#domodal) devuelve IDOK.

Este valor proviene directamente de la `lpszTo` miembro de la [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) estructura.

Para obtener más información, consulte el [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) estructura en el SDK de Windows.

##  <a name="m_cs"></a>  COleChangeSourceDialog::m_cs

Este miembro de datos es una estructura de tipo [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea).

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>Comentarios

`OLEUICHANGESOURCE` se usa para controlar el comportamiento del cuadro de diálogo origen de OLE cambio. Los miembros de esta estructura se pueden modificar directamente.

Para obtener más información, consulte el [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) estructura en el SDK de Windows.

##  <a name="isvalidsource"></a>  COleChangeSourceDialog::IsValidSource

Llame a esta función para determinar si el nuevo origen es válido.

```
BOOL IsValidSource();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si es válido, el nuevo origen de lo contrario, 0.

### <a name="remarks"></a>Comentarios

Llamada a esta función solo después de [DoModal](#domodal) devuelve IDOK.

Para obtener más información, consulte el [OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) estructura en el SDK de Windows.

## <a name="see-also"></a>Vea también

[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
