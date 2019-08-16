---
title: CSettingsStore Class
ms.date: 11/04/2016
f1_keywords:
- CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::Close
- AFXSETTINGSSTORE/CSettingsStore::CreateKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteValue
- AFXSETTINGSSTORE/CSettingsStore::Open
- AFXSETTINGSSTORE/CSettingsStore::Read
- AFXSETTINGSSTORE/CSettingsStore::Write
helpviewer_keywords:
- CSettingsStore [MFC], CSettingsStore
- CSettingsStore [MFC], Close
- CSettingsStore [MFC], CreateKey
- CSettingsStore [MFC], DeleteKey
- CSettingsStore [MFC], DeleteValue
- CSettingsStore [MFC], Open
- CSettingsStore [MFC], Read
- CSettingsStore [MFC], Write
ms.assetid: 0ea181de-a13e-4b29-b560-7c43838223ff
ms.openlocfilehash: 75d86b81d9651e5892913af5919ae0a78fe6bbc5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502919"
---
# <a name="csettingsstore-class"></a>CSettingsStore Class

Incluye las funciones API de Windows, proporcionando una interfaz orientada a objetos que se utiliza para tener acceso al registro.

## <a name="syntax"></a>Sintaxis

```
class CSettingsStore : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSettingsStore::CSettingsStore](#csettingsstore)|Construye un objeto `CSettingsStore`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSettingsStore::Close](#close)|Cierra la clave del registro Open.|
|[CSettingsStore::CreateKey](#createkey)|Abre la clave especificada o la crea si no existe.|
|[CSettingsStore::DeleteKey](#deletekey)|Elimina la clave especificada y todos sus elementos secundarios.|
|[CSettingsStore::DeleteValue](#deletevalue)|Elimina el valor especificado de la clave abierta.|
|[CSettingsStore::Open](#open)|Abre la clave especificada.|
|[CSettingsStore::Read](#read)|Recupera los datos para un valor de clave especificado.|
|[CSettingsStore::Write](#write)|Escribe un valor en el registro bajo la clave abierta.|

## <a name="remarks"></a>Comentarios

Las funciones `CreateKey` miembro y `Open` son muy similares. Si la clave del registro ya existe `CreateKey` y `Open` funcionan de la misma manera. Sin embargo, si la clave del registro no existe `CreateKey` , se creará `Open` , mientras que devolverá un valor de error.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar los métodos Open y Read de `CSettingsStore` la clase. Este fragmento de código forma parte del [ejemplo de demostración de la información sobre herramientas](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxsettingsstore. h

##  <a name="close"></a>  CSettingsStore::Close

Cierra la clave del registro Open.

```
virtual void Close();
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, se llama a este método desde el destructor de la [clase CSettingsStore](../../mfc/reference/csettingsstore-class.md).

##  <a name="createkey"></a>  CSettingsStore::CreateKey

Abre una clave del registro o la crea si no existe.

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>Parámetros

*pszPath*<br/>
de Especifica el nombre de una clave que se va a crear o abrir.

### <a name="return-value"></a>Valor devuelto

0 si se realiza correctamente; de lo contrario, un valor distinto de cero.

### <a name="remarks"></a>Comentarios

`CreateKey`utiliza `m_hKey` como raíz de las consultas del registro. Busca *pszPath* como subclave de `m_hKey`. Si la clave no existe, `CreateKey` la crea. De lo contrario, se abre la clave. `CreateKey`a continuación `m_hKey` , establece en la clave creada o abierta.

##  <a name="csettingsstore"></a>  CSettingsStore::CSettingsStore

Crea un objeto `CSettngsStore`.

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Parámetros

*bAdmin*<br/>
de Parámetro booleano que especifica si el `CSettingsStore` objeto está actuando en modo de administrador.

*bReadOnly*<br/>
de Parámetro booleano que especifica si el `CSettingsStore` objeto se crea en modo de solo lectura.

### <a name="remarks"></a>Comentarios

Si *bAdmin* se establece en true, la `m_hKey` variable miembro se establece en **HKEY_LOCAL_MACHINE**. Si establece *bAdmin* en false, `m_hKey` se establece en **HKEY_CURRENT_USER**.

El acceso de seguridad depende del parámetro *bReadOnly* . Si *bReadonly* es false, el acceso de seguridad se establecerá en **KEY_ALL_ACCESS**. Si *bReadyOnly* es true, el acceso de seguridad se establecerá en una combinación de **KEY_QUERY_VALUE, KEY_NOTIFY** y **KEY_ENUMERATE_SUB_KEYS**. Para obtener más información sobre el acceso de seguridad junto con el registro, consulte [derechos de acceso y seguridad de la clave del registro](/windows/win32/SysInfo/registry-key-security-and-access-rights).

El destructor para `CSettingsStore` las `m_hKey` versiones de forma automática.

##  <a name="deletekey"></a>  CSettingsStore::DeleteKey

Elimina una clave y todos sus elementos secundarios del registro.

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>Parámetros

*pszPath*<br/>
de Nombre de la clave que se va a eliminar.

*bAdmin*<br/>
de Modificador que especifica la ubicación de la clave que se va a eliminar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Este método producirá un error `CSettingsStore` si el objeto está en modo de solo lectura.

Si el parámetro *bAdmin* es cero, `DeleteKey` busca la clave que se va a eliminar en **HKEY_CURRENT_USER**. Si *bAdmin* es distinto de cero `DeleteKey` , busca la clave que se va a eliminar en **HKEY_LOCAL_MACHINE**.

##  <a name="deletevalue"></a>  CSettingsStore::DeleteValue

Elimina un valor de `m_hKey`.

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>Parámetros

