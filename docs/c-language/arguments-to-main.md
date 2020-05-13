---
title: Argumentos de main
ms.date: 11/04/2016
ms.assetid: 39824fef-05ad-461d-ae82-49447dda8060
ms.openlocfilehash: 918be9d281f1cb12c27c6c2f5dd834e4af137179
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313563"
---
# <a name="arguments-to-main"></a>Argumentos de main

**ANSI 2.1.2.2.1** Semántica de argumentos para main

En Microsoft C, la función a la que se llama al inicio del programa se denomina **main**. No se declara ningún prototipo para **main**, y puede definirse con cero, dos o tres parámetros:

```
int main( void )
int main( int argc, char *argv[] )
int main( int argc, char *argv[], char *envp[] )
```

La tercera línea de arriba, donde **main** acepta tres parámetros, es una extensión de Microsoft para el estándar ANSI C. El tercer parámetro, **envp**, es una matriz de punteros a variables de entorno. La matriz de **envp** termina con un puntero nulo. Vea [La función main y la ejecución del programa](../c-language/main-function-and-program-execution.md) para obtener más información sobre **main** y **envp**.

La variable **argc** nunca contiene un valor negativo.

La matriz de cadenas finaliza con **argv[argc]** , que contiene un puntero nulo.

Todos los elementos de la matriz **argv** son punteros a cadenas.

Un programa invocado sin argumentos de línea de comandos recibirá un valor de uno para **argc**, porque el nombre del archivo ejecutable se coloca en **argv[0]** . (En las versiones de MS-DOS anteriores a la 3.0, el nombre del archivo ejecutable no está disponible. La letra "C" se coloca en **argv[0]** ). Las cadenas a las que señalan **argv[1]** mediante **argv[argc - 1]** representan parámetros de programa.

Los parámetros **argc** y **argv** son modificables y conservan los últimos valores almacenados entre el inicio del programa y su finalización.

## <a name="see-also"></a>Vea también

[Entorno](../c-language/environment.md)
