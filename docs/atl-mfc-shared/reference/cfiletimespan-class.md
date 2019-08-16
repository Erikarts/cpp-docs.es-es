---
title: Clase CFileTimeSpan
ms.date: 10/18/2018
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
ms.openlocfilehash: f9bb42ba4c142f671a83dcfa7e99cff940fff047
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491291"
---
# <a name="cfiletimespan-class"></a>Clase CFileTimeSpan

Esta clase proporciona métodos para administrar valores de fecha y hora relativos asociados a un archivo.

## <a name="syntax"></a>Sintaxis

```
class CFileTimeSpan
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|Llame a este método para recuperar el intervalo de tiempo `CFileTimeSpan` del objeto.|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Llame a este método para establecer el intervalo de tiempo `CFileTimeSpan` del objeto.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFileTimeSpan::operator -](#operator_-)|Realiza la resta en un `CFileTimeSpan` objeto.|
|[CFileTimeSpan::operator !=](#operator_neq)|Compara dos objetos `CFileTimeSpan` para determinar si no son iguales.|
|[CFileTimeSpan::operator +](#operator_add)|Realiza sumas en `CFileTimeSpan` un objeto.|
|[CFileTimeSpan::operator +=](#operator_add_eq)|Realiza sumas en `CFileTimeSpan` un objeto y asigna el resultado al objeto actual.|
|[CFileTimeSpan:: Operator&lt;](#operator_lt)|Compara dos `CFileTimeSpan` objetos para determinar el menor.|
|[CFileTimeSpan:: Operator&lt;=](#operator_lt_eq)|Compara dos `CFileTimeSpan` objetos para determinar la igualdad o el menor.|
|[CFileTimeSpan::operator =](#operator_eq)|Operador de asignación.|
|[CFileTimeSpan::operator -=](#operator_-_eq)|Realiza una resta en un `CFileTimeSpan` objeto y asigna el resultado al objeto actual.|
|[CFileTimeSpan::operator ==](#operator_eq_eq)|Compara dos objetos `CFileTimeSpan` para determinar si son iguales.|
|[CFileTimeSpan:: Operator&gt;](#operator_gt)|Compara dos `CFileTimeSpan` objetos para determinar el mayor.|
|[CFileTimeSpan:: Operator&gt;=](#operator_gt_eq)|Compara dos `CFileTimeSpan` objetos para determinar la igualdad o el mayor.|

## <a name="remarks"></a>Comentarios

Esta clase proporciona métodos para administrar períodos de tiempo relativos que suelen producirse al realizar operaciones relacionadas con la creación, el último acceso o la última modificación de un archivo. Los métodos de esta clase se usan con frecuencia junto con los objetos de la [clase CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md) .

## <a name="example"></a>Ejemplo

Vea el ejemplo de [CFileTime:: millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).

## <a name="requirements"></a>Requisitos

**Encabezado:** atltime. h

##  <a name="cfiletimespan"></a>  CFileTimeSpan::CFileTimeSpan

El constructor.

```
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
Objeto `CFileTimeSpan` existente.

*nSpan*<br/>
Un período de tiempo en milisegundos.

### <a name="remarks"></a>Comentarios

El `CFileTimeSpan` objeto se puede crear con un objeto `CFileTimeSpan` existente o expresarse como un valor de 64 bits. El constructor predeterminado establece el intervalo de tiempo en 0.

##  <a name="gettimespan"></a>  CFileTimeSpan::GetTimeSpan

Llame a este método para recuperar el intervalo de tiempo `CFileTimeSpan` del objeto.

```
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el intervalo de tiempo en milisegundos.

##  <a name="operator_-"></a>  CFileTimeSpan::operator -

Realiza la resta en un `CFileTimeSpan` objeto.

```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
Objeto `CFileTimeSpan`.

### <a name="return-value"></a>Valor devuelto

Devuelve un `CFileTimeSpan` objeto que representa el resultado de la diferencia entre dos intervalos de tiempo.

##  <a name="operator_neq"></a>  CFileTimeSpan::operator !=

Compara dos objetos `CFileTimeSpan` para determinar si no son iguales.

```
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el elemento que se va a comparar no es `CFileTimeSpan` igual al objeto; de lo contrario, es false.

##  <a name="operator_add"></a>  CFileTimeSpan::operator +

Realiza sumas en `CFileTimeSpan` un objeto.

```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
Objeto `CFileTimeSpan`.

### <a name="return-value"></a>Valor devuelto

Devuelve un `CFileTimeSpan` objeto que contiene la suma de los dos intervalos de tiempo.

##  <a name="operator_add_eq"></a>  CFileTimeSpan::operator +=

Realiza sumas en `CFileTimeSpan` un objeto y asigna el resultado al objeto actual.

```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
Objeto `CFileTimeSpan`.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CFileTimeSpan` actualizado que contiene la suma de los dos intervalos de tiempo.

##  <a name="operator_lt"></a>  CFileTimeSpan::operator &lt;

Compara dos `CFileTimeSpan` objetos para determinar el menor.

```
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es menor (es decir, representa un período de tiempo más corto) que el segundo; de lo contrario, es FALSE.

##  <a name="operator_lt_eq"></a>  CFileTimeSpan::operator &lt;=

Compara dos `CFileTimeSpan` objetos para determinar la igualdad o el menor.

```
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es menor que (es decir, representa un período de tiempo más corto) o igual que el segundo; de lo contrario, es FALSE.

##  <a name="operator_eq"></a>  CFileTimeSpan::operator =

Operador de asignación.

```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
Objeto `CFileTimeSpan`.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CFileTimeSpan` actualizado.

##  <a name="operator_-_eq"></a>  CFileTimeSpan::operator -=

Realiza una resta en un `CFileTimeSpan` objeto y asigna el resultado al objeto actual.

```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
Objeto `CFileTimeSpan`.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CFileTimeSpan` actualizado.

##  <a name="operator_eq_eq"></a>  CFileTimeSpan::operator ==

Compara dos objetos `CFileTimeSpan` para determinar si son iguales.

```
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si los objetos son iguales; de lo contrario, es FALSE.

##  <a name="operator_gt"></a>  CFileTimeSpan::operator &gt;

Compara dos `CFileTimeSpan` objetos para determinar el mayor.

```
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es mayor que (es decir, representa un período de tiempo más largo) que el segundo; de lo contrario, es FALSE.

##  <a name="operator_gt_eq"></a>  CFileTimeSpan::operator &gt;=

Compara dos `CFileTimeSpan` objetos para determinar la igualdad o el mayor.

```
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parámetros

*extienda*<br/>
Objeto `CFileTimeSpan` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es mayor que (es decir, representa un período de tiempo más largo) o igual que el segundo; de lo contrario, es FALSE.

##  <a name="settimespan"></a>  CFileTimeSpan::SetTimeSpan

Llame a este método para establecer el intervalo de tiempo `CFileTimeSpan` del objeto.

```
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parámetros

*nSpan*<br/>
Nuevo valor para el intervalo de tiempo en milisegundos.

## <a name="see-also"></a>Vea también

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTime (clase)](../../atl-mfc-shared/reference/cfiletime-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas de ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
