---
title: Clase CAnimationVariableChangeHandler
ms.date: 11/04/2016
f1_keywords:
- CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::OnValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::SetAnimationController
helpviewer_keywords:
- CAnimationVariableChangeHandler [MFC], OnValueChanged
- CAnimationVariableChangeHandler [MFC], SetAnimationController
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
ms.openlocfilehash: 589691f8bb2bc14eba46245082ff972ca6b97fcc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604408"
---
# <a name="canimationvariablechangehandler-class"></a>Clase CAnimationVariableChangeHandler

Implementa una devolución de llamada, a la que llama la API de animación cuando cambia el valor de una animación.

## <a name="syntax"></a>Sintaxis

```
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|Construye un objeto `CAnimationVariableChangeHandler`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CreateInstance`|Crea una instancia de `CAnimationVariableChangeHandler` objeto.|
|[CAnimationVariableChangeHandler::OnValueChanged](#onvaluechanged)|Se llama cuando ha cambiado un valor de una variable de animación. (Invalida `CUIAnimationVariableChangeHandlerBase::OnValueChanged`).|
|[CAnimationVariableChangeHandler::SetAnimationController](#setanimationcontroller)|Almacena un puntero al controlador de animación para el enrutamiento de eventos.|

## <a name="remarks"></a>Comentarios

Se crea y se pasa a este controlador de eventos `IUIAnimationVariable::SetVariableChangeHandler` método, cuando se llama a `CAnimationVariable::EnableValueChangedEvent` o `CAnimationBaseObject::EnableValueChangedEvent` (lo que permite este evento para todas las variables de animación encapsulado en un objeto de animación).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CUIAnimationCallbackBase`

`CUIAnimationVariableChangeHandlerBase`

`CAnimationVariableChangeHandler`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="onvaluechanged"></a>  CAnimationVariableChangeHandler::OnValueChanged

Se llama cuando ha cambiado un valor de una variable de animación.

```
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```

### <a name="parameters"></a>Parámetros

*guión gráfico*<br/>
El guión gráfico que se anima la variable.

*Variable*<br/>
La variable de animación que se ha actualizado.

*newValue*<br/>
Nuevo valor.

*valores anteriores previousValue*<br/>
El valor anterior.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. En caso contrario, devuelve un código de error HRESULT.

##  <a name="setanimationcontroller"></a>  CAnimationVariableChangeHandler::SetAnimationController

Almacena un puntero al controlador de animación para el enrutamiento de eventos.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parámetros

*pAnimationController*<br/>
Un puntero al controlador de animación, que se va a recibir eventos.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
