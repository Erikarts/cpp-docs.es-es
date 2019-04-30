---
title: restrict
ms.date: 02/09/2018
f1_keywords:
- restrict_cpp
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
ms.openlocfilehash: 40c1c05ca72f639829f2d3658497b0e9f3199640
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403378"
---
# <a name="restrict"></a>restrict

**Específicos de Microsoft**

Cuando se aplica a una declaración de función o una definición que devuelve un tipo de puntero, **restringir** indica al compilador que la función devuelve un objeto que no es *con alias*, es decir, al que hace referencia por ningún otro punteros. Esto permite que el compilador realice optimizaciones adicionales.

## <a name="syntax"></a>Sintaxis

> **__declspec(restrict)** *pointer_return_type* *function*();

## <a name="remarks"></a>Comentarios

El compilador propaga **__declspec (Restrict)**. Por ejemplo, CRT `malloc` función tiene un **__declspec (Restrict)** decoración y, por lo tanto, el compilador supone que punteros inicializados en ubicaciones de memoria por `malloc` también no son proporcionado por él previamente punteros existentes.

El compilador no comprueba que el puntero devuelto no es realmente un alias. Es responsabilidad del desarrollador para asegurarse de que el programa no alias no un puntero marcado con el **restringir __declspec** modificador.

Para conocer la semántica similar en las variables, consulte [__restrict](../cpp/extension-restrict.md).

Para la otra anotación que se aplica a los alias dentro de una función, vea [__declspec (noalias)](../cpp/noalias.md).

Para obtener información sobre la **restringir** palabra clave que forma parte de C++ AMP, consulte [restringir (C++ AMP)](../cpp/restrict-cpp-amp.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra el uso de **__declspec (Restrict)**.

Cuando **__declspec (Restrict)** se aplica a una función que devuelve un puntero, esto indica al compilador que la memoria que apunta el valor devuelto no es un alias. En este ejemplo, los punteros `mempool` y `memptr` son globales, por lo que el compilador no puede estar seguro de que la memoria que hacen referencia no es un alias. Sin embargo, se utilizan dentro de `ma` y su llamador `init` de manera que devuelve la memoria que no es lo contrario, al que hace referencia el programa, por lo que **__decslpec(restrict)** se usa para el optimizador. Esto es similar a cómo los encabezados de CRT decoran las funciones de asignación como `malloc` utilizando **__declspec (Restrict)** para indicar que siempre devuelven memoria que no se puede tener un alias existente punteros.

```C
// declspec_restrict.c
// Compile with: cl /W4 declspec_restrict.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

__declspec(restrict) float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

__declspec(restrict) float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1f/k++;
    return a;
}

void multiply(float * a, float * b, float * c)
{
    int i, j, k;

    for (j=0; j<P; j++)
        for (i=0; i<M; i++)
            for (k=0; k<N; k++)
                c[i * P + j] =
                          a[i * N + k] *
                          b[k * P + j];
}

int main()
{
    float * a, * b, * c;

    mempool = (float *) malloc(sizeof(float) * (M*N + N*P + M*P));

    if (!mempool)
    {
        puts("ERROR: Malloc returned null");
        exit(1);
    }

    memptr = mempool;
    a = init(M, N);
    b = init(N, P);
    c = init(M, P);

    multiply(a, b, c);
}
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[__declspec](../cpp/declspec.md)<br/>
[__declspec(noalias)](../cpp/noalias.md)
