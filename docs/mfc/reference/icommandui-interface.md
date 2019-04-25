---
title: ICommandUI (interfaz)
ms.date: 11/04/2016
f1_keywords:
- ICommandUI
- AFXWINFORMS/ICommandUI
- AFXWINFORMS/icommandui__Check
- AFXWINFORMS/ICommandUI::ContinueRouting
- AFXWINFORMS/ICommandUI::Enabled
- AFXWINFORMS/ICommandUI::ID
- AFXWINFORMS/ICommandUI::Index
- AFXWINFORMS/ICommandUI::Radio
- AFXWINFORMS/ICommandUI::Text
helpviewer_keywords:
- ICommandUI interface [MFC]
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
ms.openlocfilehash: 31157ba2445a432af274650011b839fb3df9b3c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322061"
---
# <a name="icommandui-interface"></a>ICommandUI (interfaz)

Administra los comandos de la interfaz de usuario.

## <a name="syntax"></a>Sintaxis

```
interface class ICommandUI
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[icommandui__Check](#check)|Establece el elemento de interfaz de usuario para este comando en el estado de comprobación adecuada.|
|[ICommandUI::ContinueRouting](#continuerouting)|Indica al mecanismo de enrutamiento de comandos para enrutar el mensaje actual de la cadena de controladores de continuar.|
|[ICommandUI::Enabled](#enabled)|Habilita o deshabilita el elemento de interfaz de usuario para este comando.|
|[ICommandUI::ID](#id)|Obtiene el identificador del objeto de interfaz de usuario representado por la `ICommandUI` objeto.|
|[ICommandUI::Index](#index)|Obtiene el índice del objeto de interfaz de usuario representado por la `ICommandUI` objeto.|
|[ICommandUI::Radio](#radio)|Establece el elemento de interfaz de usuario para este comando en el estado de comprobación adecuada.|
|[ICommandUI::Text](#text)|Establece el texto del elemento de interfaz de usuario para este comando.|

## <a name="remarks"></a>Comentarios

Esta interfaz proporciona métodos y propiedades que administran los comandos de la interfaz de usuario. `ICommandUI` es similar a [CCmdUI (clase)](../../mfc/reference/ccmdui-class.md), salvo que `ICommandUI` se utiliza para aplicaciones MFC que interoperan con los componentes. NET.

`ICommandUI` se utiliza dentro de un controlador ON_UPDATE_COMMAND_UI en un [ICommandTarget](../../mfc/reference/icommandtarget-interface.md)-clase derivada. Cuando un usuario de una aplicación activa (activa o clics) se muestra un menú, cada elemento de menú como habilitado o deshabilitado. El destino de cada comando de menú proporciona esta información mediante la implementación de un controlador ON_UPDATE_COMMAND_UI. Para cada uno de los objetos de interfaz de usuario de comandos en la aplicación, utilice la ventana Propiedades para crear una entrada de mapa de mensajes y el prototipo de función para cada controlador.

Para obtener más información sobre cómo el `ICommandUI` interfaz se utiliza en el enrutamiento de comandos, vea [Cómo: Agregar comando enrutamiento a la Windows Forms Control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Para obtener más información sobre el uso de Windows Forms, consulte [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Para obtener más información sobre cómo se administran los comandos de la interfaz de usuario en MFC, vea [CCmdUI (clase)](../../mfc/reference/ccmdui-class.md).

## <a name="check"></a> ICommandUI::Check

Establece el elemento de interfaz de usuario para este comando en el estado de comprobación adecuada.
```
property UICheckState Check;
```

## <a name="remarks"></a>Comentarios

Esta propiedad establece el elemento de interfaz de usuario para este comando en el estado de comprobación adecuada. Establecer comprobación en los siguientes valores:
- Desactive 0
- 1 protección
- 2 establecer indeterminado

## <a name="continuerouting"></a> ICommandUI::ContinueRouting

Indica el mecanismo de enrutamiento de comandos para enrutar el mensaje actual de la cadena de controladores de continuar.
```
void ContinueRouting();
```

## <a name="remarks"></a>Comentarios

Se trata de una función miembro avanzado que debe usarse junto con un controlador ON_COMMAND_EX que devuelve FALSE. Para obtener más información, consulte TN006 de nota técnica: Mapas de mensajes.

## <a name="enabled"></a> ICommandUI::Enabled

Habilita o deshabilita el elemento de interfaz de usuario para este comando.
```
property bool Enabled;
```

## <a name="remarks"></a>Comentarios

Esta propiedad habilita o deshabilita el elemento de interfaz de usuario para este comando. Establezca Enabled en True para habilitar el elemento, FALSE para deshabilitarla.

## <a name="id"></a> ICommandUI::ID

Obtiene el identificador del objeto de interfaz de usuario, representado por el objeto ICommandUI.
```
property unsigned int ID;
```

## <a name="remarks"></a>Comentarios

Esta propiedad obtiene el identificador (un identificador) de otro objeto de interfaz de usuario representado por el objeto ICommandUI, botón de barra de herramientas o el elemento de menú.

## <a name="index"></a> ICommandUI::Index

Obtiene el índice del objeto de interfaz de usuario, representado por el objeto ICommandUI.
```
property unsigned int Index;
```

## <a name="remarks"></a>Comentarios

Esta propiedad obtiene el índice (un identificador) de otro objeto de interfaz de usuario representado por el objeto ICommandUI, botón de barra de herramientas o el elemento de menú.

## <a name="radio"></a> ICommandUI::Radio

Establece el elemento de interfaz de usuario para este comando en el estado de comprobación adecuada.
```
property bool Radio;
```

## <a name="remarks"></a>Comentarios

Esta propiedad establece el elemento de interfaz de usuario para este comando en el estado de comprobación adecuada. Establece el Radio en True para habilitar el elemento; en caso contrario, FALSE.

## <a name="text"></a> ICommandUI::Text

Establece el texto del elemento de interfaz de usuario para este comando.
```
property String^ Text;
```

## <a name="remarks"></a>Comentarios

Esta propiedad establece el texto del elemento de interfaz de usuario para este comando. Establezca texto en un identificador de cadena de texto.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h (definido en el ensamblado atlmfc\lib\mfcmifc80.dll)

## <a name="see-also"></a>Vea también

[CCmdUI (clase)](../../mfc/reference/ccmdui-class.md)
