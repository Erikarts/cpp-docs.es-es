---
title: goto (Instrucción) (C++)
ms.date: 11/04/2016
f1_keywords:
- goto_cpp
helpviewer_keywords:
- goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
ms.openlocfilehash: aac308905a01a52a4ce5ee0fa3be03f2f33ac1cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153702"
---
# <a name="goto-statement-c"></a>goto (Instrucción) (C++)

El **goto** instrucción transfiere incondicionalmente el control a la instrucción etiquetada por el identificador especificado.

## <a name="syntax"></a>Sintaxis

```
goto identifier;
```

## <a name="remarks"></a>Comentarios

La instrucción con etiqueta designada por `identifier` debe estar en la función actual. Todos los nombres de `identifier` son miembros de un espacio de nombres interno y, por tanto, no interfieren con otros identificadores.

Una etiqueta de instrucción solo es significativa para un **goto** instrucción; de lo contrario, se omiten las etiquetas de instrucción. Las etiquetas no se pueden volver a declarar.

Un **goto** no se permite la instrucción para transferir el control a una ubicación que omite la inicialización de la variable que está en el ámbito en esa ubicación. El ejemplo siguiente genera C2362:

```cpp
int goto_fn(bool b)
{
    if (!b)
    {
        goto exit;  // C2362
    }
    else
    { /*...*/ }

    int error_code = 42;

exit:
    return error_code;
}
```

Es una buena programación de estilo que se usará el **salto**, **continuar**, y **devolver** instrucciones en lugar de la **goto** instrucción cada vez que es posible. Sin embargo, dado que el **salto** instrucción sale de un solo nivel de un bucle, es posible que deba usar un **goto** instrucción para salir de un bucle profundamente anidado.

Para obtener más información acerca de las etiquetas y la **goto** instrucción, consulte [instrucciones con etiquetas](../cpp/labeled-statements.md).

## <a name="example"></a>Ejemplo

En este ejemplo, un **goto** instrucción transfiere el control al punto con la etiqueta `stop` cuando `i` es igual a 3.

```cpp
// goto_statement.cpp
#include <stdio.h>
int main()
{
    int i, j;

    for ( i = 0; i < 10; i++ )
    {
        printf_s( "Outer loop executing. i = %d\n", i );
        for ( j = 0; j < 2; j++ )
        {
            printf_s( " Inner loop executing. j = %d\n", j );
            if ( i == 3 )
                goto stop;
        }
    }

    // This message does not print:
    printf_s( "Loop exited. i = %d\n", i );

    stop:
    printf_s( "Jumped to stop. i = %d\n", i );
}
```

```Output
Outer loop executing. i = 0
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 1
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 2
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 3
Inner loop executing. j = 0
Jumped to stop. i = 3
```

## <a name="see-also"></a>Vea también

[Instrucciones de salto](../cpp/jump-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
