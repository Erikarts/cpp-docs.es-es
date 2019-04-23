---
title: make_public
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.make_public
- make_public_CPP
helpviewer_keywords:
- pragmas, make_public
- make_public pragma
ms.assetid: c3665f4d-268a-4932-9661-c37c8ae6a341
ms.openlocfilehash: d569758f90b9e55f65ad13517f86dea41d151ca8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039129"
---
# <a name="makepublic"></a>make_public
Indica que un tipo nativo debe tener accesibilidad pública de ensamblado.

## <a name="syntax"></a>Sintaxis

```
#pragma make_public(type)
```

### <a name="parameters"></a>Parámetros

*tipo* es el nombre del tipo que desea tener accesibilidad pública de ensamblado.

## <a name="remarks"></a>Comentarios

**make_public** es útil cuando es el tipo nativo que desea hacer referencia desde un archivo .h que no se puede cambiar. Si desea usar el tipo nativo en signatura de una función pública en un tipo con visibilidad pública de ensamblado, el tipo nativo también debe tener accesibilidad pública de ensamblado o el compilador emitirá una advertencia.

**make_public** debe especificarse en el ámbito global y solo tiene efecto desde el punto en donde se declara hasta el final del archivo de código fuente.

El tipo nativo puede ser implícita o explícitamente privado; consulte [visibilidad de tipos](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) para obtener más información.

## <a name="examples"></a>Ejemplos

El ejemplo siguiente es el contenido de un archivo .h que contiene las definiciones para dos structs nativos.

```cpp
// make_public_pragma.h
struct Native_Struct_1 { int i; };
struct Native_Struct_2 { int i; };
```

Ejemplo de código siguiente consume el archivo de encabezado y se muestra que, a menos que marque explícitamente los structs nativos como públicos con **make_public**, el compilador generará una advertencia cuando se intenta usar los structs nativos en el firma de función pública en un tipo público administrado.

```cpp
// make_public_pragma.cpp
// compile with: /c /clr /W1
#pragma warning (default : 4692)
#include "make_public_pragma.h"
#pragma make_public(Native_Struct_1)

public ref struct A {
   void Test(Native_Struct_1 u) {u.i = 0;}   // OK
   void Test(Native_Struct_2 u) {u.i = 0;}   // C4692
};
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)