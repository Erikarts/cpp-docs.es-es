---
title: Información general sobre los declaradores
ms.date: 11/19/2018
helpviewer_keywords:
- declarators, about declarators
ms.assetid: 0f2e2312-80bd-4154-8345-718bd9ed2173
ms.openlocfilehash: e651b4422a159bf947e364c82cc4aac1b888d30d
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52177087"
---
# <a name="overview-of-declarators"></a>Información general sobre los declaradores

Los declaradores son los componentes de una declaración que especifican nombres de objetos o funciones. Los declaradores también especifican si el objeto con nombre es o no un objeto, puntero, referencia o matriz.  Aunque los declaradores no especifican el tipo base, modifican la información de tipo del tipo básico para especificar tipos derivados, como punteros, referencias y matrices.  Cuando se aplica a las funciones, el declarador funciona con el especificador de tipo para especificar completamente que el tipo de valor devuelto de una función es un objeto, puntero o referencia. (Los especificadores, se describe en [declaraciones y definiciones](declarations-and-definitions-cpp.md), transmiten propiedades tales como la clase de tipo y el almacenamiento. Modificadores, que se describe en esta sección y en [modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md), modifican los declaradores.) En la ilustración siguiente se muestra una declaración completa de `MyFunction` y se llama a los componentes de la declaración.

![Modificadores, especificadores y declaradores](../cpp/media/vc38qy1.gif "modificadores, especificadores y declaradores") <br/>
Especificadores, modificadores y declaradores

**Específicos de Microsoft**

La mayoría de las palabras clave extendidas de Microsoft se pueden utilizar como modificadores para formar tipos derivados; no son especificadores ni declaradores. (Consulte [modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md).)

**FIN de Específicos de Microsoft**

Los declaradores aparecen en la sintaxis de declaración después de una lista opcional de especificadores. Estos especificadores se describen en [declaraciones.](declarations-and-definitions-cpp.md) Una declaración puede contener varios declaradores, pero cada declarador declara un solo nombre.

En la declaración de ejemplo siguiente se muestra cómo se combinan especificadores y declaradores para formar una declaración completa:

```cpp
const char *pch, ch;
```

En la declaración anterior, las palabras clave **const** y **char** forman la lista de especificadores. Se muestran dos declaradores: `*pch` y `ch`.  Una declaración que declara varias entidades está formada por un especificador de tipo seguido de una lista separada por comas de declaradores, finalizada con un punto y coma.

**Declaradores de objetos simples**

El declarador de un objeto simple, como int o double, es simplemente su nombre, con paréntesis opcionales.

`int i; // declarator is i`

`int (i); // declarator is (i)`

**Declaradores de punteros, referencias y matrices**

Los operadores de puntero que se insertan delante del nombre hacen que el objeto sea un puntero o referencia.  El <strong>\*</strong> operador declara el nombre como puntero; el **&** operador lo declara como referencia.

```cpp
int *i; // declarator is *i
int **i; // declarator is **i;
int &i = x; // declaratory is &i
```

Anexar **const** o **volátil** proporcionan al puntero estas propiedades especiales.  El uso de estos especificadores en un declarador (frente al especificador de tipo) modifica las propiedades del puntero, no el objeto al que se señala:

```cpp
char *const cpc; // const pointer to char
const char *pcc; // pointer to const char
const char *const cpcc; // const pointer to const char
```

Puede encontrar más información en [punteros const y volatile](../cpp/const-and-volatile-pointers.md).

Un puntero a un miembro de una clase o struct se declara con el especificador de nombre anidado adecuado:

```cpp
int X::* pIntMember;
int ::X::* pIntMember; // the initial :: specifies X is in global scope
char Outer::Inner::* pIntMember; // pointer to char in a nested class
```

Los corchetes que rodean una expresión constante opcional después del nombre hacen que el objeto sea una matriz.  Los corchetes posteriores declaran dimensiones adicionales de la matriz.

```cpp
int i[5]; // array with five elements of type int numbered from 0 to 4
int i[]; // array of unknown size
char *s[4]; // array of pointers to char
int i[2][2]; // two dimensional array
```

**Declaradores de funciones**

Se usan paréntesis alrededor de la lista de argumentos, detrás del nombre, para declarar una función.  El ejemplo siguiente declara una función del tipo de valor devuelto **int** y tres argumentos de tipo **int**.

```cpp
int f(int a, int b, int c);
```

