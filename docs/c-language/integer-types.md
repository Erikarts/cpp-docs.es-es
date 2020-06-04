---
title: Tipos enteros
ms.date: 11/04/2016
helpviewer_keywords:
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
ms.openlocfilehash: 23da055b56e2ae77fed796d9ba8e7f227e572a9f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232857"
---
# <a name="integer-types"></a>Tipos enteros

A cada constante entera se le asigna un tipo basado en su valor y en la manera en que se expresa. Puede forzar cualquier constante entera al tipo **long** anexando la letra **l** o **L** al final de la constante; puede forzarla para que sea del tipo `unsigned` anexando **u** o **U** al valor. La letra **l** minúscula se puede confundir con el dígito 1 y debe evitarse. Algunas formas de constantes enteras **long** son las siguientes:

```
/* Long decimal constants */
10L
79L

/* Long octal constants */
012L
0115L

/* Long hexadecimal constants */
0xaL or 0xAL
0X4fL or 0x4FL

/* Unsigned long decimal constant */
776745UL
778866LU
```

El tipo que se asigna a una constante depende del valor que representa la constante. El valor de una constante debe estar en el intervalo de valores representables para su tipo. El tipo de una constante determina qué conversiones se realizan cuando se usa la constante en una expresión o cuando se aplica el signo menos ( **-** ). En esta lista se resumen las reglas de conversión para constantes de tipo entero.

- El tipo para una constante decimal sin sufijo es `int`, **long int** o **unsigned long int**. El primero de estos tres tipos en los que se puede representar el valor de la constante es el tipo asignado a la constante.

- El tipo asignado a las constantes octales y hexadecimales sin sufijos es `int`, `unsigned int`, **long int** o **unsigned long int**, dependiendo del tamaño de la constante.

- El tipo asignado a las constantes con sufijo **u** o **U** es **unsigned int** o **unsigned long int**, dependiendo de su tamaño.

- El tipo asignado a las constantes con sufijo **l** o **L** es **long int** o **unsigned long int**, dependiendo de su tamaño.

- El tipo asignado a las constantes con sufijo **u** o **U** y un sufijo **l** o **L** es **unsigned long int**.

## <a name="see-also"></a>Vea también

[Constantes de tipo entero de C](../c-language/c-integer-constants.md)
