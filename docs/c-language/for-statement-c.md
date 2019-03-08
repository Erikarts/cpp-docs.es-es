---
title: for (Instrucción) (C)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
ms.openlocfilehash: df00bcab2f9f9e51a6f37e19670b6cd240fa5cc4
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152838"
---
# <a name="for-statement-c"></a>for (Instrucción) (C)

La instrucción **for** permite repetir una instrucción o una instrucción compuesta un número especificado de veces. El cuerpo de una instrucción **for** se ejecuta cero o más veces hasta que una condición opcional sea False. Puede usar expresiones opcionales dentro de la instrucción **for** para inicializar y cambiar valores durante la ejecución de la instrucción **for**.

## <a name="syntax"></a>Sintaxis

*iteration-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**for** **(** *init-expression*<sub>opt</sub> **;** *cond-expression*<sub>opt</sub> **;** *loop-expression*<sub>opt</sub> **)** *statement*

La ejecución de una instrucción **for** continúa como sigue:

1. Se evalúa *init-expression*, si existe. Especifica la inicialización del bucle. No hay ninguna restricción sobre el tipo de *init-expression*.

1. Se evalúa *cond-expression*, si existe. Esta expresión debe tener un tipo aritmético o de puntero. Se evalúa antes de cada iteración. Se pueden producir tres resultados:

   - Si *cond-expression* es **true** (distinto de cero), *statement* se ejecuta; después *loop-expression*, si existe, se evalúa. *loop-expression* se evalúa después de cada iteración. No hay restricciones sobre su tipo. Los efectos secundarios se ejecutarán en orden. Entonces, comienza de nuevo el proceso con la evaluación de *cond-expression*.

   - Si se omite *cond-expression*, *cond-expression* se considera True, y la ejecución continúa exactamente como se ha descrito en el párrafo anterior. Una instrucción **for** sin un argumento *cond-expression* solo finaliza cuando se ejecuta una instrucción **break** o **return** dentro del cuerpo de la instrucción o cuando se ejecuta **goto** (para una instrucción con etiqueta fuera del cuerpo de la instrucción **for**).

   - Si *cond-expression* es **false** (0), la instrucción **for** finaliza y el control pasa a la siguiente instrucción del programa.

La instrucción **for** también puede finalizar cuando se ejecuta una instrucción **break**, **goto** o **return** dentro del cuerpo de la instrucción. Una instrucción **continue** en un bucle **for** hace que *loop-expression* se evalúe. Cuando se ejecuta una instrucción **break** dentro de un bucle **for**, *loop-expression* no se evalúa ni se ejecuta. Esta instrucción

```C
for( ; ; )
```

es la forma habitual de generar un bucle infinito del que solo se puede salir con una instrucción **break**, **goto** o **return**.

## <a name="example"></a>Ejemplo

En este ejemplo se ilustra la instrucción **for**:

```C
// c_for.c
int main()
{
   char* line = "H e  \tl\tlo World\0";
   int space = 0;
   int tab = 0;
   int i;
   int max = strlen(line);
   for (i = 0; i < max; i++ )
   {
      if ( line[i] == ' ' )
      {
          space++;
      }
      if ( line[i] == '\t' )
      {
          tab++;
      }
   }

   printf("Number of spaces: %i\n", space);
   printf("Number of tabs: %i\n", tab);
   return 0;
}
```

## <a name="output"></a>Salida

```Output
Number of spaces: 4
Number of tabs: 2
```

## <a name="see-also"></a>Vea también

[Instrucciones](../c-language/statements-c.md)