Los punteros y referencias a funciones se declaran mediante la anteposición del puntero u operador de referencia al nombre de función, como se muestra a continuación.  Se requieren paréntesis, normalmente opcionales, para distinguir un puntero a una función de una función que devuelve un puntero:

```cpp
int (*pf)(int); // pointer to function returning int
int *f(int i); // function returning pointer to int
int (&pf)(int); // reference to function
```

Los punteros a funciones miembro se distinguen por los especificadores de nombre anidados:

```cpp
int (X::* pmf)(); // pointer to member function of X returning int
int* (X::* pmf)(); // pointer to member function returning pointer to int
```

Vea también [punteros a miembros](../cpp/pointers-to-members.md).

**Funciones y objetos en la misma declaración**

Las funciones y objetos se pueden declarar en la misma declaración, como se indica a continuación:

```cpp
int i, *j, f(int k);  // int, pointer to int, function returning int
```

La sintaxis puede ser confusa en algunas circunstancias.  La siguiente declaración

```cpp
int* i, f(int k);  // pointer to int, function returning int (not int*)
```

puede ser similar a la declaración de un **int** puntero y una función que devuelve `int*`, pero no lo es.  Eso es porque la \* forma parte del declarador de `i`, que no forma parte del declarador de `f`.

**Lo que simplifica la sintaxis de declarador con typedef**

Sin embargo, es una técnica mejor, con un **typedef** o una combinación de paréntesis y **typedef** palabra clave. Considere, por ejemplo, una matriz de punteros a funciones:

```cpp
//  Function returning type int that takes one
//   argument of type char *.
typedef int (*PIFN)( char * );
//  Declare an array of 7 pointers to functions
//   returning int and taking one argument of type
//   char *.
PIFN pifnDispatchArray[7];
```

La declaración equivalente se puede escribir sin la **typedef** declaración, pero es tan complicado que las posibilidades de error superan cualquier ventaja:

```cpp
int ( *pifnDispatchArray[7] )( char * );
```

Para obtener más información sobre typedef, vea [alias y definiciones de tipo](aliases-and-typedefs-cpp.md).

Los punteros, referencias y matrices de un solo tipo base se pueden combinar en una sola declaración (separados por comas), como

```cpp
int a, *b, c[5], **d, &e=a;
```

**Sintaxis de declarador más compleja**

- Los declaradores de punteros, referencias, matrices y funciones se pueden combinar para especificar objetos tales como matrices de punteros a funciones, punteros a matrices, etc.

- La gramática recursiva siguiente describe la sintaxis completa de un declarador de puntero.

- `declarator` se define como:

  - identifier
  - nombre completo
  - declarador (lista de argumentos) [cv-qualfiers] [especificación de excepción]
  - declarador de [[-expresión-constante]]
  - declarador de puntero-(operador)
  - (declarador)

- y *puntero operador* es uno de:

  - \* [calificador CV]
  - & [calificador CV]:: especificador de nombre anidado \* [calificador CV]

Dado que un declarador puede contener declaradores, es posible construir los tipos derivados más complejos, como matrices de punteros, funciones que devuelven matrices de punteros a función, mediante las reglas anteriores.  Para formar cada paso de la construcción, comience con el identificador que representa el tipo de datos base y aplique la regla de sintaxis anterior con la expresión anterior como `declarator`.  El orden de aplicación de las reglas de sintaxis debe ser el inverso de como se indica la expresión en inglés.  Si aplica el *puntero operador* regla de sintaxis en una expresión de matriz o función, utilice paréntesis si desea que un puntero a la matriz o función, como se muestra en la última fila de la tabla siguiente.

En el ejemplo siguiente, se muestra la construcción de “puntero a matriz de 10 punteros a int”.

|Expresión verbal|Declarador|Regla de sintaxis aplicada|
|-----------------------|----------------|-------------------------|
||`i`|1|
|puntero(s) a|`*i`|5|
|matriz de 10|`(*i)[10]`|4|
|puntero a|`*((*i)[10])`|6 y después 5|

Cuando se utilizan varios modificadores de puntero, referencia, matriz o función, los declaradores pueden resultar bastante complicados.  El tema [interpretar declaradores más complejos](../c-language/interpreting-more-complex-declarators.md) describe cómo leer la sintaxis de declarador más compleja.  El tema es aplicable a C y C++, aunque en C++, en cualquier lugar del \* se utiliza para indicar un puntero, un nombre completo tal como MyClass::\* puede utilizarse para especificar un puntero a un miembro de una clase.