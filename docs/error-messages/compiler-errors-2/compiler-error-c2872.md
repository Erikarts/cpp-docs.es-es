---
title: Error del compilador C2872
ms.date: 11/04/2016
f1_keywords:
- C2872
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
ms.openlocfilehash: 103998c7872b683c7405796ee28bd550246ae9bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257619"
---
# <a name="compiler-error-c2872"></a>Error del compilador C2872

'*símbolo*': símbolo ambiguo

El compilador no puede determinar el símbolo que se hace referencia a. Más de un símbolo con el nombre especificado está en el ámbito. Vea las notas después el mensaje de error para las declaraciones y las ubicaciones de archivo en el compilador encontró para el símbolo ambiguo. Para corregir este problema, puede calificar completamente el símbolo ambiguo mediante el uso de su espacio de nombres, por ejemplo, `std::byte` o `::byte`. También puede usar un [alias de espacio de nombres](../../cpp/namespaces-cpp.md#namespace_aliases) para proporcionar a un espacio de nombres incluye un nombre corto adecuado para su uso al eliminar la ambigüedad de los símbolos en el código fuente.

C2872 puede producirse si un archivo de encabezado incluye un [#using](../../cpp/namespaces-cpp.md#using_directives), y se incluye un archivo de encabezado siguiente que contiene un tipo que se encuentra también en el espacio de nombres especificado en el `using` directiva. Especifique un `using` la directiva solo después de todos los archivos de encabezado se especifican con `#include`.

C2872 puede producirse en Visual Studio 2013 debido a un conflicto entre la `Windows::Foundation::Metadata::Platform` enum tipo y C++ / c++ / CX definido por `Platform` espacio de nombres. Para solucionar este problema, siga estos pasos:

- Quite la cláusula "using namespace Windows::Foundation::Metadata" de los archivos del proyecto.

- Especifique el nombre completo para cualquier tipo que se incluye en este espacio de nombres.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C2872, porque no se realiza una referencia ambigua a una variable denominada `i`; dos variables con el mismo nombre que se encuentran dentro del ámbito:

```cpp
// C2872.cpp
// compile with: cl /EHsc C2872.cpp
namespace A {
   int i;
}

using namespace A;
int i;
int main() {
   ::i++;   // ok, uses i from global namespace
   A::i++;   // ok, uses i from namespace A
   i++;   // C2872 ambiguous: ::i or A::i?
   // To fix this issue, use the fully qualified name
   // for the intended variable.
}
```
