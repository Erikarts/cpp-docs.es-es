---
title: satype (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.satype
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
ms.openlocfilehash: 7588e8d855d648309c46d981898cfbbf7888f4c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407307"
---
# <a name="satype"></a>satype

Especifica el tipo de datos de la `SAFEARRAY` estructura.

## <a name="syntax"></a>Sintaxis

```cpp
[ satype(data_type) ]
```

### <a name="parameters"></a>Parámetros

*data_type*<br/>
Tipo de datos de la `SAFEARRAY` estructura de datos que se pasa como parámetro a un método de interfaz.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Parámetro de interfaz, el método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

## <a name="remarks"></a>Comentarios

El **satype** atributo de C++ especifica el tipo de datos de la `SAFEARRAY`.

> [!NOTE]
> Un nivel de direccionamiento indirecto se quita de la `SAFEARRAY` puntero en el archivo .idl generado de forma se declara en el archivo .cpp.

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_satype.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyModule")];
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A {
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="see-also"></a>Vea también

[Atributos de compilador](compiler-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[identificador](id.md)