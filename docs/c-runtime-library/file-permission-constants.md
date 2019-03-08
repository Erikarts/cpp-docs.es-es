---
title: Constantes de permiso de archivo
ms.date: 11/04/2016
f1_keywords:
- _S_IWRITE
- _S_IREAD
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
ms.openlocfilehash: c0c5e02458fa6b5436b029392a40bd2f54f22c0c
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220288"
---
# <a name="file-permission-constants"></a>Constantes de permiso de archivo

## <a name="syntax"></a>Sintaxis

```
#include <sys/stat.h>
```

## <a name="remarks"></a>Comentarios

Una de estas constantes es necesaria cuando `_O_CREAT` (`_open`, `_sopen`) se especifica.

El argumento `pmode` especifica la configuración de los permisos del archivo tal y como sigue.

|Constante|Significado|
|--------------|-------------|
|`_S_IREAD`|Lectura permitida|
|`_S_IWRITE`|Escritura permitida|
|`_S_IREAD` &#124; `_S_IWRITE`|Lectura y escritura permitidas|

Cuando se usa como el argumento `pmode` para `_umask`, la constante de manifiesto establece la configuración del permiso, como se indica a continuación.

|Constante|Significado|
|--------------|-------------|
|`_S_IREAD`|Escritura no permitida (el archivo es de solo lectura)|
|`_S_IWRITE`|Lectura no permitida (el archivo es de solo escritura)|
|`_S_IREAD` &#124; `_S_IWRITE`|Lectura y escritura no permitidas|

## <a name="see-also"></a>Vea también

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_umask](../c-runtime-library/reference/umask.md)<br/>
[Tipos estándar](../c-runtime-library/standard-types.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
