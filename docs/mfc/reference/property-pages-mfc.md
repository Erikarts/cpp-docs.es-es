---
title: Páginas de propiedades (MFC)
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
ms.openlocfilehash: e2f75044c7cfbc1f9d2af1d9bda5c108f9afa881
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310336"
---
# <a name="property-pages-mfc"></a>Páginas de propiedades (MFC)

Páginas de propiedades muestran los valores actuales de las propiedades específicas de control OLE en una interfaz gráfica y personalizable para verla y editarla proporcionando un mecanismo de asignación de datos en función de intercambio de datos de cuadro de diálogo (DDX).

Este mecanismo de asignación de datos asigna controles de página de propiedades a las propiedades individuales del control OLE. El valor de propiedad del control refleja el estado o el contenido del control de la página de propiedades. La asignación entre propiedades y los controles de página de propiedad especificada por **DDP_** llamadas función en la página de propiedades `DoDataExchange` función miembro. La siguiente es una lista de **DDP_** funciones que intercambian datos introducidos mediante la página de propiedades del control:

### <a name="property-page-data-transfer"></a>Transferencia de datos de la página de propiedad

|||
|-|-|
|[DDP_CBIndex](#ddp_cbindex)|Vincula el índice de la cadena seleccionada en un cuadro combinado con la propiedad de un control.|
|[DDP_CBString](#ddp_cbstring)|Vincula la cadena seleccionada en un cuadro combinado con la propiedad de un control. La cadena seleccionada puede comenzar con las mismas letras como valor de la propiedad, pero no es necesario para que coincida con completamente.|
|[DDP_CBStringExact](#ddp_cbstringexact)|Vincula la cadena seleccionada en un cuadro combinado con la propiedad de un control. La cadena seleccionada y el valor de cadena de la propiedad deben coincidir exactamente.|
|[DDP_Check](#ddp_check)|Una casilla en la página de propiedades del control con la propiedad de un control de vínculos.|
|[DDP_LBIndex](#ddp_lbindex)|Vincula el índice de la cadena seleccionada en un cuadro de lista con la propiedad de un control.|
|[DDP_LBString](#ddp_lbstring)|Vincula la cadena seleccionada en un cuadro de lista con la propiedad de un control. La cadena seleccionada puede comenzar con las mismas letras como valor de la propiedad, pero no necesita coinciden plenamente.|
|[DDP_LBStringExact](#ddp_lbstringexact)|Vincula la cadena seleccionada en un cuadro de lista con la propiedad de un control. La cadena seleccionada y el valor de cadena de la propiedad deben coincidir exactamente.|
|[DDP_PostProcessing](#ddp_postprocessing)|Finaliza a la transferencia de los valores de propiedad de su control.|
|[DDP_Radio](#ddp_radio)|Un grupo de botones de radio en la página de propiedades del control con la propiedad de un control de vínculos.|
|[DDP_Text](#ddp_text)|Vincula un control en la página de propiedades del control con la propiedad de un control. Esta función controla varios tipos diferentes de las propiedades, como **doble**, **corto**, BSTR, y **largo**.|

Para obtener más información sobre la `DoDataExchange` páginas de propiedades y la función, vea el artículo [controles ActiveX: Páginas de propiedades](../../mfc/mfc-activex-controls-property-pages.md).

La siguiente es una lista de macros que se utiliza para crear y administrar las páginas de propiedades de un control OLE:

### <a name="property-pages"></a>Páginas de propiedades

|||
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|Comienza la lista de identificadores de página de propiedades.|
|[END_PROPPAGEIDS](#end_proppageids)|Finaliza la lista de identificadores de página de propiedades.|
|[PROPPAGEID](#proppageid)|Declara una página de propiedades de la clase de control.|

##  <a name="ddp_cbindex"></a>  DDP_CBIndex

Llame a esta función en la página de propiedades `DoDataExchange` función para sincronizar el valor de propiedad de entero con el índice de la selección actual en un cuadro combinado en la página de propiedades.

```
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*identificador*<br/>
El identificador de recurso de la combinación de cuadro de control asociado con la propiedad del control especificada por *pszPropName*.

*member*<br/>
La variable de miembro asociada al control de página de propiedad especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que van a intercambiar con el control de cuadro combinado especificado por *id*.

### <a name="remarks"></a>Comentarios

Esta función debe llamarse antes de la correspondiente `DDX_CBIndex` llamada de función.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

##  <a name="ddp_cbstring"></a>  DDP_CBString

Llame a esta función en la página de propiedades `DoDataExchange` función para sincronizar el valor de una propiedad de cadena con la selección actual en un cuadro combinado en la página de propiedades.

```
void AFXAPI DDP_CBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*identificador*<br/>
El identificador de recurso de la combinación de cuadro de control asociado con la propiedad del control especificada por *pszPropName*.

*member*<br/>
La variable de miembro asociada al control de página de propiedad especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que van a intercambiar con la cadena de un cuadro combinado especificada por *id*.

### <a name="remarks"></a>Comentarios

Esta función debe llamarse antes de la correspondiente `DDX_CBString` llamada de función.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

##  <a name="ddp_cbstringexact"></a>  DDP_CBStringExact

Llame a esta función en la página de propiedades `DoDataExchange` función para sincronizar el valor de propiedad de cadena que coincide exactamente con la selección actual en un cuadro combinado en la página de propiedades.

```
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*identificador*<br/>
El identificador de recurso de la combinación de cuadro de control asociado con la propiedad del control especificada por *pszPropName*.

*member*<br/>
La variable de miembro asociada al control de página de propiedad especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que van a intercambiar con la cadena de un cuadro combinado especificada por *id*.

### <a name="remarks"></a>Comentarios

Esta función debe llamarse antes de la correspondiente `DDX_CBStringExact` llamada de función.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

##  <a name="ddp_check"></a>  DDP_Check

Llame a esta función en la página de propiedades `DoDataExchange` función para sincronizar el valor de la propiedad con el control de casilla de la página de propiedad asociada.

```
void AFXAPI DDP_Check(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*identificador*<br/>
El identificador de recurso del control de casilla de verificación asociada con la propiedad del control especificada por *pszPropName*.

*member*<br/>
La variable de miembro asociada al control de página de propiedad especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que van a intercambiar con el control de casilla de verificación especificado por *id*.

### <a name="remarks"></a>Comentarios

Esta función debe llamarse antes de la correspondiente `DDX_Check` llamada de función.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

##  <a name="ddp_lbindex"></a>  DDP_LBIndex

Llame a esta función en la página de propiedades `DoDataExchange` función para sincronizar el valor de propiedad de entero con el índice de la selección actual en un cuadro de lista en la página de propiedades.

```
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*identificador*<br/>
El identificador de recurso de la lista de cuadro de control asociado con la propiedad del control especificada por *pszPropName*.

*member*<br/>
La variable de miembro asociada al control de página de propiedad especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que van a intercambiar con la cadena del cuadro de lista especificada por *id*.

### <a name="remarks"></a>Comentarios

Esta función debe llamarse antes de la correspondiente `DDX_LBIndex` llamada de función.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

##  <a name="ddp_lbstring"></a>  DDP_LBString

Llame a esta función en la página de propiedades `DoDataExchange` función para sincronizar el valor de una propiedad de cadena con la selección actual en un cuadro de lista en la página de propiedades.

```
void AFXAPI DDP_LBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*identificador*<br/>
El identificador de recurso de la lista de cuadro de control asociado con la propiedad del control especificada por *pszPropName*.

*member*<br/>
La variable de miembro asociada al control de página de propiedad especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que van a intercambiar con la cadena del cuadro de lista especificada por *id*.

### <a name="remarks"></a>Comentarios

Esta función debe llamarse antes de la correspondiente `DDX_LBString` llamada de función.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

##  <a name="ddp_lbstringexact"></a>  DDP_LBStringExact

Llame a esta función en la página de propiedades `DoDataExchange` función para sincronizar el valor de propiedad de cadena que coincide exactamente con la selección actual en un cuadro de lista en la página de propiedades.

```
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*identificador*<br/>
El identificador de recurso de la lista de cuadro de control asociado con la propiedad del control especificada por *pszPropName*.

*member*<br/>
La variable de miembro asociada al control de página de propiedad especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que van a intercambiar con la cadena del cuadro de lista especificada por *id*.

### <a name="remarks"></a>Comentarios

Esta función debe llamarse antes de la correspondiente `DDX_LBStringExact` llamada de función.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

##  <a name="ddp_postprocessing"></a>  DDP_PostProcessing

Llame a esta función en la página de propiedades `DoDataExchange` función, para finalizar la transferencia de los valores de propiedad de la página de propiedades al control cuando se guardan los valores de propiedad.

```
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

### <a name="remarks"></a>Comentarios

Esta función debe llamarse una vez completadas todas las funciones de intercambio de datos. Por ejemplo:

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

##  <a name="ddp_radio"></a>  DDP_Radio

Llame a esta función en el control `DoPropExchange` función para sincronizar el valor de la propiedad con el control de botón de radio de página de propiedad asociada.

```
void AFXAPI DDP_Radio(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*identificador*<br/>
El identificador de recurso de la radio botón asociado a la propiedad del control especificada por el control *pszPropName*.

*member*<br/>
La variable de miembro asociada al control de página de propiedad especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que van a intercambiar con el control de botón de radio especificado por *id*.

### <a name="remarks"></a>Comentarios

Esta función debe llamarse antes de la correspondiente `DDX_Radio` llamada de función.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

##  <a name="ddp_text"></a>  DDP_Text

Llame a esta función en el control `DoDataExchange` función para sincronizar el valor de la propiedad con el control de página de la propiedad asociada.

```
void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    BYTE & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    UINT & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    long & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    DWORD & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    float & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    double & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    CString & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Puntero a un `CDataExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de datos, incluida su dirección.

*identificador*<br/>
El identificador de recurso del control asociado con la propiedad del control especificada por *pszPropName*.

*member*<br/>
La variable de miembro asociada al control de página de propiedad especificado por *id* y la propiedad especificada por *pszPropName*.

*pszPropName*<br/>
El nombre de propiedad de la propiedad de control que van a intercambiar con el control especificado por *id*.

### <a name="remarks"></a>Comentarios

Esta función debe llamarse antes de la correspondiente `DDX_Text` llamada de función.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

##  <a name="begin_proppageids"></a>  BEGIN_PROPPAGEIDS

Inicia la definición de la lista del control de los identificadores de página de propiedades.

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase de control para la propiedad que se especifican las páginas.

*count*<br/>
El número de páginas de propiedades utilizados por la clase de control.

### <a name="remarks"></a>Comentarios

En el archivo de implementación (.cpp) que define las funciones de miembro para la clase, inicio la lista de la página de propiedades con el BEGIN_PROPPAGEIDS (macro), a continuación, agregue entradas de macro para cada una de las páginas de propiedades y completar la lista de la página de propiedades con el END_PROPPAGEIDS macro.

Para obtener más información sobre las páginas de propiedades, vea el artículo [controles ActiveX: Páginas de propiedades](../../mfc/mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

##  <a name="end_proppageids"></a>  END_PROPPAGEIDS

Termina la definición de la lista de Id. de página de propiedad.

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase de control que posee la página de propiedades.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

##  <a name="proppageid"></a>  PROPPAGEID

Agrega una página de propiedades para su uso por el control OLE.

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
El identificador de clase única de una página de propiedades.

### <a name="remarks"></a>Comentarios

Todas las macros PROPPAGEID deben colocarse entre las macros BEGIN_PROPPAGEIDS y END_PROPPAGEIDS en el archivo de implementación del control.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
