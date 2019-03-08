---
title: Cuerpo de función
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
ms.openlocfilehash: c227640e45943fb57b1029a4f03329241d1d6b34
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56146871"
---
# <a name="function-body"></a>Cuerpo de función

Un *cuerpo de función* es una instrucción compuesta que contiene instrucciones que especifican lo que hace la función.

## <a name="syntax"></a>Sintaxis

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\* *attribute-seq* es específico de Microsoft \*/

*compound-statement*: /\* cuerpo de la función \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *declaration-list*<sub>opt</sub> *statement-list*<sub>opt</sub> **}**

Las variables declaradas en el cuerpo de función, o *variables locales*, tienen la clase de almacenamiento **auto** a menos que se especifique lo contrario. Cuando se llama a la función, se crea el almacenamiento para las variables locales y se realizan las inicializaciones locales. El control de ejecución pasa a la primera instrucción de *compound-statement* y continúa hasta que se ejecuta una instrucción **return** o hasta que se encuentra el final del cuerpo de función. A continuación, el control se devuelve al punto en el que se llamó a la función.

Una instrucción **return** que contiene una expresión debe ejecutarse si la función tiene que devolver un valor. El valor devuelto de una función es indefinido si no se ejecuta ninguna instrucción **return** o si la instrucción **return** no incluye una expresión.

## <a name="see-also"></a>Vea también

[Definiciones de función de C](../c-language/c-function-definitions.md)
