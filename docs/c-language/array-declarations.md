---
title: Declaraciones de matrices
ms.date: 11/04/2016
helpviewer_keywords:
- multidimensional arrays
- declaring arrays
- arrays [C++], declaring
ms.assetid: 5f958b97-cef0-4058-bbc6-37c460aaed9b
ms.openlocfilehash: 4bc75e86601da77758490544cc5b02c485dcee46
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313550"
---
# <a name="array-declarations"></a>Declaraciones de matrices

Una "declaración de matriz” designa la matriz y especifica el tipo de sus elementos. También puede definir el número de elementos de la matriz. Una variable con tipo de matriz se considera un puntero al tipo de los elementos de la matriz.

## <a name="syntax"></a>Sintaxis

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *init-declarator-list*<sub>opt</sub> **;**

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-list*  **,**  *init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator* **=** *initializer*

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*: /\* Un declarador de función \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **[**  *constant-expression*<sub>opt</sub> **]**

Como *constant-expression* es opcional, la sintaxis tiene dos formas:

- La primera forma define una variable de matriz. El argumento *constant-expression* incluido entre corchetes especifica el número de elementos de la matriz. El elemento *constant-expression*, si existe, debe tener el tipo entero y un valor mayor que cero. Cada elemento tiene el tipo especificado por *type-specifier*, que puede ser de cualquier tipo excepto `void`. Un elemento de matriz no puede ser un tipo de función.

- La segunda forma declara una variable que se ha definido en otra parte. Omite el argumento *constant-expression* incluido entre corchetes, pero no los corchetes. Solo puede usar esta variante si previamente ha inicializado la matriz, la ha declarado como parámetro o la ha declarado como una referencia a una matriz definida explícitamente en otra parte del programa.

En ambas formas, *direct-declarator* designa la variable y puede modificar el tipo de la variable. Los corchetes ( **[ ]** ) incluidos detrás de *direct-declarator* modifican el declarador de un tipo de matriz.

Se pueden incluir calificadores de tipo en la declaración de un objeto de tipo de matriz, pero estos calificadores se aplican a los elementos en lugar de a la propia matriz.

Puede declarar una matriz de matrices (matriz “multidimensional”) incluyendo detrás del declarador de matriz una lista de expresiones constantes entre corchetes del modo siguiente:

> *type-specifier* *declarator* **[** *constant-expression* **]** **[** *constant-expression* **]** ...

Cada *constant-expression* entre corchetes define el número de elementos de una dimensión determinada: las matrices bidimensionales tienen dos expresiones entre corchetes, las matrices tridimensionales tienen tres, y así sucesivamente. Puede omitir la primera expresión constante si ha inicializado la matriz, la ha declarado como parámetro o la ha declarado como una referencia a una matriz definida explícitamente en otra parte del programa.

Puede definir matrices de punteros a distintos tipos de objetos mediante declaradores complejos, como se describe en [Interpretación de los declaradores más complejos](../c-language/interpreting-more-complex-declarators.md).

Las matrices se almacenan por fila. Por ejemplo, la siguiente matriz consta de dos filas con tres columnas cada una:

```C
char A[2][3];
```

Las tres columnas de la primera fila se almacenan primero, seguidas de las tres columnas de la segunda fila. Esto significa que el último subíndice es el que más rápidamente varía.

Para hacer referencia a un elemento individual de una matriz, utilice una expresión de subíndice, como se describe en [Operadores de postfijo](../c-language/postfix-operators.md).

## <a name="examples"></a>Ejemplos

En estos ejemplos se muestran declaraciones de matriz:

```C
float matrix[10][15];
```

La matriz bidimensional denominada `matrix` tiene 150 elementos, cada uno con un tipo **float**.

```C
struct {
    float x, y;
} complex[100];
```

Esta es una declaración de una matriz de estructuras. Esta matriz tiene 100 elementos; cada elemento es una estructura que contiene dos miembros.

```C
extern char *name[];
```

Esta instrucción declara el tipo y el nombre de una matriz de punteros a `char`. La definición real de `name` aparece en otra parte.

**Específicos de Microsoft**

El tipo entero necesario para contener el tamaño máximo de una matriz es el tamaño de **size_t**. Definido en el archivo de encabezado STDDEF.H, **size_t** es un `unsigned int` con el intervalo de 0x00000000 a 0x7CFFFFFF.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Declaradores y declaraciones de variables](../c-language/declarators-and-variable-declarations.md)
