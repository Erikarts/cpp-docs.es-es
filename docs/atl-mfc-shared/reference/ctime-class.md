---
title: CTime (clase)
ms.date: 10/18/2018
f1_keywords:
- CTime
- ATLTIME/ATL::CTime
- ATLTIME/ATL::CTime::CTime
- ATLTIME/ATL::CTime::Format
- ATLTIME/ATL::CTime::FormatGmt
- ATLTIME/ATL::CTime::GetAsDBTIMESTAMP
- ATLTIME/ATL::CTime::GetAsSystemTime
- ATLTIME/ATL::CTime::GetCurrentTime
- ATLTIME/ATL::CTime::GetDay
- ATLTIME/ATL::CTime::GetDayOfWeek
- ATLTIME/ATL::CTime::GetGmtTm
- ATLTIME/ATL::CTime::GetHour
- ATLTIME/ATL::CTime::GetLocalTm
- ATLTIME/ATL::CTime::GetMinute
- ATLTIME/ATL::CTime::GetMonth
- ATLTIME/ATL::CTime::GetSecond
- ATLTIME/ATL::CTime::GetTime
- ATLTIME/ATL::CTime::GetYear
- ATLTIME/ATL::CTime::Serialize64
helpviewer_keywords:
- CTime class
- shared classes, CTime
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
ms.openlocfilehash: a73baab3e43467b76c1b4e3592314a4323d22ffb
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893982"
---
# <a name="ctime-class"></a>CTime (clase)

Representa una fecha y hora absoluta.

## <a name="syntax"></a>Sintaxis

```
class CTime
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CTime::CTime](#ctime)|Construye `CTime` objetos de varias maneras.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CTime::Format](#format)|Convierte un `CTime` objeto en una cadena con formato, según la zona horaria local.|
|[CTime::FormatGmt](#formatgmt)|Convierte un `CTime` objeto en una cadena con formato, según la hora UTC.|
|[CTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Convierte la información de hora almacenada en el `CTime` objeto a una estructura DBTIMESTAMP compatible con Win32.|
|[CTime::GetAsSystemTime](#getassystemtime)|Convierte la información de hora almacenada en el `CTime` objeto a una compatible con Win32 [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) estructura.|
|[CTime::GetCurrentTime](#getcurrenttime)|Crea un `CTime` objeto que representa la hora actual (función miembro estática).|
|[CTime::GetDay](#getday)|Devuelve el representan día por el `CTime` objeto.|
|[CTime::GetDayOfWeek](#getdayofweek)|Devuelve el día de la semana representado por la `CTime` objeto.|
|[CTime::GetGmtTm](#getgmttm)|Divide un `CTime` objeto en componentes, según la hora UTC.|
|[CTime::GetHour](#gethour)|Devuelve la hora representada por el `CTime` objeto.|
|[CTime::GetLocalTm](#getlocaltm)|Divide un `CTime` objeto en componentes, en función de la zona horaria local.|
|[CTime::GetMinute](#getminute)|Devuelve el minuto representado por la `CTime` objeto.|
|[CTime::GetMonth](#getmonth)|Devuelve el mes representado por la `CTime` objeto.|
|[CTime::GetSecond](#getsecond)|Devuelve el segundo representado por la `CTime` objeto.|
|[CTime::GetTime](#gettime)|Devuelve un **__time64_t** valor para el determinado `CTime` objeto.|
|[CTime::GetYear](#getyear)|Devuelve el año representado por el `CTime` objeto.|
|[CTime::Serialize64](#serialize64)|Serializa los datos hacia o desde un archivo.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator + -](#operator_add_-)|Estos operadores de suma y resta `CTimeSpan` y `CTime` objetos.|
|[operator +=, -=](#operator_add_eq_-_eq)|Estos operadores de suma y resta un `CTimeSpan` objetos hacia y desde este `CTime` objeto.|
|[operator =](#operator_eq)|El operador de asignación.|
|[operador ==, <, etcetera.](#ctime_comparison_operators)|Operadores de comparación.|

## <a name="remarks"></a>Comentarios

`CTime` no tiene una clase base.

`CTime` los valores se basan en hora universal coordinada (UTC), que es equivalente a la hora de Universal coordinada (hora del meridiano de Greenwich, hora peninsular española). Consulte [administración del tiempo](../../c-runtime-library/time-management.md) para obtener información acerca de cómo se determina la zona horaria.

Cuando creas un `CTime` de objetos, establezca el `nDST` parámetro en 0 para indicar que la hora estándar está en vigor, o en un valor mayor que 0 para indicar que el horario de verano está en vigor, o en un valor menor que cero para que el COMPUTE de código de biblioteca en tiempo de ejecución de C e si hora estándar o el horario de verano está vigente. `tm_isdst` es un campo obligatorio. Si no se establece, su valor es indefinido y el valor devuelto de [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) es imprevisible. Si `timeptr` apunta a una estructura de tm devuelta por una llamada anterior a [asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md), [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md), o [localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), el `tm_isdst` campo contiene el valor correcto.

Una clase complementaria, [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md), representa un intervalo de tiempo.

El `CTime` y `CTimeSpan` clases no están diseñadas para la derivación. Dado que no hay ninguna función virtual, el tamaño de `CTime` y `CTimeSpan` objetos es exactamente de 8 bytes. La mayoría de las funciones de miembro están alineados.

> [!NOTE]
>  El límite superior de fecha es 12/31/3000. El límite inferior es 1/1/1970 12:00:00 A.M. GMT.

Para obtener más información sobre el uso de `CTime`, consulte los artículos [fecha y hora](../../atl-mfc-shared/date-and-time.md), y [administración del tiempo](../../c-runtime-library/time-management.md) en la referencia de la biblioteca de tiempo de ejecución.

> [!NOTE]
>  El `CTime` estructura cambió de MFC 7.1 a MFC 8.0. Si se serializa un `CTime` estructura mediante la **operador <<** en MFC 8.0 o una versión posterior, el archivo resultante no serán legible en las versiones anteriores de MFC.

## <a name="requirements"></a>Requisitos

**Encabezado:** atltime.h

##  <a name="ctime_comparison_operators"></a>  Operadores de comparación CTime

Operadores de comparación.

```
bool operator==(CTime time) const throw();
bool operator!=(CTime time) const throw();
bool operator<(CTime time) const throw();
bool operator>(CTime time) const throw();
bool operator<=(CTime time) const throw();
bool operator>=(CTime time) const throw();
```

### <a name="parameters"></a>Parámetros

*time*<br/>
Objeto `CTime` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Estos operadores comparan dos veces absolutas y devuelve TRUE si la condición es true; en caso contrario, FALSE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

##  <a name="ctime"></a>  CTime::CTime

Crea un nuevo `CTime` objeto inicializado con el tiempo especificado.

```
CTime() throw();
CTime(__time64_t time) throw();
CTime(int nYear, int nMonth, int nDay,
      int nHour, int nMin, int nSec, int nDST = -1);
