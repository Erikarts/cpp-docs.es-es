---
title: Error del compilador C3850
ms.date: 09/05/2018
f1_keywords:
- C3850
helpviewer_keywords:
- C3850
ms.assetid: 028f3a37-f3ad-4ebc-9168-3cdea47524d4
ms.openlocfilehash: 5de7994e8bf46105e94271ab29bf9e27f1da3e76
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165573"
---
# <a name="compiler-error-c3850"></a>Error del compilador C3850

> '*Char*': un nombre de carácter universal especifica un carácter no válido

## <a name="remarks"></a>Observaciones

Los caracteres representados como nombres de carácter universal deben representar puntos de código Unicode válidos en el rango de 0 a 10FFFF. Un nombre de carácter universal no puede contener un valor en el rango suplente Unicode, de D800 a DFFF ni un par suplente codificado. El compilador genera el par suplente de un punto de código válido automáticamente.

En el código compilado como C, un nombre de carácter universal no puede representar un carácter en el intervalo 0000-009F, ambos incluidos, con las excepciones de 0024 (' $ '), 0040 ('\@') y 0060 (' ' ').

En el código compilado como C++, un nombre de carácter universal puede usar cualquier punto de código Unicode válido en una cadena o un literal de carácter. Fuera de un literal, un nombre de carácter universal no puede representar un carácter de control en los rangos de 0000 a 001F o de 007F a 009F, ambos inclusivos, ni un miembro del juego de caracteres de origen básico.  Para obtener más información, vea [Character Sets](../../cpp/character-sets.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera el error C3850 y se muestra cómo corregirlo:

```cpp
// C3850.cpp
int main() {
   int \u0019 = 0;   // C3850, not in allowed range for an identifier
   const wchar_t * wstr_bad  = L"\UD840DC8A"; // C3850, UCN is surrogate pair
   const wchar_t * wstr_good = L"\U0002008A"; // Okay, UCN is valid code point
}
```
