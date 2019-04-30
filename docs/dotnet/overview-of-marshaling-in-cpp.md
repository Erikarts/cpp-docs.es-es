---
title: Información general de la serialización en C++
ms.date: 06/28/2018
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
ms.openlocfilehash: 9e3b8f561ce6609eb2afedb527a16c4803f69c53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384743"
---
# <a name="overview-of-marshaling-in-c"></a>Información general de la serialización en C++

En modo mixto, deben serializar los datos entre los tipos nativos y los administrados. Visual Studio 2008 introdujo la *biblioteca de serialización* para ayudar a calcular y convertir los datos de una manera sencilla.  La biblioteca de serialización consta de un conjunto de funciones y una `marshal_context` clases que realizan el cálculo de referencias para los tipos comunes. La biblioteca está definida en estos encabezados en el **incluyen/msclr** directorio para su edición de Visual Studio:

|Header|Descripción|
|---------------|-----------------|
|serializar.h|`marshal_context` clase y las funciones de cálculo de referencias sin contexto|
|serializar_atl.h| Funciones de serialización de tipos ATL|
|serializar_cppstd.h|Funciones de serialización de tipos estándares de C++|
|marshal_windows.h|Funciones de serialización de tipos de Windows|

La ruta de acceso predeterminada para **msclr** carpeta es algo parecido a esto dependiendo de qué edición tiene y el número de compilación:

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

Puede usar la biblioteca de serialización con o sin un [marshal_context Class](../dotnet/marshal-context-class.md). Algunas conversiones requieren un contexto. Otras conversiones se pueden implementar mediante el [marshal_as](../dotnet/marshal-as.md) función. En la tabla siguiente se enumeran las conversiones actuales compatibles y se indica si requieren un contexto y el archivo de serializar que se debe incluir:

|De tipo|A tipo|Método serializar|Incluir archivo|
|---------------|-------------|--------------------|------------------|
|System::String^|const char \*|serializar_context|serializar.h|
|const char \*|System::String^|serializar_as|serializar.h|
|Char \*|System::String^|serializar_as|serializar.h|
|System::String^|const wchar_t\*|serializar_context|serializar.h|
|const wchar_t \*|System::String^|serializar_as|serializar.h|
|wchar_t \*|System::String^|serializar_as|serializar.h|
|System::IntPtr|HANDLE|serializar_as|marshal_windows.h|
|HANDLE|System::IntPtr|serializar_as|marshal_windows.h|
|System::String^|BSTR|serializar_context|marshal_windows.h|
|BSTR|System::String^|serializar_as|serializar.h|
|System::String^|bstr_t|serializar_as|marshal_windows.h|
|bstr_t|System::String^|serializar_as|marshal_windows.h|
|System::String^|std::string|serializar_as|serializar_cppstd.h|
|std::string|System::String^|serializar_as|serializar_cppstd.h|
|System::String^|std::wstring|serializar_as|serializar_cppstd.h|
|std::wstring|System::String^|serializar_as|serializar_cppstd.h|
|System::String^|CStringT\<char>|serializar_as|serializar_atl.h|
|CStringT\<char>|System::String^|serializar_as|serializar_atl.h|
|System::String^|CStringT<wchar_t>|serializar_as|serializar_atl.h|
|CStringT<wchar_t>|System::String^|serializar_as|serializar_atl.h|
|System::String^|CComBSTR|serializar_as|serializar_atl.h|
|CComBSTR|System::String^|serializar_as|serializar_atl.h|

El cálculo de referencias requiere un contexto solo cuando se calcula de tipos de datos administrados a tipos de datos nativos y el tipo nativo que se va a convertir no tiene un destructor para la limpieza automática. El contexto de serialización destruye el tipo de datos nativo asignado en su destructor. Por consiguiente, las conversiones que requieren un contexto serán válidas solo hasta que se elimine el contexto. Para guardar cualquier valor de cálculo de referencias, debe copiar los valores a sus propias variables.

> [!NOTE]
>  Si ha incrustado valores `NULL`en la cadena, el resultado de serializar la cadena no se puede garantizar. Los valores `NULL` incrustados pueden hacer que la cadena se trunque o no pueda conservarse.

Este ejemplo muestra cómo incluir el directorio msclr en una declaración de encabezado de inclusión:

`#include "msclr\marshal_cppstd.h"`

La biblioteca de cálculo de referencias es extensible para que pueda agregar sus propios tipos de serialización. Para obtener más información sobre cómo extender la biblioteca de serialización, vea [Cómo: Extender la biblioteca de serialización](../dotnet/how-to-extend-the-marshaling-library.md).

En versiones anteriores, se podían serializar los datos mediante el uso de [de invocación de plataforma](/dotnet/framework/interop/consuming-unmanaged-dll-functions). Para obtener más información acerca de `PInvoke`, consulte [llamar a funciones nativas desde código administrado](../dotnet/calling-native-functions-from-managed-code.md).

## <a name="see-also"></a>Vea también

[Biblioteca de compatibilidad de C++](../dotnet/cpp-support-library.md)<br/>
[Cómo: Extender la biblioteca de serialización](../dotnet/how-to-extend-the-marshaling-library.md)
