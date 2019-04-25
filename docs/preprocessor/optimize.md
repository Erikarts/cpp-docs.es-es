---
title: optimize
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
ms.openlocfilehash: 9f5240fc59f59a71ddb3d18b67fadf3463a0d1ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328177"
---
# <a name="optimize"></a>optimize

Especifica las optimizaciones que se efectuarán función por función.

## <a name="syntax"></a>Sintaxis

```
#pragma optimize( "[optimization-list]", {on | off} )
```

## <a name="remarks"></a>Comentarios

El **optimizar** pragma debe aparecer fuera de una función y tiene efecto en la primera función definida después de la pragma. El *en* y *desactivar* argumentos activar las opciones especificadas en el *optimization-list* activado o desactivado.

El *optimization-list* puede ser cero o más de los parámetros mostrados en la tabla siguiente.

### <a name="parameters-of-the-optimize-pragma"></a>Parámetros de la directiva pragma optimize

|Parámetros|Tipo de optimización|
|--------------------|--------------------------|
|*g*|Habilitar optimizaciones globales.|
|*s* o *t*|Especificar secuencias cortas o rápidas de código máquina.|
|*y*|Generar punteros de marco en la pila del programa.|

Estas son las mismas letras usadas con la [/O](../build/reference/o-options-optimize-code.md) opciones del compilador. Por ejemplo, la directiva pragma siguiente es equivalente a la opción del compilador `/Os`:

```
#pragma optimize( "ts", on )
```

Mediante el **optimizar** pragma con la cadena vacía (**""**) es una forma especial de la directiva:

Cuando se usa el *desactivar* parámetro, desactiva todas las optimizaciones, *g*, *s*, *t*, y *y*, desactivado.

Cuando se usa el *en* parámetro, restablece las optimizaciones a aquellas que especificó con el [/O](../build/reference/o-options-optimize-code.md) opción del compilador.

```
#pragma optimize( "", off )
.
.
.
#pragma optimize( "", on )
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)