---
title: CInternetSession (clase)
ms.date: 06/20/2018
f1_keywords:
- CInternetSession
- AFXINET/CInternetSession
- AFXINET/CInternetSession::CInternetSession
- AFXINET/CInternetSession::Close
- AFXINET/CInternetSession::EnableStatusCallback
- AFXINET/CInternetSession::GetContext
- AFXINET/CInternetSession::GetCookie
- AFXINET/CInternetSession::GetCookieLength
- AFXINET/CInternetSession::GetFtpConnection
- AFXINET/CInternetSession::GetGopherConnection
- AFXINET/CInternetSession::GetHttpConnection
- AFXINET/CInternetSession::OnStatusCallback
- AFXINET/CInternetSession::OpenURL
- AFXINET/CInternetSession::SetCookie
- AFXINET/CInternetSession::SetOption
helpviewer_keywords:
- CInternetSession [MFC], CInternetSession
- CInternetSession [MFC], Close
- CInternetSession [MFC], EnableStatusCallback
- CInternetSession [MFC], GetContext
- CInternetSession [MFC], GetCookie
- CInternetSession [MFC], GetCookieLength
- CInternetSession [MFC], GetFtpConnection
- CInternetSession [MFC], GetGopherConnection
- CInternetSession [MFC], GetHttpConnection
- CInternetSession [MFC], OnStatusCallback
- CInternetSession [MFC], OpenURL
- CInternetSession [MFC], SetCookie
- CInternetSession [MFC], SetOption
ms.assetid: ef54feb4-9d0f-4e65-a45d-7a4cf6c40e51
ms.openlocfilehash: e3d6d319a963fbc24e89bf8c4c0858cd80ec5a9d
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503460"
---
# <a name="cinternetsession-class"></a>CInternetSession (clase)

Crea e inicializa una o varias sesiones de Internet simultáneas y, si es necesario, describe la conexión a un servidor proxy.

## <a name="syntax"></a>Sintaxis

