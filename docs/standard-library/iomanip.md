---
title: '&lt;iomanip&gt;'
ms.date: 11/04/2016
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
helpviewer_keywords:
- iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
ms.openlocfilehash: 983fbc190fb83b81534e3888c748c0bf9c235638
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404941"
---
# <a name="ltiomanipgt"></a>&lt;iomanip&gt;

Incluir el `iostreams` encabezado estándar \<iomanip > para definir varios manipuladores que toman un solo argumento.

## <a name="syntax"></a>Sintaxis

```cpp
#include <iomanip>
```

## <a name="remarks"></a>Comentarios

Cada uno de estos manipuladores devuelve un tipo sin especificar, denominado `T1` a través de `T10`, que ambas sobrecargas `basic_istream` \< **Elem**, **Tr** > `::` [operador >>](../standard-library/istream-operators.md#op_gt_gt) y `basic_ostream` \< **Elem**, **Tr** > `::` [operador <<](../standard-library/ostream-operators.md#op_lt_lt).

### <a name="manipulators"></a>Manipuladores

|||
|-|-|
|[get_money](../standard-library/iomanip-functions.md#iomanip_get_money)|Obtiene un importe monetario, opcionalmente en formato internacional.|
|[get_time](../standard-library/iomanip-functions.md#iomanip_get_time)|Obtiene una hora en una estructura de hora con un formato especificado.|
|[put_money](../standard-library/iomanip-functions.md#iomanip_put_money)|Proporciona un importe monetario, opcionalmente en formato internacional.|
|[put_time](../standard-library/iomanip-functions.md#iomanip_put_time)|Proporciona una hora en una estructura de hora y una cadena de formato que se va a usar.|
|[quoted](../standard-library/iomanip-functions.md#quoted)|Permite realizar un práctico recorrido de ida y vuelta de cadenas con operadores de inserción y extracción.|
|[resetiosflags](../standard-library/iomanip-functions.md#resetiosflags)|Borra las marcas especificadas.|
|[setbase](../standard-library/iomanip-functions.md#setbase)|Establece la base de los enteros.|
|[setfill](../standard-library/iomanip-functions.md#setfill)|Establece el carácter que se usará para rellenar los espacios en una presentación justificada a la derecha.|
|[setiosflags](../standard-library/iomanip-functions.md#setiosflags)|Establece las marcas especificadas.|
|[setprecision](../standard-library/iomanip-functions.md#setprecision)|Establece la precisión de los valores de punto flotante.|
|[setw](../standard-library/iomanip-functions.md#setw)|Especifica el ancho del campo de presentación.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>
