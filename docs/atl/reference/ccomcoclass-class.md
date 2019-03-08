---
title: CComCoClass (clase)
ms.date: 11/04/2016
f1_keywords:
- CComCoClass
- ATLCOM/ATL::CComCoClass
- ATLCOM/ATL::CComCoClass::CreateInstance
- ATLCOM/ATL::CComCoClass::Error
- ATLCOM/ATL::CComCoClass::GetObjectCLSID
- ATLCOM/ATL::CComCoClass::GetObjectDescription
helpviewer_keywords:
- CComCoClass class
- aggregation [C++], aggregation models
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
ms.openlocfilehash: c52e1a95483807f9c842b0b904cd2314258f0e26
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282648"
---
# <a name="ccomcoclass-class"></a>CComCoClass (clase)

Esta clase proporciona métodos para crear instancias de una clase y obtener sus propiedades.

## <a name="syntax"></a>Sintaxis

```
template <class T, const CLSID* pclsid = &CLSID_NULL>
class CComCoClass
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `CComCoClass`.

*pclsid*<br/>
Un puntero al CLSID del objeto.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComCoClass::CreateInstance](#createinstance)|(Estático) Crea una instancia de la clase y las consultas para una interfaz.|
|[CComCoClass::Error](#error)|(Estático) Devuelve información de error completa al cliente.|
|[CComCoClass::GetObjectCLSID](#getobjectclsid)|(Estático) Devuelve el identificador de clase del objeto.|
|[CComCoClass::GetObjectDescription](#getobjectdescription)|(Estático) Invalide para devolver la descripción del objeto.|

## <a name="remarks"></a>Comentarios

`CComCoClass` Proporciona métodos para recuperar CLSID de un objeto, establecer la información del error y la creación de instancias de la clase. Cualquier clase registrada en la asignación de objeto debe derivarse de `CComCoClass`.

`CComCoClass` También define el modelo de fábrica y agregación de clase predeterminado para el objeto. `CComCoClass` usa las dos macros siguientes:

- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) declara el generador de clases se [CComClassFactory](../../atl/reference/ccomclassfactory-class.md).

- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable) declara que se puede agregar el objeto.

Puede invalidar cualquiera de estos valores predeterminados especificando otra macro en su definición de clase. Por ejemplo, para usar [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) en lugar de `CComClassFactory`, especifique el [macro DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) macro:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="createinstance"></a>  CComCoClass::CreateInstance

Use estos `CreateInstance` funciones para crear una instancia de COM de un objeto y recuperar un puntero de interfaz sin usar la API de COM.

```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```

### <a name="parameters"></a>Parámetros

*Q*<br/>
La interfaz COM que debe devolverse a través de *pp*.

*punkOuter*<br/>
[in] El desconocido externo o desconocido de control del agregado.

*pp*<br/>
[out] La dirección de una variable de puntero que recibe el puntero de interfaz solicitada si se crea correctamente.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar. Consulte [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance) en el SDK de Windows para obtener una descripción de los posibles valores devueltos.

### <a name="remarks"></a>Comentarios

Usar la primera sobrecarga de esta función para la creación de objeto típico; usar la segunda sobrecarga cuando necesite agregar el objeto que se está creando.

La clase ATL que implementa el objeto COM necesario (es decir, la clase que se utiliza como el primer parámetro de plantilla [CComCoClass](../../atl/reference/ccomcoclass-class.md)) debe estar en el mismo proyecto que el código de llamada. La creación del objeto COM se lleva a cabo por el generador de clases registrado para esta clase ATL.

Estas funciones son útiles para crear los objetos que ha impedido que se va a externamente que se pueden crear mediante el uso de la [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto) macro. También son útiles en situaciones donde desee evitar la API de COM, por motivos de eficacia.

Tenga en cuenta que la interfaz *Q* debe tener asociado un IID que se puede recuperar mediante el [__uuidof](../../cpp/uuidof-operator.md) operador.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente, `CDocument` se deriva de una clase ATL generados por el asistente `CComCoClass` que implementa el `IDocument` interfaz. La clase se registra en el mapa de objetos con la macro OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO, por lo que los clientes no pueden crear instancias de documento mediante [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance). `CApplication` es una coclase que proporciona un método en uno de sus propias interfaces COM para crear instancias de la clase de documento. El código siguiente muestra lo fácil que cree instancias de la clase de documento mediante el `CreateInstance` miembro heredado de la `CComCoClass` clase base.

[!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]

##  <a name="error"></a>  CComCoClass::Error

Esta función estática se configura el `IErrorInfo` interfaz para proporcionar información de error al cliente.

```
static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance ());

