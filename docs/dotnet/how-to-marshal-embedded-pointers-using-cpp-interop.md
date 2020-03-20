---
title: 'Cómo: Calcular las referencias de punteros incrustados mediante la interoperabilidad de C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- structures [C++], marshaling embedded pointers
- interop [C++], embedded pointers
- C++ Interop, embedded pointers
- marshaling [C++], embedded pointers
- pointers [C++], marshaling
- data marshaling [C++], embedded pointers
ms.assetid: 05fb8858-97f2-47aa-86b2-2c0ad713bdb2
ms.openlocfilehash: 972d7a9c09100c35cb0bf527efbd0884c909c46d
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79544902"
---
# <a name="how-to-marshal-embedded-pointers-using-c-interop"></a>Cómo: Calcular las referencias de punteros incrustados mediante la interoperabilidad de C++

En los siguientes ejemplos de código se usan las directivas de #pragma [administradas y no administradas](../preprocessor/managed-unmanaged.md) para implementar funciones administradas y no administradas en el mismo archivo, pero estas funciones interoperan de la misma manera si se definen en archivos independientes. No es necesario compilar los archivos que contienen solo funciones no administradas con [/CLR (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo se puede llamar a una función no administrada que toma una estructura que contenga punteros desde una función administrada. La función administrada crea una instancia de la estructura e inicializa el puntero incrustado con la palabra clave New (en lugar de la palabra clave [ref New, gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md) ). Dado que esto asigna la memoria en el montón nativo, no es necesario anclar la matriz para suprimir la recolección de elementos no utilizados. Sin embargo, la memoria se debe eliminar explícitamente para evitar la fuga de memoria.

```cpp
// marshal_embedded_pointer.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

// unmanaged struct
struct ListStruct {
   int count;
   double* item;
};

#pragma unmanaged

void UnmanagedTakesListStruct(ListStruct list) {
   printf_s("[unmanaged] count = %d\n", list.count);
   for (int i=0; i<list.count; i++)
      printf_s("array[%d] = %f\n", i, list.item[i]);
}

#pragma managed

int main() {
   ListStruct list;
   list.count = 10;
   list.item = new double[list.count];

   Console::WriteLine("[managed] count = {0}", list.count);
   Random^ r = gcnew Random(0);
   for (int i=0; i<list.count; i++) {
      list.item[i] = r->NextDouble() * 100.0;
      Console::WriteLine("array[{0}] = {1}", i, list.item[i]);
   }

   UnmanagedTakesListStruct( list );
   delete list.item;
}
```

```Output
[managed] count = 10
array[0] = 72.624326996796
array[1] = 81.7325359590969
array[2] = 76.8022689394663
array[3] = 55.8161191436537
array[4] = 20.6033154021033
array[5] = 55.8884794618415
array[6] = 90.6027066011926
array[7] = 44.2177873310716
array[8] = 97.754975314138
array[9] = 27.370445768987
[unmanaged] count = 10
array[0] = 72.624327
array[1] = 81.732536
array[2] = 76.802269
array[3] = 55.816119
array[4] = 20.603315
array[5] = 55.888479
array[6] = 90.602707
array[7] = 44.217787
array[8] = 97.754975
array[9] = 27.370446
```

## <a name="see-also"></a>Consulte también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
