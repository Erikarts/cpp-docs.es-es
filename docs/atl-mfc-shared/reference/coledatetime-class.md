---
title: COleDateTime (clase)
ms.date: 03/27/2019
f1_keywords:
- COleDateTime
- ATLCOMTIME/ATL::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::Format
- ATLCOMTIME/ATL::COleDateTime::GetAsDBTIMESTAMP
- ATLCOMTIME/ATL::COleDateTime::GetAsSystemTime
- ATLCOMTIME/ATL::COleDateTime::GetAsUDATE
- ATLCOMTIME/ATL::COleDateTime::GetCurrentTime
- ATLCOMTIME/ATL::COleDateTime::GetDay
- ATLCOMTIME/ATL::COleDateTime::GetDayOfWeek
- ATLCOMTIME/ATL::COleDateTime::GetDayOfYear
- ATLCOMTIME/ATL::COleDateTime::GetHour
- ATLCOMTIME/ATL::COleDateTime::GetMinute
- ATLCOMTIME/ATL::COleDateTime::GetMonth
- ATLCOMTIME/ATL::COleDateTime::GetSecond
- ATLCOMTIME/ATL::COleDateTime::GetStatus
- ATLCOMTIME/ATL::COleDateTime::GetYear
- ATLCOMTIME/ATL::COleDateTime::ParseDateTime
- ATLCOMTIME/ATL::COleDateTime::SetDate
- ATLCOMTIME/ATL::COleDateTime::SetDateTime
- ATLCOMTIME/ATL::COleDateTime::SetStatus
- ATLCOMTIME/ATL::COleDateTime::SetTime
- ATLCOMTIME/ATL::COleDateTime::m_dt
- ATLCOMTIME/ATL::COleDateTime::m_status
helpviewer_keywords:
- shared classes, COleDateTime
- time-only values
- Date data type, MFC encapsulation of
- COleDateTime class
- dates, handling in MFC
- time, handling in MFC
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
ms.openlocfilehash: 63c2971f5d55cb5198925650bcf90b2f1a8b0958
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503226"
---
# <a name="coledatetime-class"></a>COleDateTime (clase)

Encapsula el `DATE` tipo de datos que se usa en la automatización OLE.

## <a name="syntax"></a>Sintaxis

