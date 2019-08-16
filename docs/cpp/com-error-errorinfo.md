---
title: _com_error::ErrorInfo
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorInfo
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
ms.openlocfilehash: 59ada8a7e098e57cca5641a439365851bbae2485
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155077"
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo

**Específicos de Microsoft**

Recupera el objeto `IErrorInfo` pasado al constructor.

## <a name="syntax"></a>Sintaxis

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>Valor devuelto

Elemento `IErrorInfo` sin formato pasado en el constructor.

## <a name="remarks"></a>Comentarios

Recupera el encapsulado `IErrorInfo` de elemento en un `_com_error` objeto, o NULL si no hay ningún `IErrorInfo` se registra el elemento. El llamador debe llamar a `Release` en el objeto devuelto cuando terminado de usarlo.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_error (Clase)](../cpp/com-error-class.md)