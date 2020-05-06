---
title: extern (Especificador de clase de almacenamiento)
ms.date: 07/10/2018
helpviewer_keywords:
- extern keyword [C]
- storage class specifiers, extern
- extern keyword [C], storage class specifier
- external linkage, storage-class specifiers
- external linkage, extern modifier
ms.assetid: 6e16d927-291f-49e4-986c-9d91a482a441
ms.openlocfilehash: 6bbae7c778f5196ac0dca387265499b27119a367
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233839"
---
# <a name="extern-storage-class-specifier"></a>extern (Especificador de clase de almacenamiento)

Una variable declarada con el especificador de clase de almacenamiento **extern** es una referencia a una variable con el mismo nombre definido en otro archivo de origen. Se utiliza para hacer que la definición de variable de nivel externo esté visible. Una variable declarada como **extern** no tiene almacenamiento asignado para sí misma; es solo un nombre.

## <a name="example"></a>Ejemplo

En este ejemplo se muestran declaraciones de nivel interno y externo:

```c

// Source1.c

int i = 1;

// Source2. c

#include <stdio.h>

// Refers to the i that is defined in Source1.c:
extern int i;

void func(void);

int main()
{
    // Prints 1:
    printf_s("%d\n", i);
    func();
    return;
}

void func(void)
{
    // Address of global i assigned to pointer variable:
    static int *external_i = &i;

    // This definition of i hides the global i in Source.c:
    int i = 16;

    // Prints 16, 1:
    printf_s("%d\n%d\n", i, *external_i);
}
```

En este ejemplo, la variable `i` se define en Source1.c con un valor inicial de 1. Una declaración **extern** en Source2.c hace que “i” esté visible en ese archivo.

En la función `func`, la dirección de la variable global `i` se usa para inicializar la variable de puntero **static**`external_i`. Esto funciona porque la variable global tiene una duración **static**, lo que significa que la dirección no cambia durante la ejecución del programa. A continuación, una variable `i` se define dentro del ámbito de `func` como una variable local con el valor inicial 16. Esta definición no afecta al valor de `i` de nivel externo, que está oculto por el uso de su nombre para la variable local. Al valor de `i` global ahora solo se puede acceder a través del puntero `external_i`.

## <a name="see-also"></a>Vea también

[Especificadores de clase de almacenamiento para las declaraciones de nivel interno](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
