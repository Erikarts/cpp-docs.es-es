---
title: Error del compilador C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: 20251292ec4635ea855a56890878bc55f567ab62
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58777472"
---
# <a name="compiler-error-c3888"></a>Error del compilador C3888

'name': C++/CLI no admite la expresión const asociada con este miembro de datos literal

El miembro de datos *name* que se declara con la palabra clave [literal](../../extensions/literal-cpp-component-extensions.md) se inicializa con un valor que no es compatible con el compilador. El compilador solo admite los tipos de constante integral, de enumeración o de cadena. La causa probable del error **C3888** es que el miembro de datos se inicializa con una matriz de bytes.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Compruebe que el miembro de datos declarado literal es un tipo admitido.

## <a name="see-also"></a>Vea también

[literal](../../extensions/literal-cpp-component-extensions.md)