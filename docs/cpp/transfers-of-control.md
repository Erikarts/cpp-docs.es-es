---
title: Transferencias del control
ms.date: 11/04/2016
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
ms.openlocfilehash: 1fc487628f26dcac097109bc71fa960e501d0797
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266821"
---
# <a name="transfers-of-control"></a>Transferencias del control

Puede usar el **goto** instrucción o un **caso** etiquetar en un **cambiar** instrucción para especificar un programa que se bifurque más allá de un inicializador. Este código no es válido a menos que la declaración que contenga el inicializador esté en un bloque dentro del bloque en el que aparezca la instrucción de salto.

En el ejemplo siguiente se muestra un bucle que declara e inicializa los objetos `total`, `ch` y `i`. También hay un erróneos **goto** instrucción que transfiere el control más allá de un inicializador.

```cpp
// transfers_of_control.cpp
// compile with: /W1
// Read input until a nonnumeric character is entered.
int main()
{
   char MyArray[5] = {'2','2','a','c'};
   int i = 0;
   while( 1 )
   {
      int total = 0;

      char ch = MyArray[i++];

      if ( ch >= '0' && ch <= '9' )
      {
         goto Label1;

         int i = ch - '0';
      Label1:
         total += i;   // C4700: transfers past initialization of i.
      } // i would be destroyed here if  goto error were not present
   else
      // Break statement transfers control out of loop,
      //  destroying total and ch.
      break;
   }
}
```

En el ejemplo anterior, el **goto** instrucción intenta transferir el control más allá de la inicialización de `i`. Sin embargo, si se declarara `i` pero no se inicializara, la transferencia sería válida.

Los objetos `total` y `ch`, declarado en el bloque que actúa como el *instrucción* de la **mientras** instrucción, se destruyen cuando se sale de dicho bloque mediante el  **salto** instrucción.