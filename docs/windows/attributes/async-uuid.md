---
title: async_uuid (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.async_uuid
helpviewer_keywords:
- async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
ms.openlocfilehash: 4c2bca9165d8b23f8cfa4f0f5523c882fd2f52bf
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035801"
---
# <a name="asyncuuid"></a>async_uuid

Especifica el UUID que indica al compilador MIDL para definir las versiones sincrónicas y asincrónicas de una interfaz COM.

## <a name="syntax"></a>Sintaxis

```cpp
[async_uuid (uuid)]
```

### <a name="parameters"></a>Parámetros

*uuid*<br/>
Un UUID que identifica la versión de la interfaz.

## <a name="remarks"></a>Comentarios

El **async_uuid** atributo de C++ tiene la misma funcionalidad que el [async_uuid](/windows/desktop/Midl/async-uuid) atributo MIDL.

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_async_uuid.cpp
// compile with: /LD
#include <Windows.h>
[module(name="Test")];
[object, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb"),
async_uuid("e8583106-38fd-487e-912e-4fc8645c677e")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|`interface`|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|**dual**, **dispinterface**|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)