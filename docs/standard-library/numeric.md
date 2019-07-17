---
title: '&lt;numeric&gt;'
ms.date: 11/04/2016
f1_keywords:
- <numeric>
helpviewer_keywords:
- <numeric> header
ms.assetid: 6d6ccb94-48cc-479b-b4a9-bd9c78d4896a
ms.openlocfilehash: ce195742605c3dd2e127c84ac2f4e1e696c75bd0
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246695"
---
# <a name="ltnumericgt"></a>&lt;numeric&gt;

Define las funciones de plantilla contenedor que realizan algoritmos para el procesamiento numérico.

## <a name="requirements"></a>Requisitos

**Encabezado**: \<numeric >

**Espacio de nombres:** std

## <a name="remarks"></a>Comentarios

Los algoritmos numéricos se parecen a los algoritmos de la biblioteca estándar de C++ en [\<algorithm>](algorithm.md), y pueden funcionar en una variedad de estructuras de datos. Entre ellas se incluyen clases contenedoras de biblioteca estándar, por ejemplo [vector](../standard-library/vector-class.md) y [list](../standard-library/list-class.md), y estructuras de datos y matrices de elementos definidas por el programa que cumplen los requisitos de un algoritmo determinado. Para lograr este nivel de generalidad, los algoritmos acceden a los elementos de un contenedor y los recorren indirectamente mediante iteradores. Los algoritmos procesan los intervalos de iteradores que se suelen especificar por sus posiciones inicial o final. Los intervalos a los que se hace referencia deben ser válidos en el sentido de que todos los punteros de los intervalos se deben poder desreferenciar y, dentro de las secuencias de cada intervalo, se debe poder llegar a la última posición desde la primera mediante incrementos.

Los algoritmos extienden las acciones que admiten las operaciones y las funciones miembro de cada uno de los contenedores de la biblioteca estándar de C++ y permiten la interacción con diferentes tipos de objetos contenedores al mismo tiempo.

## <a name="members"></a>Miembros

### <a name="functions"></a>Funciones

|||
|-|-|
|[accumulate](../standard-library/numeric-functions.md#accumulate)|Calcula la suma de todos los elementos de un intervalo especificado, incluido algún valor inicial, mediante el cálculo de sumas parciales sucesivas, o calcula el resultado de los resultados parciales sucesivos obtenidos mediante el uso de una operación binaria determinada en lugar de la operación de suma.|
|[adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference)|Calcula las diferencias sucesivas entre cada elemento y su predecesor en un intervalo de entrada y pone los resultados en un intervalo de destino, o calcula el resultado de un procedimiento generalizado donde la operación de diferencia se reemplaza por otra operación binaria especificada.|
|[exclusive_scan](../standard-library/numeric-functions.md#exclusive_scan)||
|[Gcd](../standard-library/numeric-functions.md#gcd)||
|[inclusive_scan](../standard-library/numeric-functions.md#inclusive_scan)||
|[inner_product](../standard-library/numeric-functions.md#inner_product)|Calcula la suma del producto de elementos de dos intervalos y la agrega a un valor inicial especificado, o calcula el resultado de un procedimiento general donde las operaciones de suma y de producto se reemplazan con otras operaciones binarias especificadas.|
|[iota](../standard-library/numeric-functions.md#iota)|Almacena un valor inicial, empezando por el primer elemento y rellenando con incrementos sucesivos del valor (`value++`) en cada uno de los elementos del intervalo `[first, last)`.|
|[LCM](../standard-library/numeric-functions.md#lcm)||
|[partial_sum](../standard-library/numeric-functions.md#partial_sum)|Calcula una serie de sumas en un intervalo de entrada desde el primer elemento hasta el elemento *i*-ésimo y almacena el resultado de cada suma en el elemento *i*-ésimo de un intervalo de destino, o calcula el resultado de un procedimiento generalizado donde la operación de suma se reemplaza por otra operación binaria especificada.|
|[reducir](../standard-library/numeric-functions.md#reduce)||
|[transform_exclusive_scan](../standard-library/numeric-functions.md#transform_exclusive_scan)||
|[transform_inclusive_scan](../standard-library/numeric-functions.md#transform_inclusive_scan)||
|[transform_reduce](../standard-library/numeric-functions.md#transform_reduce)||

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
