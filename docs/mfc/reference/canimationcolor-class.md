---
title: Clase CAnimationColor
ms.date: 11/04/2016
f1_keywords:
- CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationColor::GetB
- AFXANIMATIONCONTROLLER/CAnimationColor::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetG
- AFXANIMATIONCONTROLLER/CAnimationColor::GetR
- AFXANIMATIONCONTROLLER/CAnimationColor::GetValue
- AFXANIMATIONCONTROLLER/CAnimationColor::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationColor::m_bValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_gValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_rValue
helpviewer_keywords:
- CAnimationColor [MFC], CAnimationColor
- CAnimationColor [MFC], AddTransition
- CAnimationColor [MFC], GetB
- CAnimationColor [MFC], GetDefaultValue
- CAnimationColor [MFC], GetG
- CAnimationColor [MFC], GetR
- CAnimationColor [MFC], GetValue
- CAnimationColor [MFC], SetDefaultValue
- CAnimationColor [MFC], GetAnimationVariableList
- CAnimationColor [MFC], m_bValue
- CAnimationColor [MFC], m_gValue
- CAnimationColor [MFC], m_rValue
ms.assetid: 88bfabd4-efeb-4652-87e8-304253d8e48c
ms.openlocfilehash: ee6003a22db78c2a510579c3d717fec887f8a6ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151180"
---
# <a name="canimationcolor-class"></a>Clase CAnimationColor

Implementa la funcionalidad de un color cuyos componentes rojo, verde y azul se pueden animar.

## <a name="syntax"></a>Sintaxis

```
class CAnimationColor : public CAnimationBaseObject;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationColor::CAnimationColor](#canimationcolor)|Sobrecargado. Construye un objeto de color de la animación.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationColor::AddTransition](#addtransition)|Agrega las transiciones para los componentes rojo, verde y azul.|
|[CAnimationColor::GetB](#getb)|Proporciona acceso a CAnimationVariable que representa el componente azul.|
|[CAnimationColor::GetDefaultValue](#getdefaultvalue)|Devuelve los valores predeterminados para los componentes de color.|
|[CAnimationColor::GetG](#getg)|Proporciona acceso a CAnimationVariable que representa el componente verde.|
|[CAnimationColor::GetR](#getr)|Proporciona acceso a CAnimationVariable que representa el componente rojo.|
|[CAnimationColor::GetValue](#getvalue)|Devuelve el valor actual.|
|[CAnimationColor::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CAnimationColor::GetAnimationVariableList](#getanimationvariablelist)|Coloca las variables de animación encapsulado en una lista. (Invalida [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationColor::operator COLORREF](#operator_colorref)||
|[CAnimationColor::operator=](#operator_eq)|Asigna el color a CAnimationColor.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Name|Descripción|
|----------|-----------------|
|[CAnimationColor::m_bValue](#m_bvalue)|La variable de animación encapsulado que representa el componente azul del color de la animación.|
|[CAnimationColor::m_gValue](#m_gvalue)|La variable de animación encapsulado que representa el componente verde del color de la animación.|
|[CAnimationColor::m_rValue](#m_rvalue)|La variable de animación encapsulado que representa el componente rojo del color de la animación.|

## <a name="remarks"></a>Comentarios

La clase CAnimationColor encapsula los tres objetos CAnimationVariable y puede representar en aplicaciones de un color. Por ejemplo, puede usar esta clase se va a animar los colores de cualquier objeto en la pantalla (como el color del texto, el color de fondo etcetera). Para usar esta clase en la aplicación, simplemente cree una instancia de un objeto de esta clase, agréguelo al controlador de animación mediante CAnimationController::AddAnimationObject y llamar a AddTransition para cada transición que se aplicará a los componentes rojo, verde y azul.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationColor`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationColor::AddTransition

Agrega las transiciones para los componentes rojo, verde y azul.

```
void AddTransition(
    CBaseTransition* pRTransition,
    CBaseTransition* pGTransition,
    CBaseTransition* pBTransition);
```

### <a name="parameters"></a>Parámetros

*pRTransition*<br/>
Transición del componente rojo.

*pGTransition*<br/>
Transición del componente verde.

*pBTransition*<br/>
Transición del componente azul.

### <a name="remarks"></a>Comentarios

Llame a esta función para agregar las transiciones especificadas a la lista interna de las transiciones que se aplicará a las variables de animación que representan los componentes de color. Al agregar transiciones, no se aplican inmediatamente y almacenan en una lista interna. Las transiciones se aplican (agregado a un guión gráfico para un determinado valor) cuando se llama a CAnimationController::AnimateGroup. Si no tiene que aplicar una transición a uno de los componentes de color, puede pasar NULL.

##  <a name="canimationcolor"></a>  CAnimationColor::CAnimationColor

Construye un objeto CAnimationColor.

