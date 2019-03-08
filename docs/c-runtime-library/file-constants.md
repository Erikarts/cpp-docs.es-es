---
title: Constantes de archivo
ms.date: 11/04/2016
f1_keywords:
- _O_EXCL
- _O_RDWR
- _O_APPEND
- _O_RDONLY
- _O_TRUNC
- _O_CREAT
- _O_WRONLY
helpviewer_keywords:
- _O_RDWR constant
- O_EXCL constant
- O_RDWR constant
- O_WRONLY constant
- O_APPEND constant
- O_CREAT constant
- _O_CREAT constant
- _O_APPEND constant
- _O_EXCL constant
- O_TRUNC constant
- _O_RDONLY constant
- _O_TRUNC constant
- O_RDONLY constant
- _O_WRONLY constant
ms.assetid: c8fa5548-9ac2-4217-801d-eb45e86f2fa4
ms.openlocfilehash: 2dc473db50b1835d4e1495ce255c0a826563b70a
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220444"
---
# <a name="file-constants"></a>Constantes de archivo

## <a name="syntax"></a>Sintaxis

```
#include <fcntl.h>
```

## <a name="remarks"></a>Comentarios

La expresión de entero formada a partir de una o varias de estas constantes determina el tipo de operaciones de lectura o escritura permitidas. Se forma mediante la combinación de una o varias constantes con una constante de modo de traducción.

Las constantes de archivo son las siguientes:

|Constante|Descripción|
|-|-|
| `_O_APPEND`  | Recoloca el puntero de archivo al final del archivo antes de cada operación de escritura.  |
| `_O_CREAT`  | Crea y abre un nuevo archivo para escritura; esto no tiene ningún efecto si el archivo especificado por *filename* existe.  |
| `_O_EXCL`  | Devuelve un valor de error si el archivo especificado por *filename* existe. Solo se aplica cuando se usa con `_O_CREAT`.  |
| `_O_RDONLY`  | Abre el archivo solo para lectura; si se especifica esta marca, no se pueden proporcionar `_O_RDWR` ni `_O_WRONLY`.  |
| `_O_RDWR`  | Abre el archivo para lectura y escritura; si se especifica esta marca, no se pueden proporcionar `_O_RDONLY` ni `_O_WRONLY`.  |
| `_O_TRUNC`  | Abre un archivo existente y lo trunca a longitud cero. El archivo debe tener permiso de escritura. Se destruye el contenido del archivo. Si se proporciona esta marca, no se puede especificar `_O_RDONLY`.  |
| `_O_WRONLY`  | Abre el archivo solo para escritura; si se especifica esta marca, no se pueden proporcionar `_O_RDONLY` ni `_O_RDWR`.  |

## <a name="see-also"></a>Vea también

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
