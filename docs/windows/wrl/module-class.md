---
title: Module (clase)
ms.date: 10/18/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module
- module/Microsoft::WRL::Module::Create
- module/Microsoft::WRL::Module::DecrementObjectCount
- module/Microsoft::WRL::Module::GetActivationFactory
- module/Microsoft::WRL::Module::GetClassObject
- module/Microsoft::WRL::Module::GetModule
- module/Microsoft::WRL::Module::GetObjectCount
- module/Microsoft::WRL::Module::IncrementObjectCount
- module/Microsoft::WRL::Module::Module
- module/Microsoft::WRL::Module::objectCount_Data
- module/Microsoft::WRL::Module::RegisterCOMObject
- module/Microsoft::WRL::Module::RegisterObjects
- module/Microsoft::WRL::Module::RegisterWinRTObject
- module/Microsoft::WRL::Module::releaseNotifier_
- module/Microsoft::WRL::Module::Terminate
- module/Microsoft::WRL::Module::~Module
- module/Microsoft::WRL::Module::UnregisterCOMObject
- module/Microsoft::WRL::Module::UnregisterObjects
- module/Microsoft::WRL::Module::UnregisterWinRTObject
helpviewer_keywords:
- Microsoft::WRL::Module class
- Microsoft::WRL::Module::Create method
- Microsoft::WRL::Module::DecrementObjectCount method
- Microsoft::WRL::Module::GetActivationFactory method
- Microsoft::WRL::Module::GetClassObject method
- Microsoft::WRL::Module::GetModule method
- Microsoft::WRL::Module::GetObjectCount method
- Microsoft::WRL::Module::IncrementObjectCount method
- Microsoft::WRL::Module::Module, constructor
- Microsoft::WRL::Module::objectCount_ data member
- Microsoft::WRL::Module::RegisterCOMObject method
- Microsoft::WRL::Module::RegisterObjects method
- Microsoft::WRL::Module::RegisterWinRTObject method
- Microsoft::WRL::Module::releaseNotifier_ data member
- Microsoft::WRL::Module::Terminate method
- Microsoft::WRL::Module::~Module, destructor
- Microsoft::WRL::Module::UnregisterCOMObject method
- Microsoft::WRL::Module::UnregisterObjects method
- Microsoft::WRL::Module::UnregisterWinRTObject method
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
ms.openlocfilehash: db3eb123382ac70f6198d094c5eb3fe44d3bbcd9
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337515"
---
# <a name="module-class"></a>Module (clase)

Representa una colección de objetos relacionados.

## <a name="syntax"></a>Sintaxis

```cpp
template<ModuleType moduleType>
class Module;

template<>
class Module<InProc> : public Details::ModuleBase;

template<>
class Module<OutOfProc> : public Module<InProc>;
```

### <a name="parameters"></a>Parámetros

*moduleType*<br/>
Una combinación de uno o varios [ModuleType](moduletype-enumeration.md) valores de enumeración.

## <a name="members"></a>Miembros

### <a name="protected-classes"></a>Clases protegidas

nombre                                                                                | Descripción
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[Module::GenericReleaseNotifier](module-genericreleasenotifier-class.md) | Invoca un controlador de eventos cuando se libera el último objeto del módulo actual. El controlador de eventos se especifica por en una expresión lambda, functor o puntero a función.
[Module::MethodReleaseNotifier](module-methodreleasenotifier-class.md)   | Invoca un controlador de eventos cuando se libera el último objeto del módulo actual. El controlador de eventos se especifica mediante un objeto y su miembro de puntero al método.
[Module::ReleaseNotifier](module-releasenotifier-class.md)               | Invoca un controlador de eventos cuando se libera el último objeto de un módulo.

### <a name="public-constructors"></a>Constructores públicos