CTime(WORD wDosDate, WORD wDosTime, int nDST = -1);
CTime(const SYSTEMTIME& st, int nDST = - 1) throw();
CTime(const FILETIME& ft, int nDST = - 1);
CTime(const DBTIMESTAMP& dbts, int nDST = -1) throw();
```

### <a name="parameters"></a>Parámetros

*timeSrc*<br/>
Indica un `CTime` objeto que ya existe.

*time*<br/>
Un `__time64_t` el valor de hora, que es el número de segundos después del 1 de enero de 1970 UTC. Tenga en cuenta que esto también se ajuste a la hora local. Por ejemplo, si se encuentra en Nueva York y crear un `CTime` pasando un parámetro de 0, [CTime::GetMonth](#getmonth) devolverá 12.

*nYear*, *nMonth*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
Indica los valores de fecha y hora en que se copiará en el nuevo `CTime` objeto.

*nDST*<br/>
Indica si el horario de verano está vigente. Puede tener uno de estos tres valores:

- *nDST* establecido en tiempo de 0Standard está en vigor.

- *nDST* establecido en un valor mayor que 0Daylight horario está vigente.

- *nDST* establecido en un valor menor que 0The predeterminado. Calcula automáticamente de si hora estándar o el horario de verano está vigente.

*wDosDate*, *wDosTime*<br/>
Los valores de fecha y hora de MS-DOS para convertirse en un valor de fecha y hora y copiar en el nuevo `CTime` objeto.

*st*<br/>
Un [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) estructura para convertirse en un valor de fecha y hora y copiar en el nuevo `CTime` objeto.

*ft*<br/>
Un [FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) estructura para convertirse en un valor de fecha y hora y copiar en el nuevo `CTime` objeto.

*dbts*<br/>
Una referencia a una estructura DBTIMESTAMP que contiene la hora local actual.

### <a name="remarks"></a>Comentarios

Cada constructor se describe a continuación:

- `CTime();` Construye un sin inicializar `CTime` objeto. Este constructor permite definir `CTime` matrices de objetos. Se deben inicializar estas matrices con horas válidas antes de usar.

- `CTime( const CTime& );` Construye un `CTime` objeto desde otro `CTime` valor.

- `CTime( __time64_t );` Construye un `CTime` objeto desde un **__time64_t** tipo. Este constructor espera una hora UTC y convierte el resultado en una hora local antes de almacenar el resultado.

- `CTime( int, int, ...);` Construye un `CTime` objeto a partir de los componentes de hora local con cada componente se limita a los siguientes intervalos:

   |Componente|Intervalo|
   |---------------|-----------|
   |*nYear*|1970-3000|
   |*nMonth*|1-12|
   |*nDay*|1-31|
   |*nHour*|0-23|
   |*nMin*|0-59|
   |*nSec*|0-59|

   Este constructor realiza la conversión apropiada a la hora UTC. La versión de depuración de la biblioteca Microsoft Foundation Class aserciones si uno o varios de los componentes de tiempo están fuera del intervalo. Debe validar los argumentos antes de llamar a. Este constructor espera una hora local.

- `CTime( WORD, WORD );` Construye un `CTime` objeto a partir de los valores de fecha y hora de MS-DOS especificados. Este constructor espera una hora local.

- `CTime( const SYSTEMTIME& );` Construye un `CTime` objeto desde un `SYSTEMTIME` estructura. Este constructor espera una hora local.

- `CTime( const FILETIME& );` Construye un `CTime` objeto desde un `FILETIME` estructura. Lo más probable es que no usará `CTime FILETIME` inicialización directamente. Si usa un `CFile` objeto para manipular un archivo, `CFile::GetStatus` recupera la marca de tiempo del archivo por usted a través de un `CTime` objeto inicializado con un `FILETIME` estructura. Este constructor asume un tiempo según la hora UTC y convierte automáticamente el valor a la hora local antes de almacenar el resultado.

   > [!NOTE]
   > El constructor utilizando `DBTIMESTAMP` parámetro solo está disponible cuando se incluye OLEDB.h.

Para obtener más información, consulte el [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) y [FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) estructura en el SDK de Windows. Consulte también el [MS-DOS fecha y hora](/windows/desktop/SysInfo/ms-dos-date-and-time) entrada en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

##  <a name="format"></a>  CTime::Format

Llame a esta función miembro para crear una representación con formato del valor de fecha y hora.

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parámetros

*pszFormat*<br/>
Cadena de un formato similar a la `printf` cadena de formato. Códigos de formato, precedidos por un porcentaje (`%`) inicie sesión, se reemplazan por la correspondiente `CTime` componente. Otros caracteres en la cadena de formato se copian sin cambios a la cadena devuelta. Vea la función de tiempo de ejecución [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para obtener una lista de códigos de formato.

*nFormatID*<br/>
El identificador de la cadena que identifica este formato.

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la hora con formato.

### <a name="remarks"></a>Comentarios

Si el estado de este `CTime` objeto es null, el valor devuelto es una cadena vacía.

Este método produce una excepción si el valor de fecha y hora para dar formato a no está comprendida entre la medianoche del 1 de enero de 1970 a través del 31 de diciembre de 3000, hora Universal coordinada (UTC).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

##  <a name="formatgmt"></a>  CTime::FormatGmt

Genera una cadena con formato que corresponde a este `CTime` objeto.

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>Parámetros

*pszFormat*<br/>
Especifica una cadena de formato similar a la `printf` cadena de formato. Vea la función de tiempo de ejecución [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para obtener más información.

*nFormatID*<br/>
El identificador de la cadena que identifica este formato.

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la hora con formato.

### <a name="remarks"></a>Comentarios

No se convierte el valor de tiempo y, por tanto, refleja la hora UTC.

Este método produce una excepción si el valor de fecha y hora para dar formato a no está comprendida entre la medianoche del 1 de enero de 1970 a través del 31 de diciembre de 3000, hora Universal coordinada (UTC).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CTime::Format](#format).

##  <a name="getasdbtimestamp"></a>  CTime::GetAsDBTIMESTAMP

Llame a esta función miembro para convertir la información de hora almacenada en el `CTime` objeto a una estructura DBTIMESTAMP compatible con Win32.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>Parámetros

*dbts*<br/>
Una referencia a una estructura DBTIMESTAMP que contiene la hora local actual.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Almacena la hora resultante en la que se hace referencia *dbts* estructura. El `DBTIMESTAMP` estructura de datos inicializada por esta función tendrá su `fraction` miembro establecido en cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

##  <a name="getassystemtime"></a>  CTime::GetAsSystemTime

Llame a esta función miembro para convertir la información de hora almacenada en el `CTime` objeto a una compatible con Win32 [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) estructura.

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>Parámetros

*timeDest*<br/>
Una referencia a un [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) estructura que va a contener el valor de fecha y hora convertido de la `CTime` objeto.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

`GetAsSystemTime` almacena la hora resultante en la que se hace referencia *timeDest* estructura. El `SYSTEMTIME` estructura de datos inicializada por esta función tendrá su `wMilliseconds` miembro establecido en cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

##  <a name="getcurrenttime"></a>  CTime::GetCurrentTime

Devuelve un `CTime` objeto que representa la hora actual.

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>Comentarios

Devuelve la fecha actual del sistema y la hora en hora Universal coordinada (UTC).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

##  <a name="getday"></a>  CTime::GetDay

Devuelve el representan día por el `CTime` objeto.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el día del mes, según la hora local, en el intervalo de 1 a 31.

### <a name="remarks"></a>Comentarios

Esta función llama a `GetLocalTm`, que utiliza un búfer asignado estáticamente interno. Se sobrescriben los datos de este búfer debido a llamadas a otros `CTime` funciones miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

##  <a name="getdayofweek"></a>  CTime::GetDayOfWeek

Devuelve el día de la semana representado por la `CTime` objeto.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el día de la semana según la hora local; 1 = el domingo, 2 = el lunes, 7 = el sábado.

### <a name="remarks"></a>Comentarios

Esta función llama a `GetLocalTm`, que utiliza una instancia interna de forma estática asigna el búfer. Se sobrescriben los datos de este búfer debido a llamadas a otros `CTime` funciones miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

##  <a name="getgmttm"></a>  CTime::GetGmtTm

Obtiene un **struct tm** que contiene una descomposición de los casos incluidos en este `CTime` objeto.

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*ptm*<br/>
Apunta a un búfer que recibirá los datos de tiempo. Si este puntero es NULL, se produce una excepción.

### <a name="return-value"></a>Valor devuelto

Un puntero a un relleno de **struct tm** tal como se define en el archivo de inclusión del tiempo. H. Consulte [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) para el diseño de la estructura.

### <a name="remarks"></a>Comentarios

`GetGmtTm` Devuelve la hora UTC.

*ptm* no puede ser NULL. Si desea revertir al comportamiento anterior, en el que *ptm* podría ser NULL para indicar que una instancia interna, debe usarse un búfer asignado estáticamente, a continuación, anular la definición de _SECURE_ATL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

##  <a name="gethour"></a>  CTime::GetHour

Devuelve la hora representada por el `CTime` objeto.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la hora, según la hora local, en el intervalo de 0 a 23.

### <a name="remarks"></a>Comentarios

Esta función llama a `GetLocalTm`, que utiliza una instancia interna de forma estática asigna el búfer. Se sobrescriben los datos de este búfer debido a llamadas a otros `CTime` funciones miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

##  <a name="getlocaltm"></a>  CTime::GetLocalTm

Obtiene un **struct tm** que contiene una descomposición de los casos incluidos en este `CTime` objeto.

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parámetros

*ptm*<br/>
Apunta a un búfer que recibirá los datos de tiempo. Si este puntero es NULL, se produce una excepción.

### <a name="return-value"></a>Valor devuelto

Un puntero a un relleno de **struct tm** tal como se define en el archivo de inclusión del tiempo. H. Consulte [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) para el diseño de la estructura.

### <a name="remarks"></a>Comentarios

`GetLocalTm` Devuelve la hora local.

*ptm* no puede ser NULL. Si desea revertir al comportamiento anterior, en el que *ptm* podría ser NULL para indicar que una instancia interna, debe usarse un búfer asignado estáticamente, a continuación, anular la definición de _SECURE_ATL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

##  <a name="getminute"></a>  CTime::GetMinute

Devuelve el minuto representado por la `CTime` objeto.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el minuto, según la hora local, en el intervalo de 0 a 59.

### <a name="remarks"></a>Comentarios

Esta función llama a `GetLocalTm`, que utiliza una instancia interna de forma estática asigna el búfer. Se sobrescriben los datos de este búfer debido a llamadas a otros `CTime` funciones miembro.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHour](#gethour).

##  <a name="getmonth"></a>  CTime::GetMonth

Devuelve el mes representado por la `CTime` objeto.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el mes, según la hora local, en el intervalo del 1 al 12 (1 = enero).

### <a name="remarks"></a>Comentarios

Esta función llama a `GetLocalTm`, que utiliza una instancia interna de forma estática asigna el búfer. Se sobrescriben los datos de este búfer debido a llamadas a otros `CTime` funciones miembro.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetDay](#getday).

##  <a name="getsecond"></a>  CTime::GetSecond

Devuelve el segundo representado por la `CTime` objeto.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el segundo, según la hora local, en el intervalo de 0 a 59.

### <a name="remarks"></a>Comentarios

Esta función llama a `GetLocalTm`, que utiliza una instancia interna de forma estática asigna el búfer. Se sobrescriben los datos de este búfer debido a llamadas a otros `CTime` funciones miembro.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHour](#gethour).

##  <a name="gettime"></a>  CTime::GetTime

Devuelve un **__time64_t** valor para el determinado `CTime` objeto.

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>Valor devuelto

`GetTime` Devuelve el número de segundos entre la actual `CTime` objeto y el 1 de enero de 1970.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

##  <a name="getyear"></a>  CTime::GetYear

Devuelve el año representado por el `CTime` objeto.

```
int GetYear();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el año, según la hora local, en el intervalo de enero 1,1970 a 18 de enero de 2038 (inclusive).

