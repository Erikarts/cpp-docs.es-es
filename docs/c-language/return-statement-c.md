---
title: return (Instrucción) (C)
ms.date: 11/04/2016
helpviewer_keywords:
- ( ) parentheses in return statements
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
ms.openlocfilehash: c3975076ee65d267f3d278e20a7770e6750c06d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158390"
---
# <a name="return-statement-c"></a>return (Instrucción) (C)

La instrucción `return` finaliza la ejecución de una función y devuelve el control a la función de llamada. La ejecución se reanuda en la función de llamada, en el punto que sigue inmediatamente a la llamada. Una instrucción `return` puede devolver también un valor a la función de llamada. Consulte [Tipo de valor devuelto](../c-language/return-type.md) para obtener más información.

## <a name="syntax"></a>Sintaxis

*jump-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**return** *expression*<sub>opt</sub> **;**

El valor de *expression*, si existe, se devuelve a la función que llama. Si *expression* se omite, el valor devuelto de la función es indefinido. El valor de expression, si está presente, se evalúa y después se convierte al tipo devuelto por la función. Si la función se declaró con el tipo de valor devuelto `void`, una instrucción `return` que contiene una expresión genera una advertencia y la expresión no se evalúa.

Si no aparece ninguna instrucción `return` en una definición de función, el control vuelve automáticamente a la función de llamada después de que se ejecute la última instrucción de la función llamada. En este caso, el valor devuelto de la función llamada es indefinido. Si no se necesita un valor devuelto, declare la función para que tenga el tipo de valor devuelto `void`; de lo contrario, el tipo de valor devuelto predeterminado es `int`.

Muchos programadores usan paréntesis para incluir el argumento *expression* de la instrucción `return`. Sin embargo, C no necesita los paréntesis.

En este ejemplo se muestra la instrucción `return`:

```C
#include <limits.h>
#include <stdio.h>

void draw( int i, long long ll );
long long sq( int s );

int main()
{
    long long y;
    int x = INT_MAX;

    y = sq( x );
    draw( x, y );
    return x;
}

long long sq( int s )
{
    // Note that parentheses around the return expression
    // are allowed but not required here.
    return( s * (long long)s );
}

void draw( int i, long long ll )
{
    printf( "i = %d, ll = %lld\n", i, ll );
    return;
}
```

En este ejemplo, la función `main` llama a dos funciones: `sq` y `draw`. La función `sq` devuelve el valor de `x * x` a `main`, donde el valor devuelto se asigna a `y`. Los paréntesis que rodean la expresión return en `sq` se evalúan como parte de la expresión y la instrucción return no los necesita. Puesto que la expresión return se evalúa antes de que se convierta al tipo de valor devuelto, `sq` fuerza que el tipo de la expresión sea el tipo de valor devuelto con una conversión para evitar un posible desbordamiento con enteros, que podría provocar resultados inesperados. La función `draw` se declara como función `void`. Imprime los valores de sus parámetros y después la instrucción return vacía finaliza la función y no devuelve ningún valor. Un intento de asignar el valor devuelto de `draw` provocaría la emisión de un mensaje de diagnóstico. Después, la función `main` devuelve el valor de `x` al sistema operativo.

El resultado del ejemplo es similar a lo siguiente:

```Output
i = 2147483647, ll = 4611686014132420609
```

## <a name="see-also"></a>Vea también

[Instrucciones](../c-language/statements-c.md)
