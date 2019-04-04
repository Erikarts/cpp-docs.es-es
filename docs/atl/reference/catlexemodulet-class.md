---
title: CAtlExeModuleT (clase)
ms.date: 11/04/2016
f1_keywords:
- CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::InitializeCom
- ATLBASE/ATL::CAtlExeModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlExeModuleT::PostMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::RegisterClassObjects
- ATLBASE/ATL::CAtlExeModuleT::RevokeClassObjects
- ATLBASE/ATL::CAtlExeModuleT::Run
- ATLBASE/ATL::CAtlExeModuleT::RunMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::UninitializeCom
- ATLBASE/ATL::CAtlExeModuleT::Unlock
- ATLBASE/ATL::CAtlExeModuleT::WinMain
- ATLBASE/ATL::CAtlExeModuleT::m_bDelayShutdown
- ATLBASE/ATL::CAtlExeModuleT::m_dwPause
- ATLBASE/ATL::CAtlExeModuleT::m_dwTimeOut
helpviewer_keywords:
- CAtlExeModuleT class
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
ms.openlocfilehash: 87e526a10c9bcd6a52f4544c50344c5145cfa732
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769555"
---
# <a name="catlexemodulet-class"></a>CAtlExeModuleT (clase)

Esta clase representa el módulo de una aplicación.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `CAtlExeModuleT`.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|El constructor.|
|[CAtlExeModuleT::~CAtlExeModuleT](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlExeModuleT::InitializeCom](#initializecom)|Inicializa com|
|[CAtlExeModuleT::ParseCommandLine](#parsecommandline)|Analiza la línea de comandos y realiza el registro, si es necesario.|
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|Este método se llama inmediatamente después de que se cierra el bucle de mensajes.|
|[CAtlExeModuleT::PreMessageLoop](#premessageloop)|Este método se llama inmediatamente antes de entrar en el bucle de mensajes.|
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|Registra el objeto de clase.|
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|Revoca el objeto de clase.|
|[CAtlExeModuleT::Run](#run)|Este método se ejecuta código en el módulo EXE para inicializar, ejecute el bucle de mensajes y limpiar.|
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|Este método ejecuta el bucle de mensajes.|
|[CAtlExeModuleT::UninitializeCom](#uninitializecom)|Anula la inicialización COM.|
|[CAtlExeModuleT::Unlock](#unlock)|Disminuye el recuento de bloqueos del módulo.|
|[CAtlExeModuleT::WinMain](#winmain)|Este método implementa el código necesario para ejecutar un archivo EXE.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|Una marca que indica que debe haber un retraso que se va a cerrar el módulo.|
|[CAtlExeModuleT::m_dwPause](#m_dwpause)|Un valor de pausa que se usa para asegurarse de que todos los objetos se liberan antes del apagado.|
|[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)|Un valor de tiempo de espera utilizado para retrasar la descarga del módulo.|

## <a name="remarks"></a>Comentarios

`CAtlExeModuleT` representa el módulo de una aplicación (EXE) y contiene código que admite la creación de un archivo EXE, procesamiento de la línea de comandos, registro de objetos de clase, ejecuta el bucle de mensajes y limpiar al salir.

Esta clase está diseñada para mejorar el rendimiento cuando los objetos COM en el servidor EXE continuamente se crean y destruyen. Después de que se libera el último objeto COM, el archivo EXE espera durante un tiempo especificado por el [CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout) miembro de datos. Si no hay ninguna actividad durante este período (es decir, se crean los objetos COM), se inicia el proceso de cierre.

El [CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown) miembro de datos es una marca que se usa para determinar si el archivo ejecutable debe usar el mecanismo definido anteriormente. Si se establece en false, el módulo se finalizará inmediatamente.

Para obtener más información sobre los módulos de ATL, vea [clases de módulo ATL](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="catlexemodulet"></a>  CAtlExeModuleT::CAtlExeModuleT

El constructor.

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Comentarios

Si no se pudo inicializar el módulo del archivo EXE, WinMain devolverá inmediatamente sin más procesamiento.

##  <a name="dtor"></a>  CAtlExeModuleT::~CAtlExeModuleT

Destructor.

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados.

##  <a name="initializecom"></a>  CAtlExeModuleT::InitializeCom

Inicializa com

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Este método se llama desde el constructor y se puede invalidar para inicializar el objeto COM de una manera diferente de la implementación predeterminada. La implementación predeterminada llama bien `CoInitializeEx(NULL, COINIT_MULTITHREADED)` o `CoInitialize(NULL)` según la configuración del proyecto.

Invalidar este método normalmente es necesario reemplazar [CAtlExeModuleT::UninitializeCom](#uninitializecom).

##  <a name="m_bdelayshutdown"></a>  CAtlExeModuleT::m_bDelayShutdown

Una marca que indica que debe haber un retraso que se va a cerrar el módulo.

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>Comentarios

Consulte la [CAtlExeModuleT Introducción](../../atl/reference/catlexemodulet-class.md) para obtener más información.

##  <a name="m_dwpause"></a>  CAtlExeModuleT::m_dwPause

Un valor de pausa que se usa para asegurarse de que todos los objetos ha desaparecido antes del apagado.

```
DWORD m_dwPause;
```

### <a name="remarks"></a>Comentarios

Cambie este valor después de llamar a [a CAtlExeModuleT:: InitializeCom](#initializecom) para establecer el número de milisegundos que se utiliza como el valor de pausa para apagar el servidor. El valor predeterminado es 1000 milisegundos.

##  <a name="m_dwtimeout"></a>  CAtlExeModuleT::m_dwTimeOut

Un valor de tiempo de espera utilizado para retrasar la descarga del módulo.

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>Comentarios

Cambie este valor después de llamar a [a CAtlExeModuleT:: InitializeCom](#initializecom) para definir el número de milisegundos que se utiliza como el valor de tiempo de espera para cerrar el servidor. El valor predeterminado es 5000 milisegundos. Consulte la [CAtlExeModuleT Introducción](../../atl/reference/catlexemodulet-class.md) para obtener más detalles.

##  <a name="parsecommandline"></a>  CAtlExeModuleT::ParseCommandLine

Analiza la línea de comandos y realiza el registro, si es necesario.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parámetros

*lpCmdLine*<br/>
La línea de comandos pasados a la aplicación.

*pnRetCode*<br/>
HRESULT correspondiente al registro (si se llevó a cabo).

### <a name="return-value"></a>Valor devuelto

Devuelve true si la aplicación debe continuar ejecutándose, en caso contrario, false.

### <a name="remarks"></a>Comentarios

Este método se llama desde [CAtlExeModuleT::WinMain](#winmain) y se puede invalidar para controlar los modificadores de línea de comandos. La implementación predeterminada busca **/regserver** y **/UnRegServer** argumentos de línea de comandos y realiza el registro o anulación del registro.

##  <a name="postmessageloop"></a>  CAtlExeModuleT::PostMessageLoop

Este método se llama inmediatamente después de que se cierra el bucle de mensajes.

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Invalide este método para realizar la limpieza de la aplicación personalizada. La implementación predeterminada llama [CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects).

##  <a name="premessageloop"></a>  CAtlExeModuleT::PreMessageLoop

Este método se llama inmediatamente antes de entrar en el bucle de mensajes.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
El valor pasado como el *nShowCmd* parámetro WinMain.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Invalide este método para agregar código de inicialización personalizado para la aplicación. La implementación predeterminada registra los objetos de clase.

##  <a name="registerclassobjects"></a>  CAtlExeModuleT::RegisterClassObjects

Registra el objeto de clase con OLE para que otras aplicaciones que puedan conectarse a él.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parámetros

*dwClsContext*<br/>
Especifica el contexto en el que se ejecutará el objeto de clase. Los valores posibles son CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER o CLSCTX_LOCAL_SERVER.

*dwFlags*<br/>
Determina los tipos de conexión para el objeto de clase. Los valores posibles son REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE o REGCLS_MULTI_SEPARATE.

### <a name="return-value"></a>Valor devuelto

En el éxito, S_FALSE si no hubo ninguna clase para registrar o un error HRESULT en caso contrario, devuelve S_OK.

##  <a name="revokeclassobjects"></a>  CAtlExeModuleT::RevokeClassObjects

Quita el objeto de clase.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Valor devuelto

En el éxito, S_FALSE si no hubo ninguna clase para registrar o un error HRESULT en caso contrario, devuelve S_OK.

##  <a name="run"></a>  CAtlExeModuleT::Run

Este método se ejecuta código en el módulo EXE para inicializar, ejecute el bucle de mensajes y limpiar.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Especifica cómo se mostrará la ventana. Este parámetro puede ser uno de los valores descritos en la [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain) sección. El valor predeterminado es SW_HIDE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Este método puede invalidarse. Sin embargo, en la práctica es mejor invalidar [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](#runmessageloop), o [CAtlExeModuleT::PostMessageLoop](#postmessageloop) en su lugar.

##  <a name="runmessageloop"></a>  CAtlExeModuleT::RunMessageLoop

Este método ejecuta el bucle de mensajes.

```
void RunMessageLoop() throw();
```

### <a name="remarks"></a>Comentarios

Este método se puede invalidar para cambiar el comportamiento del bucle de mensaje.

##  <a name="uninitializecom"></a>  CAtlExeModuleT::UninitializeCom

Anula la inicialización COM.

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>Comentarios

De forma predeterminada este método simplemente llama a [CoUninitialize](/windows/desktop/api/combaseapi/nf-combaseapi-couninitialize) y se llama desde el destructor. Invalide este método si invalida [a CAtlExeModuleT:: InitializeCom](#initializecom).

##  <a name="unlock"></a>  CAtlExeModuleT::Unlock

Disminuye el recuento de bloqueos del módulo.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un valor que puede ser útil para el diagnóstico o de pruebas.

##  <a name="winmain"></a>  CAtlExeModuleT::WinMain

Este método implementa el código necesario para ejecutar un archivo EXE.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Especifica cómo se mostrará la ventana. Este parámetro puede ser uno de los valores descritos en la [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain) sección.

### <a name="return-value"></a>Valor devuelto

Devuelve el valor devuelto del archivo ejecutable.

### <a name="remarks"></a>Comentarios

Este método puede invalidarse. Si se reemplaza [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::PostMessageLoop](#postmessageloop), o [CAtlExeModuleT::RunMessageLoop](#runmessageloop) no ofrece suficiente flexibilidad , es posible invalidar el `WinMain` funcione con este método.

## <a name="see-also"></a>Vea también

[Ejemplo ATLDuck](../../overview/visual-cpp-samples.md)<br/>
[CAtlModuleT (clase)](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlDllModuleT (clase)](../../atl/reference/catldllmodulet-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