```
class COleDateTime
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[COleDateTime::COleDateTime](#coledatetime)|Construye un objeto `COleDateTime`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleDateTime::Format](#format)|Genera una representación de cadena con formato de un `COleDateTime` objeto.|
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Llame a este método para obtener la hora en la `COleDateTime` objeto como un `DBTIMESTAMP` estructura de datos.|
|[COleDateTime::GetAsSystemTime](#getassystemtime)|Llame a este método para obtener la hora en la `COleDateTime` objeto como un [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) estructura de datos.|
|[COleDateTime::GetAsUDATE](#getasudate)|Llame a este método para obtener la hora en la `COleDateTime` como un `UDATE` estructura de datos.|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|Crea un `COleDateTime` objeto que representa la hora actual (función miembro estática).|
|[COleDateTime::GetDay](#getday)|Devuelve el día esto `COleDateTime` objeto representa (1-31).|
|[COleDateTime::GetDayOfWeek](#getdayofweek)|Devuelve el día de la semana esto `COleDateTime` objeto representa (el domingo = 1).|
|[COleDateTime::GetDayOfYear](#getdayofyear)|Devuelve el día del año esto `COleDateTime` objeto representa (1 de enero = 1).|
|[COleDateTime::GetHour](#gethour)|Devuelve la hora esto `COleDateTime` objeto representa (0 - 23).|
|[COleDateTime::GetMinute](#getminute)|Devuelve el minuto esto `COleDateTime` objeto representa (0 - 59).|
|[COleDateTime::GetMonth](#getmonth)|Devuelve el mes esto `COleDateTime` objeto representa (1-12).|
|[COleDateTime::GetSecond](#getsecond)|Devuelve el segundo esto `COleDateTime` objeto representa (0 - 59).|
|[COleDateTime::GetStatus](#getstatus)|Obtiene el estado (validez) de este `COleDateTime` objeto.|
|[COleDateTime::GetYear](#getyear)|Devuelve el año esto `COleDateTime` objeto representa.|
|[COleDateTime::ParseDateTime](#parsedatetime)|Lee un valor de fecha y hora de una cadena y establece el valor de `COleDateTime`.|
|[COleDateTime::SetDate](#setdate)|Establece el valor de este `COleDateTime` objeto por el valor de solo fecha especificado.|
|[COleDateTime::SetDateTime](#setdatetime)|Establece el valor de este `COleDateTime` objeto por el valor de fecha u hora especificada.|
|[COleDateTime::SetStatus](#setstatus)|Establece el estado (validez) de este `COleDateTime` objeto.|
|[COleDateTime::SetTime](#settime)|Establece el valor de este `COleDateTime` objeto en el valor solo de tiempo especificado.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[COleDateTime:: operador ==, COleDateTime:: operador <, etcetera.](#coledatetime_relational_operators)|Comparar dos `COleDateTime` valores.|
|[COleDateTime:: operador + COleDateTime:: operador:](#operator_add_-)|Sumar y restar `COleDateTime` valores.|
|[COleDateTime::operator +=, COleDateTime::operator -=](#operator_add_eq_-_eq)|Sumar y restar un `COleDateTime` valor de este `COleDateTime` objeto.|
|[COleDateTime::operator =](#operator_eq)|Copia un `COleDateTime` valor.|
|[COleDateTime::operator DATE, COleDateTime::operator Date*](#operator_date)|Convierte un `COleDateTime` valor en un `DATE` o `DATE*`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[COleDateTime::m_dt](#m_dt)|Contiene subyacente `DATE` para este `COleDateTime` objeto.|
|[COleDateTime::m_status](#m_status)|Contiene el estado de este `COleDateTime` objeto.|

## <a name="remarks"></a>Comentarios

`COleDateTime` no tiene una clase base.

Es uno de los tipos posibles de la [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) tipo de datos de la automatización OLE. Un `COleDateTime` valor representa una fecha absoluta y el valor de tiempo.

El `DATE` se implementa como un valor de punto flotante. Días se miden a partir del 30 de diciembre de 1899 a medianoche. En la tabla siguiente se muestra algunas fechas y sus valores asociados:

|Fecha|Valor|
|----------|-----------|
|29 de diciembre de 1899, medianoche|-1.0|
|29 de diciembre de 1899, 6 A.M.|-1.25|
|30 de diciembre de 1899, medianoche|0.0|
|Medianoche del 31 de diciembre de 1899.|1.0|
|1 de enero de 1900, 6 a. M.|2.25|

> [!CAUTION]
> En la tabla anterior, aunque los valores de día pasa a ser negativos antes de la medianoche del 30 de diciembre de 1899, los valores de hora del día no lo hacen. Por ejemplo, 6:00 a. M. siempre se representa con un valor fraccionario 0,25 independientemente de si el entero que representa el día es positivo (después del 30 de diciembre de 1899) o negativo (antes del 30 de diciembre de 1899). Esto significa que una comparación de punto flotante simple desea ordenar erróneamente una `COleDateTime` que representa 6:00 a 12/29/1899 como **más adelante** que uno que representa 7:00 A.M. en el mismo día.

La `COleDateTime` clase controla las fechas desde el 1 de enero de 100 hasta el 31 de diciembre de 9999. La `COleDateTime` clase usa el calendario gregoriano; no admite fechas del calendario juliano. `COleDateTime` omite el horario de verano. (Consulte [fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).)

> [!NOTE]
> Puede usar el `%y` formato para recuperar un año de dos dígitos solo para las fechas a partir de 1900. Si usas el `%y` formato en una fecha anterior a 1900, el código genera un error de aserción.

Este tipo también se utiliza para representar los valores de solo fecha o solo de tiempo. Por convención, la fecha 0 (30 de diciembre de 1899) se usa para los valores de solo tiempo y la hora 00:00 (medianoche) se usa para los valores de solo fecha.

Si creas un `COleDateTime` objeto mediante el uso de una fecha menor que 100, la fecha es aceptadas, pero en posteriores llamadas a `GetYear`, `GetMonth`, `GetDay`, `GetHour`, `GetMinute`, y `GetSecond` producirá un error y devuelven -1. Anteriormente, podría utilizar las fechas de dos dígitos, pero las fechas deben ser 100 o más grande en MFC 4.2 y versiones posteriores.

Para evitar problemas, especifique una fecha de cuatro dígitos. Por ejemplo:

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

Operaciones aritméticas básicas para la `COleDateTime` valores usan la clase complementaria [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md). `COleDateTimeSpan` los valores de definen un intervalo de tiempo. La relación entre estas clases es similar a la entre [CTime](../../atl-mfc-shared/reference/ctime-class.md) y [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Para obtener más información sobre la `COleDateTime` y `COleDateTimeSpan` las clases, consulte el artículo [fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Requisitos

**Encabezado**: ATLComTime.h

##  <a name="coledatetime_relational_operators"></a>  Operadores relacionales COleDateTime

Operadores de comparación.

```
bool operator==(const COleDateTime& date) const throw();
bool operator!=(const COleDateTime& date) const throw();
bool operator<(const COleDateTime& date) const throw();
bool operator>(const COleDateTime& date) const throw();
bool operator<=(const COleDateTime& date) const throw();
bool operator>=(const COleDateTime& date) const throw();
```

### <a name="parameters"></a>Parámetros

*date*<br/>
Objeto `COleDateTime` que se va a comparar.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Si cualquiera de los dos operandos no es válido, se producirá un ATLASSERT.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>Ejemplo

Los operadores **>=** , **\< =** , **>** , y **<** , se producirá una aserción si el `COleDateTime` objeto está establecido en null.

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

##  <a name="coledatetime"></a>  COleDateTime::COleDateTime

Construye un objeto `COleDateTime`.

```
COleDateTime() throw();
COleDateTime(const VARIANT& varSrc) throw();
COleDateTime(DATE dtSrc) throw();
COleDateTime(time_t timeSrc) throw();
COleDateTime(__time64_t timeSrc) throw();
COleDateTime(const SYSTEMTIME& systimeSrc) throw();
COleDateTime(const FILETIME& filetimeSrc) throw();