```
CAnimationColor();

CAnimationColor(
    COLORREF color,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
Especifica el color predeterminado.

*nGroupID*<br/>
Especifica el identificador de grupo.

*nObjectID*<br/>
Especifica el identificador de objeto.

*dwUserData*<br/>
Especifica los datos definidos por el usuario.

### <a name="remarks"></a>Comentarios

Se construye el objeto con valores predeterminados para rojo, verde, azul, Id. de objeto y el identificador de grupo, que se establecerá en 0. Puede cambiar posteriormente en tiempo de ejecución mediante SetDefaultValue y SetID.

##  <a name="getanimationvariablelist"></a>  CAnimationColor::GetAnimationVariableList

Coloca las variables de animación encapsulado en una lista.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parámetros

*lst*<br/>
Cuando la función devuelve, contiene punteros a tres objetos CAnimationVariable que representan los componentes rojos, verde y azules.

##  <a name="getb"></a>  CAnimationColor::GetB

Proporciona acceso a CAnimationVariable que representa el componente azul.

```
CAnimationVariable& GetB();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a CAnimationVariable encapsulado que representa el componente azul.

### <a name="remarks"></a>Comentarios

Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa el componente azul.

##  <a name="getdefaultvalue"></a>  CAnimationColor::GetDefaultValue

Devuelve los valores predeterminados para los componentes de color.

```
COLORREF GetDefaultValue();
```

### <a name="return-value"></a>Valor devuelto

Un valor COLORREF que contiene los valores predeterminados para los componentes RGB.

### <a name="remarks"></a>Comentarios

Llame a esta función para recuperar el valor predeterminado, que anteriormente se ha establecido mediante el constructor o SetDefaultValue.

##  <a name="getg"></a>  CAnimationColor::GetG

Proporciona acceso a CAnimationVariable que representa el componente verde.

```
CAnimationVariable& GetG();
```

### <a name="return-value"></a>Valor devuelto

Una referencia al componente verde que representa CAnimationVariable encapsulado.

### <a name="remarks"></a>Comentarios

Puede llamar a este método para obtener acceso directo al componente verde que representa CAnimationVariable subyacente.

##  <a name="getr"></a>  CAnimationColor::GetR

Proporciona acceso a CAnimationVariable que representa el componente rojo.

```
CAnimationVariable& GetR();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a CAnimationVariable encapsulado que representa el componente rojo.

### <a name="remarks"></a>Comentarios

Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa el componente rojo.

##  <a name="getvalue"></a>  CAnimationColor::GetValue

Devuelve el valor actual.

```
BOOL GetValue(COLORREF& color);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
Salida. Cuando este método vuelve, contiene el valor actual.

### <a name="return-value"></a>Valor devuelto

Es TRUE si el valor actual se ha recuperado correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Llame a esta función para recuperar el valor actual del color de la animación. Si este método produce un error o no se han inicializado los objetos COM subyacentes para los componentes de color, color contiene el valor predeterminado, que anteriormente se estableció en el constructor o por SetDefaultValue.

##  <a name="m_bvalue"></a>  CAnimationColor::m_bValue

La variable de animación encapsulado que representa el componente azul del color de la animación.

```
CAnimationVariable m_bValue;
```

##  <a name="m_gvalue"></a>  CAnimationColor::m_gValue

La variable de animación encapsulado que representa el componente verde del color de la animación.

```
CAnimationVariable m_gValue;
```

##  <a name="m_rvalue"></a>  CAnimationColor::m_rValue

La variable de animación encapsulado que representa el componente rojo del color de la animación.

```
CAnimationVariable m_rValue;
```

##  <a name="operator_colorref"></a>  CAnimationColor::operator COLORREF

```
operator COLORREF();
```

### <a name="return-value"></a>Valor devuelto

##  <a name="operator_eq"></a>  CAnimationColor::operator=

Asigna el color a CAnimationColor.

```
void operator=(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
Especifica el nuevo valor de Color de la animación.

### <a name="remarks"></a>Comentarios

Se recomienda hacerlo antes del inicio de la animación, dado que este operador llama a SetDefaultValue, que vuelve a crear los objetos COM subyacentes para los componentes de color si se han creado. Si se ha suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), deberá volver a habilitar estos eventos.

##  <a name="setdefaultvalue"></a>  CAnimationColor::SetDefaultValue

Establece el valor predeterminado.

```
void SetDefaultValue(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
Especifica los nuevos valores predeterminados para los componentes rojos, verde y azules.

### <a name="remarks"></a>Comentarios

Utilice esta función para establecer un valor predeterminado para el objeto de animación. Este método asigna los valores predeterminados para los componentes de color del color de la animación. También se vuelve a crear objetos COM subyacentes si se han creado. Si se ha suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), deberá volver a habilitar estos eventos.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