Name                             | Descripción
-------------------------------- | -----------------------------------------------------------
[Module::~Module](#tilde-module) | Desinicializa la instancia actual de la `Module` clase.

### <a name="protected-constructors"></a>Constructores protegidos

Name                      | Descripción
------------------------- | ---------------------------------------------------
[Module::Module](#module) | Inicializa una nueva instancia de la clase `Module`.

### <a name="public-methods"></a>Métodos públicos

Name                                                    | Descripción
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[Module::Create](#create)                               | Crea una instancia de un módulo.
[Module::DecrementObjectCount](#decrementobjectcount)   | Disminuye el número de objetos que sigue el módulo.
[Module::GetActivationFactory](#getactivationfactory)   | Obtiene un generador de activación para el módulo.
[Module::GetClassObject](#getclassobject)               | Recupera una memoria caché de generadores de clases.
[Module::GetModule](#getmodule)                         | Crea una instancia de un módulo.
[Module::GetObjectCount](#getobjectcount)               | Recupera el número de objetos administrados por este módulo.
[Module::IncrementObjectCount](#incrementobjectcount)   | Incrementa el número de objetos que se hace un seguimiento mediante el módulo.
[Module::RegisterCOMObject](#registercomobject)         | Registra uno o más objetos COM para que otras aplicaciones pueden conectarse a ellos.
[Module::RegisterObjects](#registerobjects)             | Registra los objetos COM o en tiempo de ejecución de Windows para que otras aplicaciones pueden conectarse a ellos.
[Module::RegisterWinRTObject](#registerwinrtobject)     | Registra uno o más objetos en tiempo de ejecución de Windows para que otras aplicaciones pueden conectarse a ellos.
[Module::Terminate](#terminate)                         | Hace que todos los generadores que crea una instancia por el módulo para que se cierre.
[Module::UnregisterCOMObject](#unregistercomobject)     | Anula el registro de uno o más objetos COM, lo que impide que otras aplicaciones que se conecten a ellos.
[Module::UnregisterObjects](#unregisterobjects)         | Anula el registro de los objetos en el módulo especificado para que otras aplicaciones no se pueden conectar a ellos.
[Module::UnregisterWinRTObject](#unregisterwinrtobject) | Anula el registro de uno o más objetos en tiempo de ejecución de Windows para que otras aplicaciones no se pueden conectar a ellos.

### <a name="protected-methods"></a>Métodos protegidos

Name                      | Descripción
------------------------- | --------------------------------
[Module::Create](#create) | Crea una instancia de un módulo.

### <a name="protected-data-members"></a>Miembros de datos protegidos

nombre                                         | Descripción
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[Module::objectCount_](#objectcount)         | Realiza un seguimiento de cuántas clases se hayan creado con la [realizar](make-function.md) función.
[Module::releaseNotifier_](#releasenotifier) | Contiene un puntero a un `ReleaseNotifier` objeto.

### <a name="macros"></a>Macros

Nombre | Descripción------| --- [ActivatableClass](activatableclass-macros.md) |  Rellena una memoria caché interna que contiene una fábrica que puede crear una instancia de la clase especificada. Esta macro especifica parámetros de Id. de fábrica y de grupo predeterminados.
[ActivatableClassWithFactory](activatableclass-macros.md) | Rellena una memoria caché interna que contiene una fábrica que puede crear una instancia de la clase especificada. Esta macro le permite especificar un parámetro de fábrica concreta.
[ActivatableClassWithFactoryEx](activatableclass-macros.md) | Rellena una memoria caché interna que contiene una fábrica que puede crear una instancia de la clase especificada. Esta macro permite especificar parámetros de Id. de grupo y fábrica concreta.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres**: Microsoft::WRL

## <a name="tilde-module"></a>Module::~Module

Desinicializa la instancia actual de la `Module` clase.

```cpp
virtual ~Module();
```

## <a name="create"></a>Module::Create

Crea una instancia de un módulo.

```cpp
WRL_NOTHROW static Module& Create();
template<typename T>
WRL_NOTHROW static Module& Create(
   T callback
);
template<typename T>
WRL_NOTHROW static Module& Create(
   _In_ T* object,
   _In_ void (T::* method)()
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo de módulo.

*callback*<br/>
Se llama cuando se libera el último objeto de instancia del módulo.

*object*<br/>
El *objeto* y *método* parámetros se utilizan en combinación. Señala al último objeto de instancia cuando se libera el último objeto de instancia en el módulo.

*Método*<br/>
El *objeto* y *método* parámetros se utilizan en combinación. Señala al método del último objeto de instancia cuando se libera el último objeto de instancia en el módulo.

### <a name="return-value"></a>Valor devuelto

Referencia al módulo.

## <a name="decrementobjectcount"></a>Module::DecrementObjectCount

Disminuye el número de objetos que sigue el módulo.

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>Valor devuelto

El recuento antes de la operación de decremento.

## <a name="getactivationfactory"></a>Module::GetActivationFactory

Obtiene un generador de activación para el módulo.

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parámetros

*pActivatibleClassId*<br/>
IID de una clase en tiempo de ejecución.

*ppIFactory*<br/>
IActivationFactory para la clase en tiempo de ejecución especificado.

*serverName*<br/>
El nombre de un subconjunto de los generadores de clases en el módulo actual. Especifique el nombre del servidor usado en el [ActivatableClassWithFactoryEx](activatableclass-macros.md) macro, o especificar `nullptr` para obtener el nombre del servidor predeterminado.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, el valor HRESULT devuelto por GetActivationFactory.

## <a name="getclassobject"></a>Module::GetClassObject

Recupera una memoria caché de generadores de clases.

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
Identificador de clase.

*riid*<br/>
Id. de interfaz que solicita.

*ppv*<br/>
Puntero al objeto devuelto.

*serverName*<br/>
El nombre del servidor que se especifica en uno el `ActivatableClassWithFactory`, `ActivatableClassWithFactoryEx`, o `ActivatableClass` macro; o `nullptr` para obtener el nombre del servidor predeterminado.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

Use este método solo para COM, no el tiempo de ejecución de Windows. Este método solo expone `IClassFactory` métodos.

## <a name="getmodule"></a>Module::GetModule

Crea una instancia de un módulo.

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a un módulo.

## <a name="getobjectcount"></a>Module::GetObjectCount

Recupera el número de objetos administrados por este módulo.

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número actual de objetos administrados por este módulo.

## <a name="incrementobjectcount"></a>Module::IncrementObjectCount

Incrementa el número de objetos que se hace un seguimiento mediante el módulo.

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>Valor devuelto

El recuento antes de la operación de incremento.

## <a name="module"></a>Module::Module

Inicializa una nueva instancia de la clase `Module`.

```cpp
Module();
```

### <a name="remarks"></a>Comentarios

Este constructor está protegido y no se puede llamar con la `new` palabra clave. En su lugar, llame al [GetModule](#getmodule) o [Module](#create).

## <a name="objectcount"></a>Module::objectCount_

Realiza un seguimiento de cuántas clases se hayan creado con la [realizar](make-function.md) función.

```cpp
volatile long objectCount_;
```

## <a name="registercomobject"></a>Module::RegisterCOMObject

Registra uno o más objetos COM para que otras aplicaciones pueden conectarse a ellos.

```cpp
WRL_NOTHROW virtual HRESULT RegisterCOMObject(
   const wchar_t* serverName,
   IID* clsids,
   IClassFactory** factories,
   DWORD* cookies,
   unsigned int count);
```

### <a name="parameters"></a>Parámetros

*serverName*<br/>
Nombre completo de un servidor.

*clsids*<br/>
Una matriz de CLSID para registrar.

*factories*<br/>
Una matriz de interfaces de IUnknown de los objetos de clase cuya disponibilidad se está publicando.

*cookies*<br/>
Cuando se complete la operación, una matriz de punteros a valores que identifican la clase de objetos que se registraron. Estos valores se utilizarán posteriormente revoca el registro.

*count*<br/>
El número de CLSID para registrar.

### <a name="return-value"></a>Valor devuelto

S_OK si ostrar; en caso contrario, un HRESULT como CO_E_OBJISREG que indica el motivo por el error en la operación.

### <a name="remarks"></a>Comentarios

Los objetos COM se registran con el enumerador CLSCTX_LOCAL_SERVER de la enumeración CLSCTX.

El tipo de conexión para los objetos registrados se especifica mediante una combinación de actual *comflag* parámetro de plantilla y el enumerador REGCLS_SUSPENDED de la enumeración REGCLS.

## <a name="registerobjects"></a>Module::RegisterObjects

Registra los objetos COM o en tiempo de ejecución de Windows para que otras aplicaciones pueden conectarse a ellos.

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parámetros

*module*<br/>
Una matriz de objetos COM o en tiempo de ejecución de Windows.

*serverName*<br/>
Nombre del servidor que crea los objetos.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un HRESULT que indica el motivo del error en la operación.

## <a name="registerwinrtobject"></a>Module::RegisterWinRTObject

Registra uno o más objetos en tiempo de ejecución de Windows para que otras aplicaciones pueden conectarse a ellos.

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)
```

### <a name="parameters"></a>Parámetros

*serverName*<br/>
Un nombre que especifica un subconjunto de los objetos afectados por esta operación.

*activatableClassIds*<br/>
Una matriz de CLSID activable para registrar.

*cookie*<br/>
Un valor que identifica los objetos de clase que se registraron. Este valor se utiliza posteriormente para revocar el registro.

*count*<br/>
El número de objetos que se va a registrar.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un error HRESULT como CO_E_OBJISREG que indica el motivo por el error en la operación.

## <a name="releasenotifier"></a>Module::releaseNotifier_

Contiene un puntero a un `ReleaseNotifier` objeto.

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="terminate"></a>Module::Terminate

Hace que todos los generadores que crea una instancia por el módulo para que se cierre.

```cpp
void Terminate();
```

### <a name="remarks"></a>Comentarios

Libera las fábricas en la memoria caché.

## <a name="unregistercomobject"></a>Module::UnregisterCOMObject

Anula el registro de uno o más objetos COM, lo que impide que otras aplicaciones que se conecten a ellos.

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>Parámetros

*serverName*<br/>
(Sin usar)

*cookies*<br/>
Una matriz de punteros a valores que identifican los objetos de clase va a anular. La matriz creada por el [RegisterCOMObject](#registercomobject) método.

*count*<br/>
El número de clases para anular el registro.

### <a name="return-value"></a>Valor devuelto

S_OK si esta operación se realiza correctamente; en caso contrario, un error HRESULT que indica el motivo por el error en la operación.

## <a name="unregisterobjects"></a>Module::UnregisterObjects

Anula el registro de los objetos en el módulo especificado para que otras aplicaciones no se pueden conectar a ellos.

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parámetros

*module*<br/>
Puntero a un módulo.

*serverName*<br/>
Un nombre de calificación que especifica un subconjunto de los objetos afectados por esta operación.

### <a name="return-value"></a>Valor devuelto

S_OK si esta operación se realiza correctamente; en caso contrario, un error HRESULT que indica el motivo por el error de la operación.

## <a name="unregisterwinrtobject"></a>Module::UnregisterWinRTObject

Anula el registro de uno o más objetos en tiempo de ejecución de Windows para que otras aplicaciones no se pueden conectar a ellos.

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>Parámetros

*cookie*<br/>
Un puntero a un valor que identifica el objeto de clase cuyo registro se va a revocar.
