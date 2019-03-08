---
title: Prototipos de función
ms.date: 11/04/2016
helpviewer_keywords:
- function prototypes
- function return types, function prototypes
- data types [C], function return types
- functions [C], return types
- prototypes [C++], function
ms.assetid: d152f8e6-971e-432c-93ca-5a91400653c2
ms.openlocfilehash: 2c75db3e1550927af57054a2cc1561d9df1567a4
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148809"
---
# <a name="function-prototypes"></a>Prototipos de función

Una declaración de función precede a la definición de función y especifica el nombre, el tipo devuelto, la clase de almacenamiento y otros atributos de una función. Para ser un prototipo, la declaración de función también debe establecer tipos e identificadores para los argumentos de la función.

## <a name="syntax"></a>Sintaxis

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *attribute-seq*<sub>opt</sub> *init-declarator-list*<sub>opt</sub> **;**

/\* *attribute-seq*<sub>opt</sub> es específico de Microsoft \*/

*declaration-specifiers*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-list*  **,**  *init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator* **=** *initializer*

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*: /\* Un declarador de función \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *parameter-type-list*  **)**  /\* Declarador de nuevo estilo \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *identifier-list*<sub>opt</sub> **)** /\* Declarador de estilo obsoleto \*/

El prototipo tiene la misma forma que la definición de función, excepto en que termina con un punto y coma inmediatamente después del paréntesis de cierre y, por consiguiente, no tiene ningún cuerpo. En cualquier caso, el tipo de valor devuelto debe coincidir con el tipo de valor devuelto especificado en la definición de función.

Los prototipos de función tienen los siguientes usos importantes:

- Establecen el tipo de valor devuelto para funciones que devuelven tipos diferentes de **int**. Aunque las funciones que devuelven valores **int** no requieren prototipos, estos son recomendables.

- Sin prototipos completos se realizan conversiones estándar, pero no se hace ningún intento de comprobar el tipo o el número de argumentos con el número de parámetros.

- Los prototipos se utilizan para inicializar punteros a funciones antes de que se definan esas funciones.

- La lista de parámetros se utiliza para comprobar la correspondencia de los argumentos de la llamada de función con los parámetros de la definición de función.

El tipo convertido de cada parámetro determina la interpretación de los argumentos que la llamada de función coloca en la pila. Un error de coincidencia de tipos entre un argumento y un parámetro puede provocar que los argumentos de la pila no se interpreten correctamente. Por ejemplo, en un equipo de 16 bits, si se pasa un puntero de 16 bits como argumento y, después, se declara como un parámetro **long**, los primeros 32 bits de la pila se interpretan como un parámetro **long**. Este error crea problemas no solo con el parámetro **long**, sino con cualquier parámetro que lo siga. Puede detectar errores de este tipo declarando prototipos de función completos para todas las funciones.

Un prototipo establece los atributos de una función para poder comprobar si en las llamadas a la función que preceden a la definición (o aparecen en otros archivos de código fuente) aparecen discordancias entre tipos de argumentos y tipos devueltos. Por ejemplo, si especifica el especificador de clase de almacenamiento **static** en un prototipo, también debe especificar la clase de almacenamiento **static** en la definición de función.

Las declaraciones de parámetro completas (`int a`) se pueden mezclar con declaradores abstractos (`int`) en la misma declaración. Por ejemplo, la siguiente declaración es válida:

```C
int add( int a, int );
```

El prototipo puede incluir tanto el tipo como el identificador de cada expresión que se pasa como argumento. Sin embargo, tales identificadores solo tienen ámbito hasta el final de la declaración. El prototipo también puede reflejar el hecho de que el número de argumentos es variable o que no se pasa ningún argumento. Sin esta lista es posible que las discordancias no se revelen, así que el compilador no puede generar mensajes de diagnóstico relacionados con ellos. Vea [Argumentos](../c-language/arguments.md) para ver más información sobre la comprobación de tipos.

El ámbito de prototipo en el compilador de Microsoft C es ahora compatible con ANSI cuando se compila con la opción del compilador **/Za**. Esto significa que, si declara una etiqueta **struct** o **union** dentro de un prototipo, la etiqueta se introduce en ese ámbito en lugar de en el ámbito global. Por ejemplo, al compilar con **/Za** para la compatibilidad con ANSI, nunca se puede llamar a esta función sin obtener un error de coincidencia de tipos:

```C
void func1( struct S * );
```

Para corregir el código, definir o declarar **struct** o **union** en el ámbito global antes del prototipo de función:

```C
struct S;
void func1( struct S * );
```

Bajo **/Ze**, la etiqueta continúa introduciéndose en el ámbito global.

## <a name="see-also"></a>Vea también

[Funciones](../c-language/functions-c.md)