*pszValue*<br/>
de Especifica el campo de valor que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="open"></a>  CSettingsStore::Open

Abre una clave del registro.

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>Parámetros

*pszPath*<br/>
de Nombre de una clave del registro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Después de que este método abra correctamente la clave especificada, `m_hKey` establece en el identificador de esta clave.

##  <a name="read"></a>  CSettingsStore::Read

Lee un valor de una clave en el registro.

```
virtual BOOL Read(
    LPCTSTR pszKey,
    int& iVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    DWORD& dwVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CString& sVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Read(
    LPCTSTR pszKey,
    CRect& rect);

virtual BOOL Read(
    LPCTSTR pszKey,
    BYTE** ppData,
    UINT* pBytes);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject*& pObj);
```

### <a name="parameters"></a>Parámetros

*pszKey*<br/>
de Puntero a una cadena terminada en null que contiene el nombre del valor que se va a leer del registro.

*iVal*<br/>
enuncia Referencia a una variable entera que recibe el valor leído de la clave del registro.

*dwVal*<br/>
enuncia Referencia a una variable de doble palabra de 32 bits que recibe el valor leído de la clave del registro.

*sVal*<br/>
enuncia Referencia a una variable de cadena que recibe el valor leído de la clave del registro.

*scStringList*<br/>
enuncia Referencia a una variable de lista de cadenas que recibe el valor leído de la clave del registro.

*scArray*<br/>
enuncia Referencia a una variable de matriz de cadena que recibe el valor leído de la clave del registro.

*dwcArray*<br/>
enuncia Referencia a una variable de matriz de dos palabras de 32 bits que recibe el valor leído de la clave del registro.

*wcArray*<br/>
enuncia Referencia a una variable de matriz de palabras de 16 bits que recibe el valor leído de la clave del registro.

*bcArray*<br/>
enuncia Referencia a una variable de matriz de bytes que recibe el valor leído de la clave del registro.

*lpPoint*<br/>
enuncia Referencia a un puntero a una `POINT` estructura que recibe el valor leído de la clave del registro.

*rect*<br/>
enuncia Referencia a una variable [CRect](../../atl-mfc-shared/reference/crect-class.md) que recibe el valor leído de la clave del registro.

*ppData*<br/>
enuncia Puntero a un puntero a datos que recibe el valor leído de la clave del registro.

*pBytes*<br/>
enuncia Puntero a una variable de entero sin signo. Esta variable recibe el tamaño del búfer al que apunta *ppData* .

*lista*<br/>
enuncia Referencia a una variable [CObList](../../mfc/reference/coblist-class.md) que recibe el valor leído de la clave del registro.

*obj*<br/>
enuncia Referencia a una variable [CObject](../../mfc/reference/cobject-class.md) que recibe el valor leído de la clave del registro.

*pObj*<br/>
enuncia Referencia a un puntero a una `CObject` variable que recibe el valor leído de la clave del registro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

`Read`busca *pszKey* como subclave de `m_hKey`.

##  <a name="write"></a>  CSettingsStore::Write

Escribe un valor en el registro bajo la clave abierta.

```
virtual BOOL Write(
    LPCTSTR pszKey,
    int iVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    DWORD dwVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPCTSTR pszVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Write(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    const CRect& rect);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPBYTE pData,
    UINT nBytes);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject* pObj);
```

### <a name="parameters"></a>Parámetros

*pszKey*<br/>
de Puntero a una cadena que contiene el nombre del valor que se va a establecer.

*iVal*<br/>
de Referencia a una variable de tipo entero que contiene los datos que se van a almacenar.

*dwVal*<br/>
de Referencia a una variable de doble palabra de 32 bits que contiene los datos que se van a almacenar.

*pszVal*<br/>
de Puntero a una variable de cadena terminada en null que contiene los datos que se van a almacenar.

*scStringList*<br/>
de Referencia a una variable [CStringList](../../mfc/reference/cstringlist-class.md) que contiene los datos que se van a almacenar.

*bcArray*<br/>
de Referencia a una variable de matriz de bytes que contiene los datos que se van a almacenar.

*scArray*<br/>
de Referencia a una variable de matriz de cadenas que contiene los datos que se van a almacenar.

*dwcArray*<br/>
de Referencia a una variable de matriz de dos palabras de 32 bits que contiene los datos que se van a almacenar.

*wcArray*<br/>
de Referencia a una variable de matriz de palabras de 16 bits que contiene los datos que se van a almacenar.

*rect*<br/>
de Referencia a una variable [CRect](../../atl-mfc-shared/reference/crect-class.md) que contiene los datos que se van a almacenar.

*lpPoint*<br/>
de Referencia a un puntero a una `POINT` variable que contiene los datos que se van a almacenar.

*pData*<br/>
de Puntero a un búfer que contiene los datos que se van a almacenar.

*nBytes*<br/>
de Especifica el tamaño, en bytes, de los datos a los que apunta el parámetro *pdata* .

*lista*<br/>
de Referencia a una variable [CObList](../../mfc/reference/coblist-class.md) que contiene los datos que se van a almacenar.

*obj*<br/>
de Referencia a una variable [CObject](../../mfc/reference/cobject-class.md) que contiene los datos que se van a almacenar.

*pObj*<br/>
de Puntero a un puntero a una `CObject` variable que contiene los datos que se van a almacenar.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Para escribir en el registro, debe establecer *bReadOnly* en un valor distinto de cero al crear un objeto [CSettingsStore](../../mfc/reference/csettingsstore-class.md) . Para obtener más información, vea [CSettingsStore:: CSettingsStore](#csettingsstore).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx (clase)](../../mfc/reference/cwinappex-class.md)
