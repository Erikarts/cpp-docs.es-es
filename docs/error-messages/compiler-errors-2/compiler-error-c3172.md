---
title: Error del compilador C3172
ms.date: 11/04/2016
f1_keywords:
- C3172
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
ms.openlocfilehash: 5c9c1561b63c740b9f7f5d85b2bf3e04de2542c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175191"
---
# <a name="compiler-error-c3172"></a>Error del compilador C3172

'nombre_de_módulo': no se puede especificar distintos atributos idl_module en un proyecto

[idl_module](../../windows/idl-module.md) atributos con el mismo nombre pero distintos `dllname` o `version` se encontraron parámetros en dos de los archivos en una compilación. Solo uno único `idl_module` atributo se puede especificar cada compilación.

Idéntico `idl_module` atributos se pueden especificar más de un archivo de código fuente.

Por ejemplo, si la siguiente `idl_module` se encontraron atributos:

```
// C3172.cpp
[module(name="MyMod")];
[ idl_module(name="x", dllname="file.dll", version="1.1") ];
int main() {}
```

Y luego,

```
// C3172b.cpp
// compile with: C3172.cpp
// C3172 expected
[ idl_module(name="x", dllname="file.dll", version="1.0") ];
```

el compilador generará el error C3172 (tenga en cuenta los valores de versión diferente).