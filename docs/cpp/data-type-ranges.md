---
title: Intervalos de tipo de datos
ms.date: 05/07/2019
helpviewer_keywords:
- float keyword [C++]
- char keyword [C++]
- unsigned long
- __wchar_t keyword [C++]
- unsigned short int [C++]
- enum keyword [C++]
- unsigned char keyword [C++]
- integer data type [C++], data type ranges
- int data type
- data types [C++], ranges
- unsigned int [C++]
- short data type
- short int data
- signed types [C++], data type ranges
- long long keyword [C++]
- long double keyword [C++]
- double data type [C++], data type ranges
- signed short int [C++]
- unsigned short
- sized integer types
- signed int [C++]
- signed long int [C++]
- signed char keyword [C++]
- wchar_t keyword [C++]
- long keyword [C++]
- ranges [C++]
- unsigned types [C++], data type ranges
- floating-point numbers [C++]
- data type ranges
- ranges [C++], data types
- long int keyword [C++]
- unsigned long int [C++]
ms.assetid: 3691ceca-05fb-4b82-b1ae-5c4618cda91a
ms.openlocfilehash: 43eb5f34bc587e3ce86532c56d393da3e07c1b03
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301566"
---
# <a name="data-type-ranges"></a>Intervalos de tipo de datos

Los compiladores de Microsoft C++ 32 bits y 64 bits reconocen los tipos de la tabla más adelante en este artículo.

- `int` (`unsigned int`)

- `__int8` (`unsigned __int8`)

- `__int16` (`unsigned __int16`)

- `__int32` (`unsigned __int32`)

- `__int64` (`unsigned __int64`)

- `short` (`unsigned short`)

- `long` (`unsigned long`)

- `long` `long` (`unsigned long long`)

Si su nombre comienza con dos caracteres de subrayado (`__`), un tipo de datos no es estándar.

Los intervalos que se especifican en la tabla siguiente son inclusivo-inclusivo.

|Nombre de tipo|Bytes|Otros nombres|Intervalo de valores|
|---------------|-----------|-----------------|---------------------|
|**int**|4|**signed**|De -2.147.483.648 a 2.147.483.647|
|**unsigned int**|4|**unsigned**|De 0 a 4.294.967.295|
|**__int8**|1|**char**|De -128 a 127|
|**__int8 sin signo**|1|**unsigned char**|De 0 a 255|
|**__int16**|2|**Short**, **Short int**, **unsigned short int**|De -32 768 a 32 767|
|**__int16 sin signo**|2|**unsigned short**, **unsigned short int**|De 0 a 65.535|
|**__int32**|4|**signed**, **signed int**, **int**|De -2.147.483.648 a 2.147.483.647|
|**__int32 sin signo**|4|**unsigned**, **unsigned int**|De 0 a 4.294.967.295|
|**__int64**|8|**larga larga**, **con signo** largo largo|-9,223,372,036,854,775,808 a 9,223,372,036,854,775,807|
|**unsigned __int64**|8|**unsigned Long Long**|De 0 a 18.446.744.073.709.551.615|
|**bool**|1|ninguna|**false** o **true**|
|**char**|1|ninguna|de-128 a 127 de forma predeterminada<br /><br /> De 0 a 255 cuando se compila mediante [/J](../build/reference/j-default-char-type-is-unsigned.md)|
|**carácter con signo**|1|ninguna|De -128 a 127|
|**unsigned char**|1|ninguna|De 0 a 255|
|**short**|2|**Short int**, **signed Short int**|De -32 768 a 32 767|
|**unsigned short**|2|**unsigned short int**|De 0 a 65.535|
|**long**|4|**Long int**, **signed Long int**|De -2.147.483.648 a 2.147.483.647|
|**unsigned long**|4|**unsigned long int**|De 0 a 4.294.967.295|
|**long long**|8|ninguno (pero equivalente a **__int64**)|-9,223,372,036,854,775,808 a 9,223,372,036,854,775,807|
|**unsigned Long Long**|8|ninguno (pero equivalente a **__int64 sin signo**)|De 0 a 18.446.744.073.709.551.615|
|**enum**|varía|ninguna| |
|**float**|4|ninguna|3,4E +/- 38 (7 dígitos)|
|**double**|8|ninguna|1,7E +/- 308 (15 dígitos)|
|**long double**|igual que **doble**|ninguna|Igual que **doble**|
|**wchar_t**|2|**__wchar_t**|De 0 a 65.535|

Dependiendo de cómo se use, una variable de **__wchar_t** designa un tipo de caracteres anchos o un tipo de carácter multibyte. Utilice el prefijo `L` delante de un carácter o constante de cadena para designar la constante de tipo de carácter ancho.

**signed** y **unsigned** son modificadores que se pueden utilizar con cualquier tipo entero excepto **bool**. Tenga en cuenta que **Char**, **signed char**y **unsigned char** son tres tipos distintos para los fines de mecanismos como sobrecargas y plantillas.

Los **tipos int y** **unsigned int** tienen un tamaño de cuatro bytes. Sin embargo, el código portable no debe depender del tamaño de **int** porque el estándar del lenguaje permite que sea específico de la implementación.

C/C++ en Visual Studio también admite tipos enteros con tamaño. Para obtener más información, consulte [__int8, \___int16, \___int32, \___int64](../cpp/int8-int16-int32-int64.md) y [Límites de enteros](../cpp/integer-limits.md).

Para obtener más información sobre las restricciones de los tamaños de cada tipo, vea [tipos integrados](../cpp/fundamental-types-cpp.md).

El intervalo de tipos enumerados varía dependiendo del contexto del lenguaje y de las marcas del compilador especificadas. Para obtener más información, vea [Declaraciones de enumeración de C](../c-language/c-enumeration-declarations.md) y [Enumeraciones](../cpp/enumerations-cpp.md).

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Tipos integrados](../cpp/fundamental-types-cpp.md)