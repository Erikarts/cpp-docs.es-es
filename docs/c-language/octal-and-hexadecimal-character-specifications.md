---
title: Especificaciones de caracteres octales y hexadecimales
ms.date: 11/04/2016
helpviewer_keywords:
- octal characters
- hexadecimal characters
ms.assetid: 9264f3ec-46b8-41a5-b21a-8f7ed0a11871
ms.openlocfilehash: df4d0666a220961f64238bf95dca9e0a08d4dae6
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343369"
---
# <a name="octal-and-hexadecimal-character-specifications"></a>Especificaciones de caracteres octales y hexadecimales

La secuencia **\\** <em>ooo</em> significa que se puede especificar un carácter del juego de caracteres ASCII como código de carácter octal de tres dígitos. El valor numérico del entero octal especifica el valor del carácter o carácter ancho deseado.

De igual forma, la secuencia **\x**<em>hhh</em> permite especificar un carácter ASCII como código de carácter hexadecimal. Por ejemplo, el carácter de retroceso ASCII se puede proporcionar como secuencia de escape de C normal ( **\b**) o se puede programar como **\010** (octal) o **\x008** (hexadecimal).

Puede usar solo los dígitos 0 a 7 en una secuencia de escape octal. Una secuencia de escape octal nunca pueden tener más de tres dígitos y finaliza con el primer carácter que no es un dígito octal. Aunque no es necesario utilizar los tres dígitos, se debe utilizar al menos uno. Por ejemplo, la representación octal es **\10** para el carácter de retroceso ASCII y **\101** para la letra A, como se indica en un gráfico ASCII.

De igual forma, se debe utilizar al menos un dígito para una secuencia de escape hexadecimal, pero se pueden omitir los dígitos segundo y tercero. Por lo tanto, la secuencia de escape hexadecimal para el carácter de retroceso se puede especificar como **\x8**, **\x08** o **\x008**.

El valor de la secuencia de escape octal o hexadecimal debe estar en el intervalo de valores representables para el tipo **unsigned char** para una constante de caracteres y el tipo `wchar_t` para una constante de caracteres anchos. Vea [Caracteres multibyte y anchos](../c-language/multibyte-and-wide-characters.md) para obtener información sobre constantes de caracteres anchos.

A diferencia de las constantes de escape octales, el número de dígitos hexadecimales en una secuencia de escape es ilimitado. Una secuencia de escape hexadecimal finaliza en el primer carácter que no es un dígito hexadecimal. Dado que los dígitos hexadecimales incluyen las letras **a** a **f**, se deben tomar precauciones para asegurarse de que la secuencia de escape finalice en el dígito previsto. Para evitar confusiones, se pueden colocar definiciones de carácter octal o hexadecimal en una definición de macro:

```
#define Bell '\x07'
```

Para los valores hexadecimales, se puede interrumpir la cadena para que se muestre claramente el valor correcto:

```
"\xabc"    /* one character  */
"\xab" "c" /* two characters */
```

## <a name="see-also"></a>Vea también

[Constantes de caracteres de C](../c-language/c-character-constants.md)
