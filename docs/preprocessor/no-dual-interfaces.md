---
title: no_dual_interfaces
ms.date: 11/04/2016
f1_keywords:
- no_dual_interfaces
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
ms.openlocfilehash: ae75bc2e974f374768f1a9e5a0e1ced61e9904b0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023807"
---
# <a name="nodualinterfaces"></a>no_dual_interfaces
**Específicos de C++**

Cambia la manera en que el compilador genera las funciones de contenedor para los métodos de interfaz dual.

## <a name="syntax"></a>Sintaxis

```
no_dual_interfaces
```

## <a name="remarks"></a>Comentarios

Normalmente, el contenedor llamará al método a través de la tabla de funciones virtuales para la interfaz. Con **no_dual_interfaces**, el contenedor en su lugar llama `IDispatch::Invoke` para invocar el método.

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)