### <a name="remarks"></a>Comentarios

Esta función llama a `GetLocalTm`, que utiliza una instancia interna de forma estática asigna el búfer. Se sobrescriben los datos de este búfer debido a llamadas a otros `CTime` funciones miembro.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetDay](#getday).

##  <a name="operator_eq"></a>  CTime::operator =

El operador de asignación.

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>Parámetros

*time*<br/>
El valor de fecha y hora nuevas.

### <a name="return-value"></a>Valor devuelto

La actualización `CTime` objeto.

### <a name="remarks"></a>Comentarios

Este operador de asignación sobrecargado copia la hora de origen en esta `CTime` objeto. El almacenamiento interno del tiempo en un `CTime` objeto es independiente de la zona horaria. Conversión de zona horaria no es necesaria durante la asignación.

##  <a name="operator_add_-"></a>  CTime::operator +, -

Estos operadores de suma y resta `CTimeSpan` y `CTime` objetos.

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>Parámetros

*timeSpan*<br/>
La `CTimeSpan` objeto se va a sumar o restar.

*time*<br/>
La `CTime` objeto va a restar.

### <a name="return-value"></a>Valor devuelto

Un `CTime` o `CTimeSpan` objeto que representa el resultado de la operación.

### <a name="remarks"></a>Comentarios

`CTime` los objetos representan el tiempo absoluto, `CTimeSpan` objetos representan el tiempo relativo. Los dos primeros operadores permiten sumar y restar `CTimeSpan` objetos a y desde `CTime` objetos. El tercer operador permite que se va a restar uno `CTime` objeto desde otro para producir un `CTimeSpan` objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  CTime::operator +=, =

Estos operadores de suma y resta un `CTimeSpan` objetos hacia y desde este `CTime` objeto.

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parámetros

*span*<br/>
La `CTimeSpan` objeto se va a sumar o restar.

### <a name="return-value"></a>Valor devuelto

La actualización `CTime` objeto.

### <a name="remarks"></a>Comentarios

Estos operadores permiten sumar y restar un `CTimeSpan` objetos hacia y desde este `CTime` objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

##  <a name="serialize64"></a>  CTime::Serialize64

> [!NOTE]
> Este método solo está disponible en proyectos de MFC.

Serializa los datos asociados con la variable de miembro a o desde un archivo.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*ar*<br/>
La `CArchive` objeto que se va a actualizar.

### <a name="return-value"></a>Valor devuelto

La actualización `CArchive` objeto.

## <a name="see-also"></a>Vea también

[asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)<br/>
[_ftime_s, _ftime32_s, _ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[CTimeSpan (clase)](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas ATL y MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