COleDateTime(int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();

COleDateTime(WORD wDosDate,
    WORD wDosTime) throw();
COleDateTime(const DBTIMESTAMP& timeStamp) throw();
```

### <a name="parameters"></a>Parámetros

*dateSrc*<br/>
Existente `COleDateTime` objeto que se copiará en el nuevo `COleDateTime` objeto.

*varSrc*<br/>
Existente `VARIANT` estructura de datos (posiblemente un `COleVariant` objeto) que se convertirá en un valor de fecha y hora (VT_DATE) y copiar en el nuevo `COleDateTime` objeto.

*dtSrc*<br/>
Una fecha y hora (`DATE`) valor que se copiará en el nuevo `COleDateTime` objeto.

*timeSrc*<br/>
Un `time_t` o `__time64_t` valor al convertirse en un valor de fecha y hora y copiar en el nuevo `COleDateTime` objeto.

*systimeSrc*<br/>
Un `SYSTEMTIME` estructura para convertirse en un valor de fecha y hora y copiar en el nuevo `COleDateTime` objeto.

*filetimeSrc*<br/>
Un `FILETIME` estructura para convertirse en un valor de fecha y hora y copiar en el nuevo `COleDateTime` objeto. Un `FILETIME` usa la hora Universal coordinada (UTC), por lo que si se pasa una hora local en la estructura, los resultados serán incorrectos. Consulte [tiempos archivos](/windows/desktop/SysInfo/file-times) en el SDK de Windows para obtener más información.

*nYear*, *nMonth*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
Indique los valores de fecha y hora en que se copiará en el nuevo `COleDateTime` objeto.

*wDosDate*, *wDosTime*<br/>
Los valores de fecha y hora de MS-DOS para convertirse en un valor de fecha y hora y copiar en el nuevo `COleDateTime` objeto.

*timeStamp*<br/>
Una referencia a un [DBTimeStamp](/dotnet/api/system.data.oledb.oledbtype) estructura que contiene la hora local actual.

### <a name="remarks"></a>Comentarios

Todos estos constructores crean nuevos `COleDateTime` objetos inicializados en el valor especificado. La siguiente tabla muestra los intervalos válidos para cada componente de fecha y hora:

|Componente de fecha y hora|Intervalo válido|
|--------------------------|-----------------|
|año|100 - 9999|
|mes|0 - 12|
|día|0 - 31|
|hora|0 - 23|
|minuto|0 - 59|
|second|0 - 59|

Tenga en cuenta que el límite superior real para el componente de día varía en función de los componentes de mes y año. Para obtener más información, consulte el `SetDate` o `SetDateTime` funciones miembro.

Siguiente es una breve descripción de cada constructor:

- `COleDateTime(` **)** Construye un `COleDateTime` objeto inicializado en 0 (medianoche, 30 de diciembre de 1899).

- `COleDateTime(` `dateSrc` **)** Construye un `COleDateTime` objeto a partir de una máquina `COleDateTime` objeto.

- `COleDateTime(` *varSrc* **)** construye un `COleDateTime` objeto. Intenta convertir un `VARIANT` estructura o [COleVariant](../../mfc/reference/colevariant-class.md) objeto a una fecha y hora ( `VT_DATE`) valor. Si esta conversión se realiza correctamente, el valor convertido se copia en el nuevo `COleDateTime` objeto. Si no, es el valor de la `COleDateTime` objeto se establece en 0 (medianoche, 30 de diciembre de 1899) y su estado a no válido.

- `COleDateTime(` `dtSrc` **)** Construye un `COleDateTime` objeto desde un `DATE` valor.

- `COleDateTime(` `timeSrc` **)** Construye un `COleDateTime` objeto desde un `time_t` valor.

- `COleDateTime(` *systimeSrc* **)** construye un `COleDateTime` objeto desde un `SYSTEMTIME` valor.

- `COleDateTime(` `filetimeSrc` **)** Construye un `COleDateTime` objeto desde un `FILETIME` valor. . Un `FILETIME` usa la hora Universal coordinada (UTC), por lo que si se pasa una hora local en la estructura, los resultados serán incorrectos. Para obtener más información, consulte [tiempos archivos](/windows/desktop/SysInfo/file-times) en el SDK de Windows.

- `COleDateTime(` `nYear``nMonth`, `nDay`, `nHour`, `nMin`, `nSec` **)** Construye un `COleDateTime` objeto a partir de los valores numéricos especificados.

- `COleDateTime(` `wDosDate``wDosTime` **)** Construye un `COleDateTime` objeto a partir de los valores de fecha y hora de MS-DOS especificados.

Para obtener más información sobre la `time_t` tipo de datos, vea el [tiempo](../../c-runtime-library/reference/time-time32-time64.md) funcionando en el *referencia de la biblioteca de tiempo de ejecución*.

Para obtener más información, consulte el [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) y [FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) estructuras en el SDK de Windows.

Para obtener más información acerca de los límites de `COleDateTime` valores, consulte el artículo [fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

> [!NOTE]
> El constructor utilizando `DBTIMESTAMP` parámetro solo está disponible cuando se incluye OLEDB.h.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

##  <a name="format"></a>  COleDateTime::Format

Crea una representación con formato del valor de fecha y hora.

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Indica que uno de los siguientes indicadores de configuración regional:

- LOCALE_NOUSEROVERRIDE usar la configuración regional predeterminada del sistema, en lugar de la configuración de usuario personalizada.

- VAR_TIMEVALUEONLY omitir la parte de fecha durante el análisis.

- VAR_DATEVALUEONLY ignorar el espacio de tiempo durante el análisis.

*lcid*<br/>
Indica el identificador de configuración regional que se usará para la conversión. Para obtener más información acerca de los identificadores de idioma, consulte [los identificadores de idioma](/windows/desktop/Intl/language-identifiers).

*lpszFormat*<br/>
Cadena de un formato similar a la `printf` cadena de formato. Cada formato de código, precedido por un porcentaje ( `%`) inicie sesión, se reemplaza por la correspondiente `COleDateTime` componente. Otros caracteres en la cadena de formato se copian sin cambios a la cadena devuelta. Para obtener más información, vea la función de tiempo de ejecución [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md). El valor y el significado de los códigos de formato para `Format` son:

- `%H` Horas del día actual

- `%M` Minutos de la hora actual

- `%S` Segundos del minuto actual

- `%%` Signo de porcentaje

*nFormatID*<br/>
El identificador de recurso para la cadena de formato de control.

### <a name="return-value"></a>Valor devuelto

Un `CString` que contiene el valor con formato de fecha y hora.

### <a name="remarks"></a>Comentarios

Si el estado de este `COleDateTime` objeto es null, el valor devuelto es una cadena vacía. Si el estado no es válido, se especifica la cadena devuelta por el recurso de cadena ATL_IDS_DATETIME_INVALID.

A continuación se muestra una breve descripción de las tres formas para esta función:

`Format`( *dwFlags*, *lcid*)<br/>
Este formulario da formato al valor mediante el uso de las especificaciones del lenguaje (identificadores de configuración regional) para la fecha y hora. Con los parámetros predeterminados, este formulario imprimirá la fecha y la hora, a menos que la parte de hora es 0 (medianoche), en cuyo caso imprimirá solo la fecha o la parte de fecha es 0 (30 de diciembre de 1899), en cuyo caso se imprimirá el momento. Si el valor de fecha y hora es 0 (30 de diciembre de 1899, medianoche), este formulario con los parámetros predeterminados imprimirá la medianoche.

`Format`( *lpszFormat*)<br/>
Este formulario da formato al valor usando la cadena de formato que contiene códigos de formato especiales que van precedidos por un signo de porcentaje (%), como en `printf`. La cadena de formato se pasa como un parámetro a la función. Para obtener más información acerca de los códigos de formato, vea [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) en la referencia de la biblioteca de tiempo de ejecución.

`Format`( *nFormatID*)<br/>
Este formulario da formato al valor usando la cadena de formato que contiene códigos de formato especiales que van precedidos por un signo de porcentaje (%), como en `printf`. La cadena de formato es un recurso. El Id. de este recurso de cadena se pasa como parámetro. Para obtener más información acerca de los códigos de formato, vea [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) en el *referencia de la biblioteca de tiempo de ejecución*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

##  <a name="getasdbtimestamp"></a>  COleDateTime::GetAsDBTIMESTAMP

Llame a este método para obtener la hora en la `COleDateTime` objeto como un `DBTIMESTAMP` estructura de datos.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>Parámetros

*timeStamp*<br/>
Una referencia a un [DBTimeStamp](/dotnet/api/system.data.oledb.oledbtype) estructura.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Almacena la hora resultante en la que se hace referencia *timeStamp* estructura. El `DBTIMESTAMP` estructura de datos inicializada por esta función tendrá su `fraction` miembro establecido en cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

##  <a name="getassystemtime"></a>  COleDateTime::GetAsSystemTime

Llame a este método para obtener la hora en la `COleDateTime` objeto como un `SYSTEMTIME` estructura de datos.

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>Parámetros

*sysTime*<br/>
Una referencia a un [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) estructura para recibir el valor de fecha y hora convertido desde el `COleDateTime` objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se realiza correctamente; FALSE si se produce un error en la conversión, o si el `COleDateTime` objeto es NULL o no es válido.

### <a name="remarks"></a>Comentarios

`GetAsSystemTime` almacena la hora resultante en la que se hace referencia *sysTime* objeto. El `SYSTEMTIME` estructura de datos inicializada por esta función tendrá su `wMilliseconds` miembro establecido en cero.

Para obtener más información sobre la información de estado se mantiene en un `COleDateTime` de objetos, consulte [GetStatus](#getstatus).

##  <a name="getasudate"></a>  COleDateTime::GetAsUDATE

Llame a este método para obtener la hora en la `COleDateTime` objeto como un `UDATE` estructura de datos.

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>Parámetros

*uDate*<br/>
Una referencia a un `UDATE` estructura para recibir el valor de fecha y hora convertido desde el `COleDateTime` objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se realiza correctamente; FALSE si se produce un error en la conversión, o si el `COleDateTime` objeto es NULL o no es válido.

### <a name="remarks"></a>Comentarios

Un `UDATE` estructura representa una fecha de "desempaquetada".

##  <a name="getcurrenttime"></a>  COleDateTime::GetCurrentTime

Llame a esta función de miembro estático para devolver el valor de fecha y hora actuales.

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

##  <a name="getday"></a>  COleDateTime::GetDay

Obtiene el día del mes representado por este valor de fecha y hora.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Valor devuelto

El día del mes representado por el valor de esta `COleDateTime` objeto o `COleDateTime::error` si no se pudo obtener el día.

### <a name="remarks"></a>Comentarios

Intervalo de valores de retorno válido entre 1 y 31.

Para obtener información sobre otras funciones miembro que consultar el valor de este `COleDateTime` de objetos, vea las funciones miembro siguientes:

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

##  <a name="getdayofweek"></a>  COleDateTime::GetDayOfWeek

Obtiene el día del mes representado por este valor de fecha y hora.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Valor devuelto

El día de la semana representado por el valor de esta `COleDateTime` objeto o `COleDateTime::error` si no se pudo obtener el día de la semana.

### <a name="remarks"></a>Comentarios

Retorno válido los valores pueden oscilar entre 1 y 7, donde 1 = el domingo, 2 = el lunes y así sucesivamente.

Para obtener información sobre otras funciones miembro que consultar el valor de este `COleDateTime` de objetos, vea las funciones miembro siguientes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

##  <a name="getdayofyear"></a>  COleDateTime::GetDayOfYear

Obtiene el día del año representado por este valor de fecha y hora.

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>Valor devuelto

El día del año representado por el valor de esta `COleDateTime` objeto o `COleDateTime::error` si no se pudo obtener el día del año.

### <a name="remarks"></a>Comentarios

Retorno válido los valores pueden oscilar entre 1 y 366, donde el 1 de enero = 1.

Para obtener información sobre otras funciones miembro que consultar el valor de este `COleDateTime` de objetos, vea las funciones miembro siguientes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

##  <a name="gethour"></a>  COleDateTime::GetHour

Obtiene la hora representada por este valor de fecha y hora.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Valor devuelto

La hora representada por el valor de esta `COleDateTime` objeto o `COleDateTime::error` si no se pudo obtener la hora.

### <a name="remarks"></a>Comentarios

Intervalo de valores de retorno válido entre 0 y 23.

Para obtener información sobre otras funciones miembro que consultar el valor de este `COleDateTime` de objetos, vea las funciones miembro siguientes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

##  <a name="getminute"></a>  COleDateTime::GetMinute

Obtiene el minuto representado por este valor de fecha y hora.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Valor devuelto

El minuto representado por el valor de este `COleDateTime` objeto o `COleDateTime::error` si no se pudo obtener el minuto.

### <a name="remarks"></a>Comentarios

Intervalo de valores de retorno válido entre 0 y 59.

Para obtener información sobre otras funciones miembro que consultar el valor de este `COleDateTime` de objetos, vea las funciones miembro siguientes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHour](#gethour).

##  <a name="getmonth"></a>  COleDateTime::GetMonth

Obtiene el mes representado por este valor de fecha y hora.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Valor devuelto

Mes representado por el valor de esta `COleDateTime` objeto o `COleDateTime::error` si no se pudo obtener el mes.

### <a name="remarks"></a>Comentarios

Intervalo de valores de retorno válido entre 1 y 12.

Para obtener información sobre otras funciones miembro que consultar el valor de este `COleDateTime` de objetos, vea las funciones miembro siguientes:

- [GetDay](#getday)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetDay](#getday).

##  <a name="getsecond"></a>  COleDateTime::GetSecond

Obtiene a la segunda representada por este valor de fecha y hora.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Valor devuelto

El segundo representado por el valor de este `COleDateTime` objeto o `COleDateTime::error` si no se pudo obtener el segundo.

### <a name="remarks"></a>Comentarios

Intervalo de valores de retorno válido entre 0 y 59.

> [!NOTE]
>  La `COleDateTime` clase no admite segundos intercalares.

Para obtener más información acerca de la implementación para `COleDateTime`, consulte el artículo [fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

Para obtener información sobre otras funciones miembro que consultar el valor de este `COleDateTime` de objetos, vea las funciones miembro siguientes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetHour](#gethour).

##  <a name="getstatus"></a>  COleDateTime::GetStatus

Obtiene el estado (validez) de un determinado `COleDateTime` objeto.

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el estado de este `COleDateTime` valor. Si se llama a `GetStatus` en un `COleDateTime` construye el objeto con el valor predeterminado, el resultado será válido. Si se llama a `GetStatus` en un `COleDateTime` objeto inicializado con el conjunto de constructor en null, `GetStatus` devolverá null.

### <a name="remarks"></a>Comentarios

El valor devuelto se define mediante el `DateTimeStatus` tipo enumerado, que se define dentro de la `COleDateTime` clase.

```
enum DateTimeStatus
{
   error = -1,
   valid = 0,
   invalid = 1,    // Invalid date (out of range, etc.)
   null = 2,       // Literally has no value
};
```

Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:

- `COleDateTime::error` Indica que se produjo un error al intentar obtener la parte del valor de fecha y hora.

- `COleDateTime::valid` Indica que este `COleDateTime` objeto es válido.

- `COleDateTime::invalid` Indica que este `COleDateTime` objeto no es válido; es decir, su valor puede ser incorrecto.

- `COleDateTime::null` Indica que este `COleDateTime` objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de la base de datos de "no tener ningún valor," en lugar de NULL de C++).

El estado de un `COleDateTime` objeto no es válido en los casos siguientes:

- Si se establece su valor desde un `VARIANT` o `COleVariant` valor que no se pudo convertir en un valor de fecha y hora.

- Si se establece su valor desde un `time_t`, `SYSTEMTIME`, o `FILETIME` valor que no se pudo convertir en un valor de fecha y hora válido.

- Si su valor se establece `SetDateTime` con valores de parámetro no válido.

- Si este objeto ha sufrido un desbordamiento o subdesbordamiento durante una operación aritmética de asignación, es decir, `+=` o `-=`.

- Si se le asignó un valor no válido para este objeto.

- Si el estado de este objeto se estableció explícitamente en no válido con `SetStatus`.

Para obtener más información acerca de las operaciones que puede establecer el estado no válidos, consulte las funciones miembro siguientes:

- [COleDateTime](#coledatetime)

- [SetDateTime](#setdatetime)

- [operator +, -](#operator_add_-)

- [operator +=, -=](#operator_add_eq_-_eq)

Para obtener más información acerca de los límites de `COleDateTime` valores, consulte el artículo [fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

##  <a name="getyear"></a>  COleDateTime::GetYear

Obtiene el año representado por este valor de fecha y hora.

```
int GetYear() const throw();
```

### <a name="return-value"></a>Valor devuelto

El año representado por el valor de este `COleDateTime` objeto o `COleDateTime::error` si no se pudo obtener el año.

### <a name="remarks"></a>Comentarios

Los valores devueltos válidos oscilan entre 100 y 9999, que incluye el siglo.

Para obtener información sobre otras funciones miembro que consultar el valor de este `COleDateTime` de objetos, vea las funciones miembro siguientes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Para obtener más información acerca de los límites de `COleDateTime` valores, consulte el artículo [fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetDay](#getday).

##  <a name="m_dt"></a>  COleDateTime::m_dt

Subyacente `DATE` estructura para este `COleDateTime` objeto.

```
DATE m_dt;
```

### <a name="remarks"></a>Comentarios

> [!CAUTION]
>  Cambia el valor en el `DATE` objeto accediendo el puntero devuelto por esta función cambiará el valor de esta `COleDateTime` objeto. No cambia el estado de este `COleDateTime` objeto.

Para obtener más información sobre la implementación de la `DATE` de objetos, consulte el artículo [fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="m_status"></a>  COleDateTime::m_status

Contiene el estado de este `COleDateTime` objeto.

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>Comentarios

El tipo de este miembro de datos es el tipo enumerado `DateTimeStatus`, que se define dentro de la `COleDateTime` clase. Para obtener más información, consulte [COleDateTime::GetStatus](#getstatus).

> [!CAUTION]
>  Este miembro de datos es para situaciones de programación avanzadas. Debe usar las funciones de miembro insertada [GetStatus](#getstatus) y [SetStatus](#setstatus). Consulte `SetStatus` para las precauciones adicionales con respecto a este miembro de datos se establece explícitamente.

##  <a name="operator_eq"></a>  COleDateTime:: operador =

Copia un `COleDateTime` valor.

```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& uDate) throw();
```

### <a name="remarks"></a>Comentarios

Estos operadores de asignaciones sobrecargados copian el valor de fecha y hora de origen en este `COleDateTime` objeto. Una breve descripción de cada una de estas sobrecargado se indica a continuación los operadores de asignación:

- **operador = (** `dateSrc` **)** el valor y el estado del operando se copian en esta `COleDateTime` objeto.

- **operador = (** *varSrc* **)** si la conversión de la [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) valor (o [COleVariant](../../mfc/reference/colevariant-class.md) objeto) a una fecha y hora (VT_ FECHA) se realiza correctamente, el valor convertido se copia en esto `COleDateTime` objeto y su estado se establece en válido. Si la conversión no es correcta, el valor de este objeto se establece en cero (30 de diciembre de 1899, medianoche) y su estado a no válido.

- **operador = (** `dtSrc` **)** el `DATE` valor se copia en esto `COleDateTime` objeto y su estado se establece en válido.

- **operador = (** `timeSrc` **)** el `time_t` o `__time64_t` se convierte y se copian en este valor `COleDateTime` objeto. Si la conversión se realiza correctamente, el estado de este objeto se establece en válido; Si no lo consigue, se establece en no válido.

- **operador = (** *systimeSrc* **)** el [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) se convierte y se copian en este valor `COleDateTime` objeto. Si la conversión se realiza correctamente, el estado de este objeto se establece en válido; Si no lo consigue, se establece en no válido.

- **operador = (** `uDate` **)** el `UDATE` se convierte y se copian en este valor `COleDateTime` objeto. Si la conversión se realiza correctamente, el estado de este objeto se establece en válido; Si no lo consigue, se establece en no válido. Un `UDATE` estructura representa una fecha de "desempaquetada". Para obtener más información, vea la función [VarDateFromUdate](/windows/desktop/api/oleauto/nf-oleauto-vardatefromudate).

- **operador = (** `filetimeSrc` **)** el [FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) se convierte y se copian en este valor `COleDateTime` objeto. Si la conversión se realiza correctamente, el estado de este objeto se establece en válido; Si se establece en no válido. `FILETIME` usa la hora Universal coordinada (UTC), por lo que si se pasa una hora UTC en la estructura, los resultados se convertirá de hora UTC a la hora local y se almacenará como hora de tipo variant. Este comportamiento es igual que en Visual C++ 6.0 y Visual C++ .NET 2003 SP2. Para obtener más información, consulte [tiempos archivos](/windows/desktop/SysInfo/file-times) en el SDK de Windows.

Para obtener más información, consulte el [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) entrada en el SDK de Windows.

Para obtener más información sobre la `time_t` tipo de datos, vea el [tiempo](../../c-runtime-library/reference/time-time32-time64.md) funcionando en el *referencia de la biblioteca de tiempo de ejecución*.

Para obtener más información, consulte el [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) y [FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) estructuras en el SDK de Windows.

Para obtener más información acerca de los límites de `COleDateTime` valores, consulte el artículo [fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="operator_add_-"></a>  COleDateTime:: operador +, -

Sumar y restar `ColeDateTime` valores.

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>Comentarios

`COleDateTime` objetos representan los momentos en absolutos. [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md) representan horas relativas. Los dos primeros operadores permiten sumar y restar un `COleDateTimeSpan` valor desde un `COleDateTime` valor. El tercer operador permite que se va a restar uno `COleDateTime` valor de otra para producir un `COleDateTimeSpan` valor.

Si cualquiera de los operandos es null, el estado del resultante `COleDateTime` valor es null.

Si el resultado `COleDateTime` valor está fuera de los límites de los valores aceptables, el estado de la `COleDateTime` valor no es válido.

Si cualquiera de los operandos no es válido y el otro no es null, el estado del resultante `COleDateTime` valor no es válido.

El **+** y **-** operadores se producirá una aserción si el `COleDateTime` objeto está establecido en null. Consulte [operadores relacionales COleDateTime](#coledatetime_relational_operators) para obtener un ejemplo.

Para obtener más información sobre los valores de estado válido, null y no válidos, vea el [m_status](#m_status) variable miembro.

Para obtener más información acerca de los límites de `COleDateTime` valores, consulte el artículo [fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  COleDateTime:: operador +=, =

Sumar y restar un `ColeDateTime` valor de este `COleDateTime` objeto.

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Comentarios

Estos operadores permiten sumar y restar un `COleDateTimeSpan` valor hacia y desde este `COleDateTime`. Si cualquiera de los operandos es null, el estado del resultante `COleDateTime` valor es null.

Si resultante `COleDateTime` valor está fuera de los límites de los valores aceptables, el estado de este `COleDateTime` valor se establece en no válido.

Si cualquiera de los operandos no es válido y otro no es null, el estado del resultante `COleDateTime` valor no es válido.

Para obtener más información sobre los valores de estado válido, null y no válidos, vea el [m_status](#m_status) variable miembro.

El **+=** y **-=** operadores se producirá una aserción si el `COleDateTime` objeto está establecido en null. Consulte [operadores relacionales COleDateTime](#coledatetime_relational_operators) para obtener un ejemplo.

Para obtener más información acerca de los límites de `COleDateTime` valores, consulte el artículo [fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="operator_date"></a>  COleDateTime::operator DATE

Convierte un `ColeDateTime` valor en un `DATE`.

```
operator DATE() const throw();
```

### <a name="remarks"></a>Comentarios

Este operador devuelve un `DATE` objeto cuyo valor se copia desde este `COleDateTime` objeto. Para obtener más información sobre la implementación de la `DATE` de objetos, consulte el artículo [fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

El `DATE` operador se producirá una aserción si el `COleDateTime` objeto está establecido en null. Consulte [operadores relacionales COleDateTime](#coledatetime_relational_operators) para obtener un ejemplo.

##  <a name="parsedatetime"></a>  COleDateTime::ParseDateTime

Analiza una cadena para leer un valor de fecha y hora.

```
bool ParseDateTime(
    LPCTSTR lpszDate,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>Parámetros

*lpszDate*<br/>
Un puntero a la cadena terminada en null que se analizará. Para conocer más detalles, vea la sección Comentarios.

*dwFlags*<br/>
Indica los marcadores para la configuración regional y el análisis. Uno o varios de los siguientes indicadores:

- LOCALE_NOUSEROVERRIDE usar la configuración regional predeterminada del sistema, en lugar de configuración de usuario personalizada.

- VAR_TIMEVALUEONLY omitir la parte de fecha durante el análisis.

- VAR_DATEVALUEONLY ignorar el espacio de tiempo durante el análisis.

*lcid*<br/>
Indica el identificador de configuración regional que se usará para la conversión.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la cadena se convirtió correctamente en un valor de fecha y hora, en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Si la cadena se convirtió correctamente en una fecha y hora valor, el valor de esta `COleDateTime` objeto se establece en ese valor y su estado a válido.

> [!NOTE]
>  Valores de año deben estar comprendida entre 100 y 9999, ambos inclusive.

El *lpszDate* parámetro puede tomar una variedad de formatos. Por ejemplo, las cadenas siguientes contienen formatos de fecha y hora aceptable:

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

El identificador de configuración regional también afectará si el formato de cadena es aceptable para la conversión a un valor de fecha y hora.

En el caso de VAR_DATEVALUEONLY, el valor de hora se establece en 0 o medianoche de tiempo. En el caso de VAR_TIMEVALUEONLY, se establece el valor de fecha en fecha 0, lo que significa que el 30 de diciembre de 1899.

Si no se pudo convertir la cadena en un valor de fecha y hora, o si se ha producido un desbordamiento numérico, el estado de este `COleDateTime` objeto no es válido.

Para obtener más información acerca de los límites y la implementación para `COleDateTime` valores, consulte el artículo [fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="setdate"></a>  COleDateTime::SetDate

Establece la fecha de este `COleDateTime` objeto.

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>Parámetros

*nYear*, *nMonth*, *nDay*<br/>
Indican los componentes de fecha que se copiará en esto `COleDateTime` objeto.

### <a name="return-value"></a>Valor devuelto

Cero si el valor de esta `COleDateTime` objeto se estableció correctamente; en caso contrario, 1. Este valor devuelto se basa en el `DateTimeStatus` tipo enumerado. Para obtener más información, consulte el [SetStatus](#setstatus) función miembro.

### <a name="remarks"></a>Comentarios

La fecha se establece en los valores especificados. La hora se establece en 0, hora de medianoche.

Consulte la tabla siguiente para los límites de los valores de parámetro:

|Parámetro|Límites|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*nDay*|0 - 31|

Si desborda el día del mes, se convierte en el día correcto del mes siguiente y mes o año se incrementa en consecuencia. Un valor de día cero indica el último día del mes anterior. El comportamiento es el mismo que `SystemTimeToVariantTime`.

Si el valor de fecha especificado por los parámetros no es válido, el estado de este objeto se establece en `COleDateTime::invalid`. Debe usar [GetStatus](#getstatus) para comprobar la validez de la `DATE` de valor y no debe suponer que el valor de [m_dt](#m_dt) permanecerán sin modificar.

Estos son algunos ejemplos de valores de fecha:

|*nYear*|*nMonth*|*nDay*|Valor|
|-------------|--------------|------------|-----------|
|2000|2|29|29 de febrero de 2000|
|1776|7|4|4 de julio de 1776|
|1925|4|35|35 abril de 1925 (fecha no válida)|
|10000|1|1|1 de enero 10000 (fecha no válida)|

Para establecer la fecha y hora, vea [COleDateTime::SetDateTime](#setdatetime).

Para obtener información sobre las funciones miembro que consultar el valor de este `COleDateTime` de objetos, vea las funciones miembro siguientes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Para obtener más información acerca de los límites de `COleDateTime` valores, consulte el artículo [fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

##  <a name="setdatetime"></a>  COleDateTime::SetDateTime

Establece la fecha y hora de esta `COleDateTime` objeto.

```
int SetDateTime(
    int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Parámetros

*nYear*, *nMonth*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
Indican los componentes de fecha y hora en que se copiará en esto `COleDateTime` objeto.

### <a name="return-value"></a>Valor devuelto

Cero si el valor de esta `COleDateTime` objeto se estableció correctamente; en caso contrario, 1. Este valor devuelto se basa en el `DateTimeStatus` tipo enumerado. Para obtener más información, consulte el [SetStatus](#setstatus) función miembro.

### <a name="remarks"></a>Comentarios

Consulte la tabla siguiente para los límites de los valores de parámetro:

|Parámetro|Límites|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*nDay*|0 - 31|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Si desborda el día del mes, se convierte en el día correcto del mes siguiente y mes o año se incrementa en consecuencia. Un valor de día cero indica el último día del mes anterior. El comportamiento es igual a [SystemTimeToVariantTime](/windows/desktop/api/oleauto/nf-oleauto-systemtimetovarianttime).

Si el valor de fecha u hora especificado por los parámetros no es válido, que el estado de este objeto se establece en válida y el valor de este objeto no se puede cambiar.

Estos son algunos ejemplos de valores de hora:

|*nHour*|*nMin*|*nSec*|Valor|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|No válido|
|9|60|0|No válido|

Estos son algunos ejemplos de valores de fecha:

|*nYear*|*nMonth*|*nDay*|Valor|
|-------------|--------------|------------|-----------|
|1995|4|15|15 de abril de 1995|
|1789|7|14|17 de julio de 1789|
|1925|2|30|No válido|
|10000|1|1|No válido|

Para establecer solo la fecha, consulte [COleDateTime::SetDate](#setdate). Para establecer solo la hora, vea [COleDateTime::SetTime](#settime).

Para obtener información sobre las funciones miembro que consultar el valor de este `COleDateTime` de objetos, vea las funciones miembro siguientes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Para obtener más información acerca de los límites de `COleDateTime` valores, consulte el artículo [fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetStatus](#getstatus).

##  <a name="setstatus"></a>  COleDateTime::SetStatus

Establece el estado de este `COleDateTime` objeto.

```
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>Parámetros

*status*<br/>
El nuevo valor de estado para esta `COleDateTime` objeto.

### <a name="remarks"></a>Comentarios

El *estado* el valor del parámetro se define mediante el `DateTimeStatus` tipo enumerado, que se define dentro de la `COleDateTime` clase. Consulte [COleDateTime::GetStatus](#getstatus) para obtener más información.

> [!CAUTION]
>  Esta función es para situaciones de programación avanzadas. Esta función no modifica los datos de este objeto. Más a menudo se usará para establecer el estado en **null** o **válido**. El operador de asignación ([operador =](#operator_eq)) y [SetDateTime](#setdatetime) establecer el estado del objeto basado en los valores de origen.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetStatus](#getstatus).

##  <a name="settime"></a>  COleDateTime::SetTime

Establece la hora de esta `COleDateTime` objeto.

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Parámetros

*nHour*, *nMin*, *nSec*<br/>
Indican los componentes de tiempo que se copiará en esto `COleDateTime` objeto.

### <a name="return-value"></a>Valor devuelto

Cero si el valor de esta `COleDateTime` objeto se estableció correctamente; en caso contrario, 1. Este valor devuelto se basa en el `DateTimeStatus` tipo enumerado. Para obtener más información, consulte el [SetStatus](#setstatus) función miembro.

### <a name="remarks"></a>Comentarios

La hora se establece en los valores especificados. La fecha se establece en fecha 0, lo que significa que el 30 de diciembre de 1899.

Consulte la tabla siguiente para los límites de los valores de parámetro:

|Parámetro|Límites|
|---------------|------------|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Si el tiempo especificado por los parámetros de valor no es válido, el estado de este objeto se establece en válida y el valor de este objeto no se modifica.

Estos son algunos ejemplos de valores de hora:

|*nHour*|*nMin*|*nSec*|Valor|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|No válido|
|9|60|0|No válido|

Para establecer la fecha y hora, vea [COleDateTime::SetDateTime](#setdatetime).

Para obtener información sobre las funciones miembro que consultar el valor de este `COleDateTime` de objetos, vea las funciones miembro siguientes:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Para obtener más información acerca de los límites de `COleDateTime` valores, consulte el artículo [fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [SetDate](#setdate).

## <a name="see-also"></a>Vea también

[COleVariant (clase)](../../mfc/reference/colevariant-class.md)<br/>
[CTime (clase)](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan (clase)](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas ATL y MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