```cpp
class CInternetSession : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CInternetSession::CInternetSession](#cinternetsession)|Construye un objeto `CInternetSession`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CInternetSession::Close](#close)|Cierra la conexión a Internet cuando se finaliza la sesión de Internet.|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|Establece una rutina de devolución de llamada de estado.|
|[CInternetSession::GetContext](#getcontext)|Cierra la conexión a Internet cuando se finaliza la sesión de Internet.|
|[CInternetSession::GetCookie](#getcookie)|Devuelve las cookies para la dirección URL especificada y todos su elemento primario de direcciones URL.|
|[CInternetSession::GetCookieLength](#getcookielength)|Recupera la variable que especifica la longitud de la cookie almacenada en el búfer.|
|[CInternetSession::GetFtpConnection](#getftpconnection)|Se abre una sesión de FTP con un servidor. Inicia sesión el usuario.|
|[CInternetSession::GetGopherConnection](#getgopherconnection)|Se abre en un servidor gopher para una aplicación que está intentando abrir una conexión.|
|[CInternetSession::GetHttpConnection](#gethttpconnection)|Se abre en un servidor HTTP para una aplicación que está intentando abrir una conexión.|
|[CInternetSession::OnStatusCallback](#onstatuscallback)|Actualiza el estado de una operación cuando está habilitada la devolución de llamada de estado.|
|[CInternetSession::OpenURL](#openurl)|Analiza y se abre una dirección URL.|
|[CInternetSession::SetCookie](#setcookie)|Establece una cookie para la dirección URL especificada.|
|[CInternetSession::SetOption](#setoption)|Establece las opciones de la sesión de Internet.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CInternetSession::operator HINTERNET](#operator_hinternet)|Identificador de la sesión actual de Internet.|

## <a name="remarks"></a>Comentarios

Si la conexión a Internet se debe conservar durante la duración de una aplicación, puede crear un `CInternetSession` miembro de la clase [CWinApp](../../mfc/reference/cwinapp-class.md).

Una vez que ha establecido una sesión de Internet, puede llamar a [OpenURL](#openurl). `CInternetSession` a continuación, se analiza la dirección URL automáticamente mediante una llamada a la función global [AfxParseURL](internet-url-parsing-globals.md#afxparseurl). Independientemente de su tipo de protocolo, `CInternetSession` interpreta la dirección URL y lo administra para usted. Puede controlar las solicitudes de archivos locales identificados con el recurso de dirección URL "file://". `OpenURL` Devuelve un puntero a un [CStdioFile](../../mfc/reference/cstdiofile-class.md) objeto si el nombre se pasa es un archivo local.

Si abre una dirección URL en un servidor de Internet mediante `OpenURL`, puede leer información desde el sitio. Si desea realizar acciones específicas del servicio (por ejemplo, HTTP, FTP o gopher) en los archivos ubicados en un servidor, debe establecer la conexión con dicho servidor correspondiente. Para abrir un determinado tipo de conexión directa a un servicio determinado, use una de las funciones miembro siguientes:

- [GetGopherConnection](#getgopherconnection) para abrir una conexión a un servicio gopher.

- [GetHttpConnection](#gethttpconnection) para abrir una conexión a un servicio HTTP.

- [GetFtpConnection](#getftpconnection) para abrir una conexión a un servicio FTP.

[SetOption](#setoption) le permite establecer las opciones de consulta de la sesión, como los valores de tiempo de espera, número de reintentos y así sucesivamente.

`CInternetSession` las funciones miembro [SetCookie](#setcookie), [GetCookie](#getcookie), y [GetCookieLength](#getcookielength) proporcionan los medios para administrar una base de datos de la cookie de Win32, a través del cual mantienen servidores y las secuencias de comandos información de estado acerca de la estación de trabajo cliente.

Para obtener más información sobre tareas básicas de programación de Internet, consulte el artículo [Internet primeros pasos: WinInet](../../mfc/wininet-basics.md). Para obtener información general sobre el uso de las clases WinInet de MFC, vea el artículo [Internet programar con WinInet](../../mfc/win32-internet-extensions-wininet.md).

> [!NOTE]
> `CInternetSession` se producirá un [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception) para tipos de servicio no admitido. Actualmente se admiten los siguientes tipos de servicio: FTP, HTTP, gopher y archivo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

## <a name="cinternetsession"></a> CInternetSession::CInternetSession

Esta función miembro se llama cuando un `CInternetSession` se crea el objeto.

```cpp
CInternetSession(
    LPCTSTR pstrAgent = NULL,
    DWORD_PTR dwContext = 1,
    DWORD dwAccessType = PRE_CONFIG_INTERNET_ACCESS,
    LPCTSTR pstrProxyName = NULL,
    LPCTSTR pstrProxyBypass = NULL,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parámetros

*pstrAgent*<br/>
Un puntero a una cadena que identifica el nombre de la aplicación o una entidad llamada a las funciones de Internet (por ejemplo, "Microsoft Explorador de Internet"). Si *pstrAgent* es NULL (valor predeterminado), llama el marco de la función global [AfxGetAppName](application-information-and-management.md#afxgetappname), que devuelve una cadena terminada en null que contiene el nombre de la aplicación. Algunos protocolos de usan esta cadena para identificar la aplicación en el servidor.

*dwContext*<br/>
El identificador de contexto para la operación. *dwContext* identifica información de estado de la operación devuelta por [CInternetSession:: OnStatusCallback](#onstatuscallback). El valor predeterminado se establece en 1; Sin embargo, puede asignar explícitamente un identificador de contexto específico para la operación. El objeto y cualquier trabajo que se asociarán con ese identificador de contexto.

*dwAccessType*<br/>
El tipo de acceso necesario. Valores válidos, exactamente uno de los cuales puede ser proporcionada son los siguientes:

- Conectar INTERNET_OPEN_TYPE_PRECONFIG utilizando había preconfigurada de la configuración en el registro. Este tipo de acceso se establece como valor predeterminado. Para conectarse a través de un proxy TIS, establecer *dwAccessType* a este valor; a continuación, Establece el registro correctamente.

- INTERNET_OPEN_TYPE_DIRECT conectarse directamente a Internet.

- INTERNET_OPEN_TYPE_PROXY se conectan a través de un proxy CERN.

Para obtener información sobre la conexión con diferentes tipos de proxy, vea [pasos en una aplicación de cliente FTP típica](../../mfc/steps-in-a-typical-ftp-client-application.md).

*pstrProxyName*<br/>
El nombre del proxy CERN preferido si *dwAccessType* se establece como INTERNET_OPEN_TYPE_PROXY. El valor predeterminado es NULL.

*pstrProxyBypass*<br/>
Un puntero a una cadena que contiene una lista opcional de direcciones de servidor. Estas direcciones pueden omitirse cuando se usa el acceso al proxy. Si se proporciona un valor NULL, la lista de omisión se leerá desde el registro. Este parámetro es significativo únicamente si *dwAccessType* está establecido en INTERNET_OPEN_TYPE_PROXY.

*dwFlags*<br/>
Indica las distintas opciones de almacenamiento en caché. El valor predeterminado se establece en 0. Los valores posibles incluyen:

- INTERNET_FLAG_DONT_CACHE no almacenar en caché los datos, ya sea localmente o en cualquier servidor de puerta de enlace.

- Descargar INTERNET_FLAG_OFFLINE operaciones se satisfacen a través de la caché de persistente. Si el elemento no existe en la memoria caché, se devuelve un código de error adecuado. Esta marca se puede combinar con el bit a bit **o** ( **&#124;** ) operador.

### <a name="remarks"></a>Comentarios

`CInternetSession` la primera función Internet llama a una aplicación. Inicializa las estructuras de datos internas y lo prepara para futuras llamadas desde la aplicación.

Si no se puede abrir ninguna conexión a Internet, `CInternetSession` produce una [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="close"></a>  CInternetSession::Close

Llame a esta función miembro cuando la aplicación ha terminado de utilizar el `CInternetSession` objeto.

```cpp
virtual void Close();
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="enablestatuscallback"></a>  CInternetSession::EnableStatusCallback

Llame a esta función miembro para habilitar la devolución de llamada de estado.

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
Especifica si la devolución de llamada está habilitada o deshabilitada. El valor predeterminado es TRUE.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, determinar la causa del error examinando el producida [CInternetException](../../mfc/reference/cinternetexception-class.md) objeto.

### <a name="remarks"></a>Comentarios

Al controlar la devolución de llamada de estado, puede proporcionar el estado sobre el progreso de la operación (por ejemplo, la resolución de nombre, conectarse al servidor etc.) en la barra de estado de la aplicación. Mostrar estado de la operación es especialmente conveniente durante una operación de larga duración.

Dado que las devoluciones de llamada se producen durante el procesamiento de la solicitud, la aplicación debe dedicar tiempo a tan solo como sea posible en la devolución de llamada para evitar la degradación del rendimiento de los datos a la red. Por ejemplo, la colocación de un cuadro de diálogo en una devolución de llamada puede ser tal una operación larga que el servidor finaliza la solicitud.

No se puede quitar la devolución de llamada de estado mientras las devoluciones de llamada están pendientes.

Para controlar las operaciones de forma asincrónica, debe crear su propio subproceso o usar las funciones de WinInet sin MFC.

## <a name="getcontext"></a>  CInternetSession::GetContext

Llame a esta función miembro para obtener el valor de contexto para una sesión de aplicación determinada.

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Valor devuelto

El contexto definido por la aplicación identificador.

### <a name="remarks"></a>Comentarios

[OnStatusCallback](#onstatuscallback) usa el identificador de contexto devuelto por `GetContext` para informar del estado de una aplicación determinada. Por ejemplo, cuando un usuario activa una solicitud de Internet que implica la devolución de información de estado, la devolución de llamada de estado usa el identificador de contexto para informar del estado en esa solicitud determinada. Si el usuario activa independiente dos solicitudes de Internet que ambos involucran devuelve información de estado, `OnStatusCallback` usa los identificadores de contexto para devolver el estado de sus solicitudes correspondientes. Por lo tanto, el identificador de contexto se utiliza para todas las operaciones de devolución de llamada de estado y está asociado con la sesión hasta que finaliza la sesión.

Para obtener más información acerca de las operaciones asincrónicas, vea el artículo [Internet primeros pasos: WinInet](../../mfc/wininet-basics.md).

## <a name="getcookie"></a>  CInternetSession::GetCookie

Esta función miembro implementa el comportamiento de la función de Win32 [método](/windows/desktop/api/wininet/nf-wininet-internetgetcookiea), tal y como se describe en el SDK de Windows.

```cpp
static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPTSTR pstrCookieData,
    DWORD dwBufLen);

static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    CString& strCookieData);
```

### <a name="parameters"></a>Parámetros

*pstrUrl*<br/>
Un puntero a una cadena que contiene la dirección URL.

*pstrCookieName*<br/>
Un puntero a una cadena que contiene el nombre de la cookie para obtener la dirección URL especificada.

*pstrCookieData*<br/>
En la primera sobrecarga, un puntero a una cadena que contiene la dirección del búfer que recibe los datos de la cookie. Este valor puede ser NULL. En la segunda sobrecarga, una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto para recibir los datos de la cookie.

*dwBufLen*<br/>
La variable especifica el tamaño de la *pstrCookieData* búfer. Si la función se realiza correctamente, recibe la cantidad de datos copiados en el búfer del *pstrCookieData* búfer. Si *pstrCookieData* es NULL, este parámetro recibe un valor que especifica el tamaño del búfer necesario para copiar todos los datos de la cookie.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se realiza correctamente o falso en caso contrario. Si se produce un error en la llamada, llame a la función de Win32 [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error. Se aplican los valores de error siguiente:

- ERROR_NO_MORE_ITEMS no es ninguna cookie para la dirección URL especificada y todos sus objetos primarios.

- El valor pasado en ERROR_INSUFFICIENT_BUFFER *dwBufLen* es insuficiente para copiar todos los datos de la cookie. El valor devuelto en *dwBufLen* es el tamaño del búfer necesario para obtener todos los datos.

### <a name="remarks"></a>Comentarios

En la segunda sobrecarga, MFC recupera los datos de cookies en proporcionado `CString` objeto.

## <a name="getcookielength"></a>  CInternetSession::GetCookieLength

Llame a esta función miembro para obtener la longitud de la cookie almacenada en el búfer.

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>Parámetros

*pstrUrl*<br/>
Un puntero a una cadena que contiene la dirección URL

*pstrCookieName*<br/>
Un puntero a una cadena que contiene el nombre de la cookie.

### <a name="return-value"></a>Valor devuelto

Un valor DWORD que indica la longitud de la cookie, se almacena en el búfer. Cero si ninguna cookie con el nombre indicado por *pstrCookieName* existe.

### <a name="remarks"></a>Comentarios

Este valor se usa por [GetCookie](#getcookie).

## <a name="getftpconnection"></a>  CInternetSession::GetFtpConnection

Llame a esta función miembro para establecer una conexión FTP y obtener un puntero a un `CFtpConnection` objeto.

```cpp
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>Parámetros

*pstrServer*<br/>
Un puntero a una cadena que contiene el nombre del servidor FTP.

*pstrUserName*<br/>
Puntero a una cadena terminada en null que especifica el nombre del usuario para iniciar sesión. Si es NULL, el valor predeterminado es anónimo.

*pstrPassword*<br/>
Un puntero a una cadena terminada en null que especifica la contraseña que se utilizará para iniciar sesión. Si ambos *pstrPassword* y *pstrUserName* son NULL, la contraseña anónima predeterminada es el nombre de correo electrónico del usuario. Si *pstrPassword* es NULL (o una cadena vacía) pero *pstrUserName* no es NULL, se utiliza una contraseña en blanco. En la tabla siguiente describe el comportamiento de las cuatro configuraciones posibles de *pstrUserName* y *pstrPassword*:

| *pstrUserName*  | *pstrPassword*  | Nombre de usuario se envía al servidor FTP | Contraseña que se envían al servidor FTP |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   NULL o ""   |   NULL o ""   |         "anónimo"         |      Nombre de correo electrónico del usuario      |
| Cadena no nula |   NULL o ""   |       *pstrUserName*        |             " "             |
|      NULL       | Cadena no nula |            ERROR            |            ERROR            |
| Cadena no nula | Cadena no nula |       *pstrUserName*        |       *pstrPassword*        |

*nPort*<br/>
Número que identifica el puerto TCP/IP que se usará en el servidor.

*bPassive*<br/>
Especifica el modo pasivo o activo para esta sesión FTP. Si se establece en TRUE, Establece la API Win32 `dwFlag` a INTERNET_FLAG_PASSIVE.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CFtpConnection](../../mfc/reference/cftpconnection-class.md) objeto. Si se produce un error en la llamada, determinar la causa del error examinando el producida [CInternetException](../../mfc/reference/cinternetexception-class.md) objeto.

### <a name="remarks"></a>Comentarios

`GetFtpConnection` se conecta a un servidor FTP y crea y devuelve un puntero a un `CFTPConnection` objeto. No realiza ninguna operación específica en el servidor. Por ejemplo, si desea leer o escribir en archivos, debe realizar esas operaciones en pasos distintos. Vea las clases [CFtpConnection](../../mfc/reference/cftpconnection-class.md) y [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) para obtener información sobre la búsqueda de archivos, abrir archivos y leer o escribir en archivos. Consulte el artículo [Internet programar con WinInet](../../mfc/win32-internet-extensions-wininet.md) para conocer los pasos en la realización de tareas comunes de conexión de FTP.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="getgopherconnection"></a>  CInternetSession::GetGopherConnection

Llame a esta función miembro para establecer una nueva conexión gopher y obtener un puntero a un `CGopherConnection` objeto.

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Parámetros

*pstrServer*<br/>
Un puntero a una cadena que contiene el nombre del servidor gopher.

*pstrUserName*<br/>
Un puntero a una cadena que contiene el nombre de usuario.

*pstrPassword*<br/>
Un puntero a una cadena que contiene la contraseña de acceso.

*nPort*<br/>
Número que identifica el puerto TCP/IP que se usará en el servidor.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objeto. Si se produce un error en la llamada, determinar la causa del error examinando el producida [CInternetException](../../mfc/reference/cinternetexception-class.md) objeto.

### <a name="remarks"></a>Comentarios

`GetGopherConnection` se conecta a un servidor gopher y crea y devuelve un puntero a un `CGopherConnection` objeto. No realiza ninguna operación específica en el servidor. Por ejemplo, si desea leer o escribir datos, debe realizar esas operaciones en pasos distintos. Vea las clases [CGopherConnection](../../mfc/reference/cgopherconnection-class.md), [CGopherFile](../../mfc/reference/cgopherfile-class.md), y [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) para obtener información sobre la búsqueda de archivos, abrir archivos y leer o escribir en archivos. Para obtener información acerca de la exploración de un sitio FTP, vea la función miembro [OpenURL](#openurl). Consulte el artículo [Internet programar con WinInet](../../mfc/win32-internet-extensions-wininet.md) para conocer los pasos en la realización de tareas comunes de conexión gopher.

## <a name="gethttpconnection"></a>  CInternetSession::GetHttpConnection

Llame a esta función miembro para establecer una conexión HTTP y obtener un puntero a un `CHttpConnection` objeto.

```cpp
CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);

CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    DWORD dwFlags,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);
```

### <a name="parameters"></a>Parámetros

*pstrServer*<br/>
Un puntero a una cadena que contiene el nombre del servidor HTTP.

*nPort*<br/>
Número que identifica el puerto TCP/IP que se usará en el servidor.

*pstrUserName*<br/>
Un puntero a una cadena que contiene el nombre de usuario.

*pstrPassword*<br/>
Un puntero a una cadena que contiene la contraseña de acceso.

*dwflags*<br/>
Cualquier combinación de la `INTERNET_FLAG_*` marcas. Consulte la tabla en la **comentarios** sección de [CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) para obtener una descripción de *dwFlags* valores.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CHttpConnection](../../mfc/reference/chttpconnection-class.md) objeto. Si se produce un error en la llamada, determinar la causa del error examinando el producida [CInternetException](../../mfc/reference/cinternetexception-class.md) objeto.

### <a name="remarks"></a>Comentarios

`GetHttpConnection` se conecta a un servidor HTTP y crea y devuelve un puntero a un `CHttpConnection` objeto. No realiza ninguna operación específica en el servidor. Por ejemplo, si desea consultar un encabezado HTTP, debe realizar esta operación como un paso independiente. Vea las clases [CHttpConnection](../../mfc/reference/chttpconnection-class.md) y [CHttpFile](../../mfc/reference/chttpfile-class.md) para obtener información acerca de las operaciones que puede realizar mediante una conexión a un servidor HTTP. Para obtener información acerca de cómo explorar un sitio HTTP, vea la función miembro [OpenURL](#openurl). Consulte el artículo [Internet programar con WinInet](../../mfc/win32-internet-extensions-wininet.md) para conocer los pasos en la realización de tareas comunes de conexión HTTP.

## <a name="onstatuscallback"></a>  CInternetSession::OnStatusCallback

Esta función miembro se llama el marco de trabajo para actualizar el estado cuando está habilitada la devolución de llamada de estado y una operación está pendiente.

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>Parámetros

*dwContext*<br/>
El valor de contexto proporcionado por la aplicación.

*dwInternetStatus*<br/>
Un código de estado que indica por qué se realiza la devolución de llamada. Consulte **comentarios** para una tabla de valores posibles.

*lpvStatusInformation*<br/>
Un puntero a un búfer que contiene información relativa a esta devolución de llamada.

*dwStatusInformationLength*<br/>
El tamaño de *lpvStatusInformation*.

### <a name="remarks"></a>Comentarios

Debe llamar primero a [EnableStatusCallback](#enablestatuscallback) para aprovechar las ventajas de devolución de llamada de estado.

El *dwInternetStatus* parámetro indica la operación se realiza y determina qué el contenido de *lpvStatusInformation* será. *dwStatusInformationLength* indica la longitud de los datos incluidos en *lpvStatusInformation*. El siguiente estado de los valores de *dwInternetStatus* se definen como sigue:

|Valor|Significado|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|Buscar la dirección IP del nombre del contenido en *lpvStatusInformation*.|
|INTERNET_STATUS_NAME_RESOLVED|Encuentra correctamente la dirección IP del nombre del contenido en *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTING_TO_SERVER|Conectarse a la dirección del socket ([SOCKADDR](/windows/desktop/winsock/sockaddr-2)) apunta *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTED_TO_SERVER|Conectado correctamente a la dirección de socket (SOCKADDR) apuntada *lpvStatusInformation*.|
|INTERNET_STATUS_SENDING_REQUEST|Enviando la solicitud de información en el servidor. El *lpvStatusInformation* parámetro es NULL.|
|INTERNET_STATUS_ REQUEST_SENT|La solicitud de información se envió correctamente al servidor. El *lpvStatusInformation* parámetro es NULL.|
|INTERNET_STATUS_RECEIVING_RESPONSE|Esperando a que el servidor responda a una solicitud. El *lpvStatusInformation* parámetro es NULL.|
|INTERNET_STATUS_RESPONSE_RECEIVED|Correctamente recibió una respuesta desde el servidor. El *lpvStatusInformation* parámetro es NULL.|
|INTERNET_STATUS_CLOSING_CONNECTION|Cerrando la conexión al servidor. El *lpvStatusInformation* parámetro es NULL.|
|INTERNET_STATUS_CONNECTION_CLOSED|Cerrado correctamente la conexión al servidor. El *lpvStatusInformation* parámetro es NULL.|
|INTERNET_STATUS_HANDLE_CREATED|Usa la función de la API Win32 [InternetConnect](/windows/desktop/api/wininet/nf-wininet-internetconnecta) para indicar que ha creado el nuevo identificador. Esto permite que la función llamada a Win32 application [InternetCloseHandle](/windows/desktop/api/wininet/nf-wininet-internetclosehandle) desde otro subproceso, si la conexión está tardando demasiada. Consulte la SDKfor de Windows para obtener más información acerca de estas funciones.|
|INTERNET_STATUS_HANDLE_CLOSING|Este valor de identificador se finalizó correctamente.|

Reemplace esta función miembro para requerir alguna acción antes de realiza una rutina de devolución de llamada de estado.

> [!NOTE]
> Las devoluciones de llamada de estado necesitan protección del estado de subproceso. Si usa MFC en una biblioteca compartida, agregue la siguiente línea al principio de la invalidación:

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

Para obtener más información acerca de las operaciones asincrónicas, vea el artículo [Internet primeros pasos: WinInet](../../mfc/wininet-basics.md).

## <a name="openurl"></a>  CInternetSession::OpenURL

Llame a este miembro de función para enviar la solicitud especificada para el servidor HTTP y permitir al cliente especificar RFC822 adicionales, MIME o encabezados HTTP que se envían junto con la solicitud.

```cpp
CStdioFile* OpenURL(
    LPCTSTR pstrURL,
    DWORD_PTR dwContext = 1,
    DWORD dwFlags = INTERNET_FLAG_TRANSFER_ASCII,
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLength = 0);
```

### <a name="parameters"></a>Parámetros

*pstrURL*<br/>
Un puntero al nombre de la dirección URL debe comenzar la lectura. Solo las direcciones URL a partir de archivos:, ftp:, gopher:, o http: se admiten. Valida si *pstrURL* es NULL.

*dwContext*<br/>
Se pasa un valor definido por la aplicación con el identificador devuelto en la devolución de llamada.

*dwFlags*<br/>
Las marcas que describen cómo controlar esta conexión. Consulte **comentarios** para obtener más información acerca de las marcas válidas. Las marcas válidas son:

- INTERNET_FLAG_TRANSFER_ASCII el valor predeterminado. Transfiera el archivo como texto ASCII.

- INTERNET_FLAG_TRANSFER_BINARY transfiera el archivo como un archivo binario.

- INTERNET_FLAG_RELOAD obtener los datos de la conexión incluso si localmente se almacena en caché.

- INTERNET_FLAG_DONT_CACHE no almacenar en caché los datos, ya sea localmente o en las puertas de enlace.

- INTERNET_FLAG_SECURE esta marca es aplicable a solo las solicitudes HTTP. Solicitudes de transacciones seguras en la conexión con la capa de Sockets seguros o PCT.

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT si es posible, reutilizar las conexiones existentes en el servidor para las nuevas solicitudes generadas por `OpenUrl` en lugar de crear una nueva sesión para cada solicitud de conexión.

- INTERNET_FLAG_PASSIVE se usa para un sitio FTP. Utiliza la semántica FTP pasiva. Puede usar con [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) de `OpenURL`.

*pstrHeaders*<br/>
Un puntero a una cadena que contiene los encabezados que se va a enviarse al servidor HTTP.

*dwHeadersLength*<br/>
La longitud, en caracteres, de los encabezados adicionales. Si es-1 L y *pstrHeaders* es distinto de NULL, a continuación, *pstrHeaders* se supone que sea cero termina y se calcula la longitud.

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador de archivo para servicios de Internet del tipo de archivo, HTTP, GOPHER y FTP. Devuelve NULL si el análisis se realizó correctamente.

El puntero que `OpenURL` devuelve depende *pstrURL*del tipo de servicio. La siguiente tabla muestra los posibles punteros `OpenURL` puede devolver.

|Tipo de dirección URL|Valores devueltos|
|--------------|-------------|
|file://|`CStdioFile*`|
|http://|`CHttpFile*`|
|gopher://|`CGopherFile*`|
|ftp://|`CInternetFile*`|

### <a name="remarks"></a>Comentarios

El parámetro *dwFlags* debe incluir INTERNET_FLAG_TRANSFER_ASCII o INTERNET_FLAG_TRANSFER_BINARY, pero no ambos. Las marcas restantes se pueden combinar bit a bit **o** operador ( **&#124;** ).

`OpenURL`, que contiene la función de Win32 `InternetOpenURL`, permite sólo descarga, recuperar y leer los datos de un servidor de Internet. `OpenURL` no permite ninguna manipulación de archivos en una ubicación remota, por lo que requiere n [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) objeto.

Para usar específico de la conexión (es decir, específicos del protocolo) las funciones, como escribir en un archivo, primero debe abrir una sesión, a continuación, abrir un determinado tipo de conexión y luego usar esa conexión para abrir un archivo en el modo deseado. Consulte `CInternetConnection` para obtener más información acerca de las funciones específicos de la conexión.

## <a name="operator_hinternet"></a>  CInternetSession::operator HINTERNET

Utilice este operador para obtener el identificador de Windows para la sesión actual de Internet.

```cpp
operator HINTERNET() const;
```

## <a name="setcookie"></a>  CInternetSession::SetCookie

Establece una cookie para la dirección URL especificada.

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>Parámetros

*pstrUrl*<br/>
Un puntero a una cadena terminada en null que especifica la dirección URL para el que se debe establecer la cookie.

*pstrCookieName*<br/>
Un puntero a una cadena que contiene el nombre de la cookie.

*pstrCookieData*<br/>
Un puntero a una cadena que contiene los datos de cadena real para asociar la dirección URL.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se realiza correctamente o falso en caso contrario. Para obtener el código de error específico, llame a `GetLastError.`

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [InternetSetCookie](/windows/desktop/api/wininet/nf-wininet-internetsetcookiea), tal y como se describe en el SDK de Windows.

## <a name="setoption"></a>  CInternetSession::SetOption

Llame a esta función miembro para establecer las opciones para la sesión de Internet.

```cpp
BOOL SetOption(
    DWORD dwOption,
    LPVOID lpBuffer,
    DWORD dwBufferLength,
    DWORD dwFlags = 0);

BOOL SetOption(
    DWORD dwOption,
    DWORD dwValue,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parámetros

*dwOption*<br/>
Para establecer la opción de Internet. Consulte [marcas de opción](/windows/desktop/WinInet/option-flags) en el SDKfor una lista de las posibles opciones de Windows.

*lpBuffer*<br/>
Un búfer que contiene el valor de opción.

*dwBufferLength*<br/>
La longitud de *lpBuffer* o el tamaño de *dwValue*.

*dwValue*<br/>
DWORD que contiene el valor de opción.

*dwFlags*<br/>
Indica las distintas opciones de almacenamiento en caché. El valor predeterminado se establece en 0. Los valores posibles incluyen:

- INTERNET_FLAG_DONT_CACHE no almacenar en caché los datos, ya sea localmente o en cualquier servidor de puerta de enlace.

- Descargar INTERNET_FLAG_OFFLINE operaciones se satisfacen a través de la caché de persistente. Si el elemento no existe en la memoria caché, se devuelve un código de error adecuado. Esta marca se puede combinar con el bit a bit **o** ( **&#124;** ) operador.

### <a name="return-value"></a>Valor devuelto

Si la operación fue correcta, se devuelve un valor TRUE. Si se produjo un error, se devuelve un valor FALSE. Si se produce un error en la llamada, la función de Win32 [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror) puede llamarse para determinar la causa del error.

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpConnection (clase)](../../mfc/reference/chttpconnection-class.md)<br/>
[CFtpConnection (clase)](../../mfc/reference/cftpconnection-class.md)<br/>
[CGopherConnection (clase)](../../mfc/reference/cgopherconnection-class.md)
