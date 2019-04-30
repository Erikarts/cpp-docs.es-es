---
title: serializar_as
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
ms.openlocfilehash: 2294d8fe94a32f281332c963b21a542366ae3207
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386088"
---
# <a name="marshalas"></a>serializar_as

Este método convierte los datos entre los entornos nativo y administrado.

## <a name="syntax"></a>Sintaxis

```
To_Type marshal_as<To_Type>(
   From_Type input
);
```

#### <a name="parameters"></a>Parámetros

*input*<br/>
[in] El valor que se desea calcular las referencias a un `To_Type` variable.

## <a name="return-value"></a>Valor devuelto

Una variable de tipo `To_Type` que es el valor convertido de `input`.

## <a name="remarks"></a>Comentarios

Este método es una manera simplificada de convertir datos entre los tipos nativos y administrados. Para determinar qué tipos de datos son compatibles, consulte [Overview of Marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md). Algunas conversiones de datos requieren un contexto. Puede convertir los tipos de datos mediante el [marshal_context Class](../dotnet/marshal-context-class.md).

Si se intenta serializar un par de tipos de datos que no son compatibles, `marshal_as` generará un error [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) en tiempo de compilación. Lea el mensaje proporcionado con el error para obtener más información. El error `C4996` se puede generar para algunas funciones, aparte de las que están en desuso. Un ejemplo de esto consiste en intentar para serializar un par de tipos de datos que no se admiten.

La biblioteca de cálculo de referencias se compone de varios archivos de encabezado. Cualquier conversión requiere solo un archivo, pero puede incluir archivos adicionales si los necesita para otras conversiones. Para ver qué conversiones están asociadas con qué archivos, consulte la tabla de `Marshaling Overview`. Independientemente de la conversión que desee hacer, el requisito de espacio de nombres siempre está en vigor.

## <a name="example"></a>Ejemplo

Este ejemplo calcula las referencias de `const char*` para un tipo de variable `System::String`.

```
// marshal_as_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   const char* message = "Test String to Marshal";
   String^ result;
   result = marshal_as<String^>( message );
   return 0;
}
```

## <a name="requirements"></a>Requisitos

**Archivo de encabezado:** \<msclr\marshal. h >, \<msclr\marshal_windows. h >, \<msclr\marshal_cppstd. h >, o \<msclr\marshal_atl. h >

**Namespace:** msclr:: Interop

## <a name="see-also"></a>Vea también

[Información general de la serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_context (Clase)](../dotnet/marshal-context-class.md)
