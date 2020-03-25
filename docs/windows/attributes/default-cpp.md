---
title: default (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.default
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
ms.openlocfilehash: b789f82f4b5a09b86d72dfde5d783665cf2e918a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167191"
---
# <a name="default-c"></a>default (C++)

Indica que la interfaz personalizada o dispinterface definida en una coclase representa la interfaz de programación predeterminada.

## <a name="syntax"></a>Sintaxis

```cpp
[ default(interface1, interface2) ]
```

### <a name="parameters"></a>Parámetros

*interface1*<br/>
Interfaz predeterminada que estará disponible para los entornos de scripting que crean un objeto basado en la clase definida con el atributo **default** .

Si no se especifica ninguna interfaz predeterminada, se usa la primera aparición de una interfaz sin origen como valor predeterminado.

*interfaz2*<br/>
Opta La interfaz de origen predeterminada. También debe especificar esta interfaz con el atributo [source](source-cpp.md) .

Si no se especifica ninguna interfaz de origen predeterminada, se usa la primera interfaz de origen como valor predeterminado.

## <a name="remarks"></a>Observaciones

El atributo C++ **default** tiene la misma funcionalidad que el atributo MIDL [default](/windows/win32/Midl/default) . El atributo **default** también se usa con el atributo [case](case-cpp.md) .

## <a name="example"></a>Ejemplo

En el código siguiente se muestra cómo se usa **default** en la definición de una coclase para especificar `ICustomDispatch` como la interfaz de programación predeterminada:

```cpp
// cpp_attr_ref_default.cpp
// compile with: /LD
#include "windows.h"
[module(name="MyLibrary")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};

[dual, uuid("9E66A291-4365-11D2-A997-00C04FA37DDB")]
__interface IDual {
   HRESULT Dual([in] long l, [out, retval] long *pLong);
};

[object, uuid("9E66A293-4365-11D2-A997-00C04FA37DDB")]
__interface ICustomDispatch : public IDispatch {
   HRESULT Dispatch([in] long l, [out, retval] long *pLong);
};

[   coclass, default(ICustomDispatch), source(IDual), uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")
]
class CClass : public ICustom, public IDual, public ICustomDispatch {
   HRESULT Custom(long l, long *pLong) { return(S_OK); }
   HRESULT Dual(long l, long *pLong) { return(S_OK); }
   HRESULT Dispatch(long l, long *pLong) { return(S_OK); }
};

int main() {
#if 0 // Can't instantiate without implementations of IUnknown/IDispatch
   CClass *pClass = new CClass;

   long llong;

   pClass->custom(1, &llong);
   pClass->dual(1, &llong);
   pClass->dispinterface(1, &llong);
   pClass->dispatch(1, &llong);

   delete pClass;
#endif
   return(0);
}
```

El atributo [source](source-cpp.md) también tiene un ejemplo de cómo usar **default**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **estructura**, miembro de datos|
|**Reiterativo**|No|
|**Atributos requeridos**|**coclase** (cuando se aplica a una **clase** o **struct**)|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[coclass](coclass.md)
