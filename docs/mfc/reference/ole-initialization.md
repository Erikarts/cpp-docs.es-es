---
title: Inicialización de OLE
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 3d49b37ffc2561fa9a51463a893ec2ba4f4fb725
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310284"
---
# <a name="ole-initialization"></a>Inicialización de OLE

Antes de que una aplicación puede usar servicios del sistema OLE, debe inicializar la DLL del sistema OLE y compruebe que los archivos DLL son la versión correcta. El `AfxOleInit` función inicializa la DLL del sistema OLE.

### <a name="ole-initialization"></a>Inicialización de OLE

|||
|-|-|
|[AfxOleInit](#afxoleinit)|Inicializa las bibliotecas OLE.|
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|Llame a esta función en el objeto de aplicación `InitInstance` función para habilitar la compatibilidad con la contención de controles OLE.|

## <a name="afxenablecontrolcontainer"></a> AfxEnableControlContainer

Llame a esta función en el objeto de aplicación `InitInstance` función para habilitar la compatibilidad con la contención de controles OLE.

### <a name="syntax"></a>Sintaxis

```
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de los controles OLE (ahora denominados controles de ActiveX), consulte [temas de Control ActiveX](../mfc-activex-controls.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="afxoleinit"></a>  AfxOleInit

Inicializa la compatibilidad con OLE para la aplicación.

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ejecuta correctamente; 0 si se produce un error en la inicialización, posiblemente porque se han instalado versiones incorrectas de los archivos DLL del sistema OLE.

### <a name="remarks"></a>Comentarios

Llame a esta función para inicializar la compatibilidad con OLE para una aplicación MFC. Cuando se llama a esta función, tienen lugar las acciones siguientes:

- Inicializa la biblioteca COM en el apartamento actual de la aplicación de llamada. Para obtener más información, consulte [OleInitialize](/windows/desktop/api/ole2/nf-ole2-oleinitialize).

- Crea un objeto de filtro de mensajes, implementar el [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) interfaz. Este filtro de mensajes puede obtenerse con una llamada a [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

> [!NOTE]
>  Si **AfxOleInit** se llama desde una DLL de MFC, la llamada se producirá un error. El error se produce porque la función supone que, si se llama desde un archivo DLL, la aplicación de llamada inicializó previamente el sistema OLE.

> [!NOTE]
>  Las aplicaciones MFC deben inicializarse como contenedor uniproceso (STA). Si se llama a [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex) en su `InitInstance` invalidar, especifique COINIT_APARTMENTTHREADED (en lugar de COINIT_MULTITHREADED).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
