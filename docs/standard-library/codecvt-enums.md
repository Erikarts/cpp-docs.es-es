---
title: '&lt;codecvt&gt; (Enumeraciones)'
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: 0b43c7c148076e96dd0d3f444ffa8b6bad7c8b29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405292"
---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt&gt; (Enumeraciones)

## <a name="codecvt_mode"></a>  codecvt_mode (Enumeración)

Especifica la información de configuración de las facetas de [configuración regional](../standard-library/locale-class.md).

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>Comentarios

La enumeración define tres constantes que proporcionan información de configuración a las facetas de configuración regional declaradas en [\<codecvt>](../standard-library/codecvt.md). Los diferentes valores son:

- `consume_header`, para consumir una secuencia de encabezados iniciales al leer una secuencia multibyte y determinar los modos endian de la secuencia multibyte que se va a leer

- `generate_header`, para generar una secuencia de encabezados iniciales al escribir una secuencia multibyte para anunciar los modos endian de la secuencia multibyte siguiente que se va a escribir

- `little_endian`, para generar una secuencia multibyte en orden little endian, en lugar del orden big endian predeterminado

Estas constantes pueden usar OR en combinaciones arbitrarias.

## <a name="see-also"></a>Vea también

[\<codecvt>](../standard-library/codecvt.md)<br/>
