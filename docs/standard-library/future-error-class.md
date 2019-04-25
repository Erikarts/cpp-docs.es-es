---
title: future_error (Clase)
ms.date: 11/04/2016
f1_keywords:
- future/std::future_error
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
ms.openlocfilehash: 2b3f754c0ceb7384d99c6a657de214d30aca24b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159761"
---
# <a name="futureerror-class"></a>future_error (Clase)

Describe un objeto de excepción que pueden producir los métodos de tipos que administran objetos [future](../standard-library/future-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
class future_error : public logic_error {
public:
    future_error(error_code code);

const error_code& code() const throw();

const char *what() const throw();

};
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<futura >

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[logic_error (Clase)](../standard-library/logic-error-class.md)<br/>
[error_code (Clase)](../standard-library/error-code-class.md)<br/>
