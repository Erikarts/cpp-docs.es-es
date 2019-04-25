---
title: Clase CDiscreteTransition
ms.date: 11/04/2016
f1_keywords:
- CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::Create
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_delay
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_hold
helpviewer_keywords:
- CDiscreteTransition [MFC], CDiscreteTransition
- CDiscreteTransition [MFC], Create
- CDiscreteTransition [MFC], m_dblFinalValue
- CDiscreteTransition [MFC], m_delay
- CDiscreteTransition [MFC], m_hold
ms.assetid: b4d84fb3-ccaa-451c-a69b-6b50dcb9b9c8
ms.openlocfilehash: dc2311f7dae71f7c3848b7825b297ec5c9747859
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62168016"
---
# <a name="cdiscretetransition-class"></a>Clase CDiscreteTransition

Encapsula una transición discreta.

## <a name="syntax"></a>Sintaxis

```
class CDiscreteTransition : public CBaseTransition;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CDiscreteTransition::CDiscreteTransition](#cdiscretetransition)|Construye un objeto de transición discreta e inicializa sus parámetros.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDiscreteTransition::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado. (Invalida [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CDiscreteTransition::m_dblFinalValue](#m_dblfinalvalue)|El valor de la variable de animación al final de la transición.|
|[CDiscreteTransition::m_delay](#m_delay)|La cantidad de tiempo por el que se va a retrasar el cambio de instantáneo para el valor final.|
|[CDiscreteTransition::m_hold](#m_hold)|La cantidad de tiempo por el que se va a contener la variable en su valor final.|

## <a name="remarks"></a>Comentarios

Durante una transición discreta, la variable de animación permanece en el valor inicial para un tiempo de retraso especificado y, a continuación, cambia al instante a un valor final especificado y permanece en ese valor para un tiempo de espera especificado. Dado que todas las transiciones se borran automáticamente, se recomienda asignada a ellos mediante el operador nuevo. El objeto COM IUIAnimationTransition encapsulado se crea por CAnimationController::AnimateGroup, hasta que es NULL. Cambiar las variables de miembro después de la creación de este objeto COM no tiene ningún efecto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CDiscreteTransition](../../mfc/reference/cdiscretetransition-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="cdiscretetransition"></a>  CDiscreteTransition::CDiscreteTransition

Construye un objeto de transición discreta e inicializa sus parámetros.

```
CDiscreteTransition(
    UI_ANIMATION_SECONDS delay,
    DOUBLE dblFinalValue,
    UI_ANIMATION_SECONDS hold);
```

### <a name="parameters"></a>Parámetros

*delay*<br/>
La cantidad de tiempo por el que se va a retrasar el cambio de instantáneo para el valor final.

*dblFinalValue*<br/>
El valor de la variable de animación al final de la transición.

*hold*<br/>
La cantidad de tiempo por el que se va a contener la variable en su valor final.

##  <a name="create"></a>  CDiscreteTransition::Create

Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

*pLibrary*<br/>
Un puntero a un [IUIAnimationTransitionLibrary interfaz](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), que define una biblioteca de transiciones estándares.

### <a name="return-value"></a>Valor devuelto

TRUE si la transición se crea correctamente; en caso contrario, FALSE.

##  <a name="m_dblfinalvalue"></a>  CDiscreteTransition::m_dblFinalValue

El valor de la variable de animación al final de la transición.

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_delay"></a>  CDiscreteTransition::m_delay

La cantidad de tiempo por el que se va a retrasar el cambio de instantáneo para el valor final.

```
UI_ANIMATION_SECONDS m_delay;
```

##  <a name="m_hold"></a>  CDiscreteTransition::m_hold

La cantidad de tiempo por el que se va a contener la variable en su valor final.

```
UI_ANIMATION_SECONDS m_hold;
```

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
