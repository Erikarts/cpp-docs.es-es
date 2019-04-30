---
title: CComPtrBase (clase)
ms.date: 11/04/2016
f1_keywords:
- CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase::Advise
- ATLCOMCLI/ATL::CComPtrBase::Attach
- ATLCOMCLI/ATL::CComPtrBase::CoCreateInstance
- ATLCOMCLI/ATL::CComPtrBase::CopyTo
- ATLCOMCLI/ATL::CComPtrBase::Detach
- ATLCOMCLI/ATL::CComPtrBase::IsEqualObject
- ATLCOMCLI/ATL::CComPtrBase::QueryInterface
- ATLCOMCLI/ATL::CComPtrBase::Release
- ATLCOMCLI/ATL::CComPtrBase::SetSite
- ATLCOMCLI/ATL::CComPtrBase::p
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
ms.openlocfilehash: 5bb599b88671447e219421efacac7a2d8a5f7b06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246236"
---
# <a name="ccomptrbase-class"></a>CComPtrBase (clase)

Esta clase proporciona una base para las clases de puntero inteligente que usa las rutinas de memoria basado en COM.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class CComPtrBase
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de objeto que hace referencia el puntero inteligente.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComPtrBase::~CComPtrBase](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComPtrBase::Advise](#advise)|Llame a este método para crear una conexión entre el `CComPtrBase`del punto de conexión y el receptor de un cliente.|
|[CComPtrBase::Attach](#attach)|Llame a este método para tomar posesión de un puntero existente.|
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|Llame a este método para crear un objeto de la clase asociada con un Id. de clase especificado o el Id. de programa.|
|[CComPtrBase::CopyTo](#copyto)|Llame a este método para copiar el `CComPtrBase` puntero a otra variable de puntero.|
|[CComPtrBase::Detach](#detach)|Llame a este método para liberar la propiedad de un puntero.|
|[CComPtrBase::IsEqualObject](#isequalobject)|Llame a este método para comprobar si especificado `IUnknown` apunta al mismo objeto asociado con el `CComPtrBase` objeto.|
|[CComPtrBase::QueryInterface](#queryinterface)|Llame a este método para devolver un puntero a una interfaz especificada.|
|[CComPtrBase::Release](#release)|Llame a este método para liberar la interfaz.|
|[CComPtrBase::SetSite](#setsite)|Llame a este método para establecer el sitio de la `CComPtrBase` de objeto para el `IUnknown` del objeto primario.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CComPtrBase::operator T*](#operator_t_star)|El operador de conversión.|
|[CComPtrBase::operator !](#operator_not)|El operador NOT.|
|[CComPtrBase::operator &](#operator_amp)|El & operador.|
|[CComPtrBase::operator *](#operator_star)|El operador \*.|
|[CComPtrBase::operator <](#ccomptrbase__operator lt)|El menor-que el operador.|
|[CComPtrBase::operator ==](#operator_eq_eq)|El operador de igualdad.|
|[CComPtrBase::operator ->](#operator_ptr)|El operador de miembros de puntero.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CComPtrBase::p](#p)|La variable de miembro de datos de puntero.|

## <a name="remarks"></a>Comentarios

Esta clase proporciona la base para otros punteros inteligentes que use las rutinas de administración de memoria de COM, como [CComQIPtr](../../atl/reference/ccomqiptr-class.md) y [CComPtr](../../atl/reference/ccomptr-class.md). Agregar sus propios constructores y operadores de las clases derivadas, pero se basan en los métodos proporcionados por `CComPtrBase`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcomcli.h

##  <a name="advise"></a>  CComPtrBase::Advise

Llame a este método para crear una conexión entre el `CComPtrBase`del punto de conexión y el receptor de un cliente.

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
Un puntero para el cliente `IUnknown`.

*iid*<br/>
El GUID del punto de conexión. Normalmente, esto es igual que la interfaz de salida administrada por el punto de conexión.

*pdw*<br/>
Un puntero a la cookie que identifica la conexión.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Consulte [AtlAdvise](connection-point-global-functions.md#atladvise) para obtener más información.

##  <a name="attach"></a>  CComPtrBase::Attach

Llame a este método para tomar posesión de un puntero existente.

```
void Attach(T* p2) throw();
```

### <a name="parameters"></a>Parámetros

*p2*<br/>
La `CComPtrBase` objeto tomará posesión de este puntero.

### <a name="remarks"></a>Comentarios

`Attach` las llamadas [CComPtrBase::Release](#release) en existente [CComPtrBase::p](#p) variable miembro y, a continuación, asigna *p2* a `CComPtrBase::p`. Cuando un `CComPtrBase` objeto toma posesión de un puntero, se llamará automáticamente a `Release` en el puntero que se eliminará el puntero y los datos asignados si el recuento de referencias en el objeto llega a 0.

##  <a name="dtor"></a>  CComPtrBase::~CComPtrBase

Destructor.

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>Comentarios

Libera la interfaz apuntada `CComPtrBase`.

##  <a name="cocreateinstance"></a>  CComPtrBase::CoCreateInstance

Llame a este método para crear un objeto de la clase asociada con un Id. de clase especificado o el Id. de programa.

```
HRESULT CoCreateInstance(
    LPCOLESTR szProgID,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();

HRESULT CoCreateInstance(
    REFCLSID rclsid,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();
```

### <a name="parameters"></a>Parámetros

*szProgID*<br/>
Puntero a un ProgID, que se utiliza para recuperar el CLSID.

*pUnkOuter*<br/>
Si es NULL, indica que el objeto no se está creando como parte de un agregado. Si no es NULL, es un puntero al objeto agregado `IUnknown` interfaz (el control `IUnknown`).

*dwClsContext*<br/>
Contexto en que se ejecutará el código que administra el objeto recién creado.

*rclsid*<br/>
CLSID asociado con los datos y el código que se usará para crear el objeto.

### <a name="return-value"></a>Valor devuelto

En caso de error, devuelve S_OK en caso de éxito, o REGDB_E_CLASSNOTREG, CLASS_E_NOAGGREGATION, CO_E_CLASSSTRING o E_NOINTERFACE. Consulte [CoCreateClassInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance) y [CLSIDFromProgID](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromprogid) para obtener una descripción de estos errores.

### <a name="remarks"></a>Comentarios

Si el primer formulario del método se llama, [CLSIDFromProgID](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromprogid) se usa para recuperar el CLSID. Ambas formas, a continuación, llame a [CoCreateClassInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).

En las compilaciones de depuración, se producirá un error de aserción si [CComPtrBase::p](#p) no es igual a NULL.

##  <a name="copyto"></a>  CComPtrBase::CopyTo

Llame a este método para copiar el `CComPtrBase` puntero a otra variable de puntero.

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>Parámetros

*ppT*<br/>
Dirección de la variable que recibirá el `CComPtrBase` puntero.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, E_POINTER en caso de error.

### <a name="remarks"></a>Comentarios

Copia el `CComPtrBase` puntero a *ppT*. El recuento de referencias el [CComPtrBase::p](#p) se incrementa la variable de miembro.

Un error HRESULT que se devolverá si *ppT* es igual a NULL. En las compilaciones de depuración, se producirá un error de aserción si *ppT* es igual a NULL.

##  <a name="detach"></a>  CComPtrBase::Detach

Llame a este método para liberar la propiedad de un puntero.

```
T* Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una copia del puntero.

### <a name="remarks"></a>Comentarios

Libera la propiedad de un puntero, Establece el [CComPtrBase::p](#p) variable de miembro de datos con valores NULL y devuelve una copia del puntero.

##  <a name="isequalobject"></a>  CComPtrBase::IsEqualObject

Llame a este método para comprobar si especificado `IUnknown` apunta al mismo objeto asociado con el `CComPtrBase` objeto.

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>Parámetros

*pOther*<br/>
`IUnknown *` que se va comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si los objetos son idénticos, false en caso contrario.

##  <a name="operator_not"></a>  CComPtrBase::operator !

El operador NOT.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el `CComHeapPtr` puntero es igual a NULL, false en caso contrario.

##  <a name="operator_amp"></a>  CComPtrBase::operator &amp;

El & operador.

```
T** operator&() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la dirección del objeto que apunta el `CComPtrBase` objeto.

##  <a name="operator_star"></a>  CComPtrBase::operator \*

El operador \*.

```
T& operator*() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de [CComPtrBase::p](#p); es decir, un puntero al objeto al que hace referencia el `CComPtrBase` objeto.

Si las compilaciones de depuración, se producirá un error de aserción si [CComPtrBase::p](#p) no es igual a NULL.

##  <a name="operator_eq_eq"></a>  CComPtrBase::operator ==

El operador de igualdad.

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>Parámetros

*pT*<br/>
Un puntero a un objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve true si `CComPtrBase` y *pT* apuntan al objeto mismo, false en caso contrario.

##  <a name="operator_ptr"></a>  CComPtrBase::operator -&gt;

El operador de puntero a miembro.

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de la [CComPtrBase::p](#p) variable de miembro de datos.

### <a name="remarks"></a>Comentarios

Utilice este operador para llamar a un método en una clase que apunta el `CComPtrBase` objeto. En las compilaciones de depuración, se producirá un error de aserción si el `CComPtrBase` miembro de datos apunta a NULL.

##  <a name="operator_lt"></a>  CComPtrBase::operator &lt;

El menor-que el operador.

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>Parámetros

*pT*<br/>
Un puntero a un objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el puntero administrado por el objeto actual es menor que el puntero a la que se está comparando.

##  <a name="operator_t_star"></a>  CComPtrBase::operator T\*

El operador de conversión.

```
operator T*() const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve un puntero al tipo de datos de objeto definido en la plantilla de clase.

##  <a name="p"></a>  CComPtrBase::p

La variable de miembro de datos de puntero.

```
T* p;
```

### <a name="remarks"></a>Comentarios

Esta variable miembro contiene la información de puntero.

##  <a name="queryinterface"></a>  CComPtrBase::QueryInterface

Llame a este método para devolver un puntero a una interfaz especificada.

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>Parámetros

*Q*<br/>
El tipo de objeto cuyo puntero de interfaz es necesario.

*pp*<br/>
Dirección de variable de salida que recibe el puntero de interfaz solicitada.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si funciona correctamente o E_NOINTERFACE en caso de error.

### <a name="remarks"></a>Comentarios

Este método llama a [IUnknown:: QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)).

En las compilaciones de depuración, se producirá un error de aserción si *pp* no es igual a NULL.

##  <a name="release"></a>  CComPtrBase::Release

Llame a este método para liberar la interfaz.

```
void Release() throw();
```

### <a name="remarks"></a>Comentarios

Se libera la interfaz, y [CComPtrBase::p](#p) se establece en NULL.

##  <a name="setsite"></a>  CComPtrBase::SetSite

Llame a este método para establecer el sitio de la `CComPtrBase` de objeto para el `IUnknown` del objeto primario.

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>Parámetros

*punkParent*<br/>
Un puntero a la `IUnknown` interfaz del elemento primario.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Este método llama a [AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite).

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
