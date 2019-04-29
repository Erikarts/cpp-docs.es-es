---
title: Especificadores
ms.date: 11/04/2016
helpviewer_keywords:
- declaration specifiers
- declarations, specifiers
- specifiers, in declarations
ms.assetid: 8b14e844-9880-4571-8779-28c8efe44633
ms.openlocfilehash: aef967b26321f289cb8c7bd0402d7fe8f12b77b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330991"
---
# <a name="specifiers"></a>Especificadores

Este tema se describe la *decl-specifiers* componente (especificadores de declaración) de un [declaración](declarations-and-definitions-cpp.md).

Los siguientes marcadores de posición y palabras clave de lenguaje son especificadores de declaración:

*storage-class-specifier*

*type-specifier*

*function-specifier*

[friend](friend-cpp.md)

[typedef](aliases-and-typedefs-cpp.md) `(` *extended-decl-modifier-seq* `)`

[__declspec](declspec.md) `(` *extended-decl-modifier-seq* `)`

## <a name="remarks"></a>Comentarios

El *decl-specifiers* parte de una declaración es la secuencia más larga de *decl-specifiers* que se puede tomar para indicar un nombre de tipo, sin incluir el puntero o hacer referencia a los modificadores. El resto de la declaración es la *declarador*, que incluye el nombre introducido.

En la tabla siguiente incluye cuatro declaraciones y, a continuación, enumera cada declaración *decl-specifers* y *declarador* componente por separado.

|Declaración|*decl-specifiers*|`declarator`|
|-----------------|------------------------|------------------|
|`char *lpszAppName;`|**char**|`*lpszAppName`|
|`typedef char * LPSTR;`|**char**|`*LPSTR`|
|`const int func1();`|**const int**|`func1`|
|`volatile void *pvvObj;`|**anular volátil**|`*pvvObj`|

Dado que **firmado**, **sin signo**, **largo**, y **corto** implican **int**, un  **TypeDef** nombre siguiente, una de estas palabras clave se considera que es un miembro de *declarator-list,* no de *decl-specifiers*.

> [!NOTE]
>  Dado que un nombre se puede declarar de nuevo, su interpretación está sujeta a la declaración más reciente del ámbito actual. Nueva declaración puede afectar a cómo se interpretan los nombres por el compilador, especialmente **typedef** nombres.

## <a name="see-also"></a>Vea también

[Declaraciones y definiciones](declarations-and-definitions-cpp.md)
