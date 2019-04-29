---
title: '&lt;regex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <regex>
helpviewer_keywords:
- regex header
ms.assetid: 5dd4ef74-6063-4dbc-b692-1960bb736f0b
ms.openlocfilehash: 0a4728008130119ed9a01334efb2fea2a4ac0639
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368986"
---
# <a name="ltregexgt"></a>&lt;regex&gt;

Define una clase de plantilla para analizar [Expresiones regulares (C++)](../standard-library/regular-expressions-cpp.md) y varias clases de plantilla y funciones para buscar texto que coincida con un objeto de expresión regular.

## <a name="syntax"></a>Sintaxis

```cpp
#include <regex>
```

## <a name="remarks"></a>Comentarios

Para crear un objeto de expresión regular, use la clase de plantilla [basic_regex](../standard-library/basic-regex-class.md) o una de sus especializaciones, [regex](../standard-library/regex-typedefs.md#regex) y [wregex](../standard-library/regex-typedefs.md#wregex), junto con las marcas de sintaxis de tipo [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

Para buscar texto que coincida con un objeto de expresión regular, utilice las funciones de plantilla [regex_match](../standard-library/regex-functions.md#regex_match) y [regex_search](../standard-library/regex-functions.md#regex_search), junto con las marcas de coincidencia de tipo [regex_constants::match_ flag_type](../standard-library/regex-constants-class.md#match_flag_type). Estas funciones devuelven resultados mediante el uso de la clase de plantilla [match_results (Clase)](../standard-library/match-results-class.md) y sus especializaciones, [cmatch](../standard-library/regex-typedefs.md#cmatch), [wcmatch](../standard-library/regex-typedefs.md#wcmatch), [smatch](../standard-library/regex-typedefs.md#smatch) y [wsmatch](../standard-library/regex-typedefs.md#wsmatch), junto con la clase de plantilla [sub_match (Clase)](../standard-library/sub-match-class.md) y sus especializaciones, [csub_match](../standard-library/regex-typedefs.md#csub_match), [wcsub_match](../standard-library/regex-typedefs.md#wcsub_match), [ssub_match](../standard-library/regex-typedefs.md#ssub_match) y [wssub_match](../standard-library/regex-typedefs.md#wssub_match).

Para reemplazar el texto que coincide con un objeto de expresión regular, use la función de plantilla [regex_replace](../standard-library/regex-functions.md#regex_replace), junto con las marcas de coincidencia de tipo [regex_constants:: match_flag_type](../standard-library/regex-constants-class.md#match_flag_type).

Para procesar una iteración en varias coincidencias de un objeto de expresión regular, use las clases de plantilla [regex_iterator (Clase)](../standard-library/regex-iterator-class.md) y [regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md) o una de sus especializaciones, [cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator), [sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator), [wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator), [wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator), [cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator), [sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator), [wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator) o [wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator), junto con las marcas de coincidencia de tipo [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#match_flag_type).

Para modificar los detalles de la gramática de expresiones regulares, escriba una clase que implemente los rasgos de expresiones regulares.

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[basic_regex](../standard-library/basic-regex-class.md)|Contiene una expresión regular.|
|[match_results](../standard-library/match-results-class.md)|Contiene una secuencia de subcoincidencias.|
|[regex_constants](../standard-library/regex-constants-class.md)|Contiene constantes ordenadas.|
|[regex_error](../standard-library/regex-error-class.md)|Notifica la existencia de una expresión regular no válida.|
|[regex_iterator](../standard-library/regex-iterator-class.md)|Procesa una iteración por los resultados de la coincidencia.|
|[regex_traits](../standard-library/regex-traits-class.md)|Describe las características de los elementos para buscar coincidencias.|
|[regex_traits\<char>](../standard-library/regex-traits-char-class.md)|Describe las características de **char** para la coincidencia.|
|[regex_traits<wchar_t>](../standard-library/regex-traits-wchar-t-class.md)|Describe las características de **wchar_t** para la coincidencia.|
|[regex_token_iterator](../standard-library/regex-token-iterator-class.md)|Procesa una iteración en las subcoincidencias.|
|[sub_match](../standard-library/sub-match-class.md)|Describe a una subcoincidencia.|

### <a name="type-definitions"></a>Definiciones de tipos

|||
|-|-|
|[cmatch](../standard-library/regex-typedefs.md#cmatch)|Definición de tipo para **char** `match_results`.|
|[cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator)|Definición de tipo para **char** `regex_iterator`.|
|[cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator)|Definición de tipo para **char** `regex_token_iterator`.|
|[csub_match](../standard-library/regex-typedefs.md#csub_match)|Definición de tipo para **char** `sub_match`.|
|[regex](../standard-library/regex-typedefs.md#regex)|Definición de tipo para **char** `basic_regex`.|
|[smatch](../standard-library/regex-typedefs.md#smatch)|Definición de tipo de `string` `match_results`.|
|[sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator)|Definición de tipo de `string` `regex_iterator`.|
|[sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator)|Definición de tipo de `string` `regex_token_iterator`.|
|[ssub_match](../standard-library/regex-typedefs.md#ssub_match)|Definición de tipo de `string` `sub_match`.|
|[wcmatch](../standard-library/regex-typedefs.md#wcmatch)|Definición de tipo para **wchar_t** `match_results`.|
|[wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator)|Definición de tipo para **wchar_t** `regex_iterator`.|
|[wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator)|Definición de tipo para **wchar_t** `regex_token_iterator`.|
|[wcsub_match](../standard-library/regex-typedefs.md#wcsub_match)|Definición de tipo para **wchar_t** `sub_match`.|
|[wregex](../standard-library/regex-typedefs.md#wregex)|Definición de tipo para **wchar_t** `basic_regex`.|
|[wsmatch](../standard-library/regex-typedefs.md#wsmatch)|Definición de tipo de `wstring` `match_results`.|
|[wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator)|Definición de tipo de `wstring` `regex_iterator`.|
|[wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator)|Definición de tipo de `wstring` `regex_token_iterator`.|
|[wssub_match](../standard-library/regex-typedefs.md#wssub_match)|Definición de tipo de `wstring` `sub_match`.|

### <a name="functions"></a>Funciones

|Función|Descripción|
|-|-|
|[regex_match](../standard-library/regex-functions.md#regex_match)|Coincide por completo con una expresión regular.|
|[regex_replace](../standard-library/regex-functions.md#regex_replace)|Reemplaza las expresiones regulares que coincidan.|
|[regex_search](../standard-library/regex-functions.md#regex_search)|Busca una coincidencia con la expresión regular.|
|[swap](../standard-library/regex-functions.md#swap)|Intercambia los objetos `basic_regex` o `match_results`.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator==](../standard-library/regex-operators.md#op_eq_eq)|Comparación de varios objetos, igual.|
|[operator!=](../standard-library/regex-operators.md#op_neq)|Comparación de desigualdad de varios objetos.|
|[operator<](../standard-library/regex-operators.md#op_lt)|Comparación de varios objetos, no igual.|
|[operator\<=](../standard-library/regex-operators.md#op_gt_eq)|Comparación de varios objetos, menor o igual que.|
|[operator>](../standard-library/regex-operators.md#op_gt)|Comparación de varios objetos, mayor que.|
|[operator>=](../standard-library/regex-operators.md#op_gt_eq)|Comparación de varios objetos, mayor o igual que.|
|[operator<<](../standard-library/regex-operators.md#op_lt_lt)|Inserta un `sub_match` en una secuencia.|

## <a name="see-also"></a>Vea también

[Expresiones regulares (C++)](../standard-library/regular-expressions-cpp.md)<br/>
[regex_constants (Clase)](../standard-library/regex-constants-class.md)<br/>
[regex_error (Clase)](../standard-library/regex-error-class.md)<br/>
[Funciones de \<regex>](../standard-library/regex-functions.md)<br/>
[regex_iterator (Clase)](../standard-library/regex-iterator-class.md)<br/>
[Operadores de \<regex>](../standard-library/regex-operators.md)<br/>
[regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits (Clase)](../standard-library/regex-traits-class.md)<br/>
[Definiciones de tipo \<regex>](../standard-library/regex-typedefs.md)<br/>