static HRESULT Error(
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```

### <a name="parameters"></a>Parámetros

*lpszDesc*<br/>
[in] La cadena que describe el error. La versión Unicode de `Error` especifica que *lpszDesc* es de tipo LPCOLESTR; la versión ANSI especifica un tipo de LPCSTR.

*iid*<br/>
[in] IID de la interfaz que define el error o GUID_NULL (el valor predeterminado) si el error se ha definido por el sistema operativo.

*hRes*<br/>
[in] El valor HRESULT que desee devolver al llamador. El valor predeterminado es 0. Para obtener más detalles sobre *hRes*, vea la sección Comentarios.

*nID*<br/>
[in] El identificador de recursos donde se almacena la cadena de descripción del error. Este valor debe estar comprendido entre 0 x 0200 y 0xFFFF, ambos inclusive. En las compilaciones de depuración, un **ASSERT** se producirá si *nID* no indiza una cadena válida. En versiones de lanzamiento, la cadena de descripción del error se establecerá en "Error desconocido".

*dwHelpID*<br/>
[in] El identificador de contexto de ayuda para el error.

*lpszHelpFile*<br/>
[in] La ruta de acceso y el nombre del archivo de ayuda que describe el error.

*hInst*<br/>
[in] El identificador del recurso. De forma predeterminada, este parámetro es `_AtlModule::GetResourceInstance`, donde `_AtlModule` es la instancia global de [CAtlModule](../../atl/reference/catlmodule-class.md).

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar. Para conocer más detalles, vea la sección Comentarios.

### <a name="remarks"></a>Comentarios

Para llamar a `Error`, el objeto debe implementar la `ISupportErrorInfo Interface` interfaz.

Si el *hRes* parámetro es distinto de cero, a continuación, `Error` devuelve el valor de *hRes*. Si *hRes* es cero, las cuatro primeras versiones de `Error` devuelve DISP_E_EXCEPTION. Las dos últimas versiones devuelven el resultado de la macro **MAKE_HRESULT (1, FACILITY_ITF,** *nID* **)**.

##  <a name="getobjectclsid"></a>  CComCoClass::GetObjectCLSID

Proporciona una manera coherente de recuperar el CLSID del objeto.

```
static const CLSID& WINAPI GetObjectCLSID();
```

### <a name="return-value"></a>Valor devuelto

Identificador de clase del objeto.

##  <a name="getobjectdescription"></a>  CComCoClass::GetObjectDescription

Esta función estática recupera la descripción de texto para el objeto class.

```
static LPCTSTR WINAPI GetObjectDescription();
```

### <a name="return-value"></a>Valor devuelto

Descripción del objeto de clase.

### <a name="remarks"></a>Comentarios

La implementación predeterminada devuelve NULL. Puede invalidar este método con el [DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description) macro. Por ejemplo:

[!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]

`GetObjectDescription` llama a `IComponentRegistrar::GetComponents`. `IComponentRegistrar` es una interfaz de automatización que le permite registrar y anular el registro de componentes individuales en un archivo DLL. Cuando se crea un objeto de registrador de componentes con el Asistente para proyectos ATL, el Asistente implementará automáticamente la `IComponentRegistrar` interfaz. `IComponentRegistrar` se utiliza normalmente con Microsoft Transaction Server.

Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
