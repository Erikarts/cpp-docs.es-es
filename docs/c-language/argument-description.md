---
title: Descripción de los argumentos
ms.date: 11/04/2016
helpviewer_keywords:
- envp argument
- main function, syntax
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 91c2cbe3-9aca-4277-afa1-6137eb8fb704
ms.openlocfilehash: 88d477c874d62800c47bb03220246cb3f0999724
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492504"
---
# <a name="argument-description"></a>Descripción de los argumentos

El parámetro `argc` en las funciones **main** y **wmain** es un entero que especifica el número de argumentos que se pasan al programa desde la línea de comandos. Como el nombre del programa se considera un argumento, el valor de `argc` es uno, por lo menos.

## <a name="remarks"></a>Comentarios

El parámetro `argv` es una matriz de punteros a cadenas finalizadas en null que representan los argumentos del programa. Cada elemento de la matriz señala a una representación de cadena de un argumento que se pasa a **main** o a **wmain**. (Para obtener información sobre matrices, vea [Declaraciones de matriz](../c-language/array-declarations.md)). El parámetro `argv` se puede declarar como una matriz de punteros a tipo `char` (`char *argv[]`) o como un puntero para punteros a tipo `char` (`char **argv`). En el caso de **wmain**, el parámetro `argv` se puede declarar como una matriz de punteros a tipo `wchar_t` (`wchar_t *argv[]`) o como un puntero para punteros a tipo`wchar_t` (`wchar_t **argv`).

Por convención, `argv` **[0]** es el comando con el que se invoca el programa.  Sin embargo, es posible generar un proceso usando [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) y, si utiliza el primero y segundo argumentos (`lpApplicationName` ay `lpCommandLine`), `argv` **[0]** puede no ser el nombre ejecutable; utilice [GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) para recuperar el nombre ejecutable.

El último puntero (`argv[argc]`) es **NULL**. (Vea [getenv](../c-runtime-library/reference/getenv-wgetenv.md) en la *Referencia de la biblioteca en tiempo de ejecución* si desea un método alternativo para obtener información de variables de entorno).

**Específicos de Microsoft**

El parámetro `envp` es un puntero a una matriz de cadenas finalizadas en null que representan los valores establecidos en las variables de entorno del usuario. El parámetro `envp` se puede declarar como una matriz de punteros a `char` (`char *envp[]`) o como un puntero para punteros a `char` (`char **envp`). En una función **wmain**, el parámetro `envp` se puede declarar como una matriz de punteros a `wchar_t` (`wchar_t *envp[]`) o como un puntero para punteros a `wchar_t` (`wchar_t **envp`). El final de la matriz se indica mediante un \*puntero **NULL**. Observe que el bloque de entorno que se pasa a **main** o a **wmain** es una copia "inmovilizada" del entorno actual. Si se cambia posteriormente el entorno mediante una llamada a _**putenv** o `_wputenv`, el entorno actual (devuelto por `getenv`/`_wgetenv` y las variables `_environ` o `_wenviron`) cambiará, pero el bloque señalado por `envp` no cambiará. El parámetro `envp` es compatible con ANSI en C, pero no en C++.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Función main y ejecución del programa](../c-language/main-function-and-program-execution.md)
