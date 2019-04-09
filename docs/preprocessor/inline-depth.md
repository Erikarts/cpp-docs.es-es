---
title: inline_depth
ms.date: 11/04/2016
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
helpviewer_keywords:
- pragmas, inline_depth
- inline_depth pragma
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
ms.openlocfilehash: 18d772c8a9f6218ed3afaa385f214445bd0fe8e6
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039025"
---
# <a name="inlinedepth"></a>inline_depth
Especifica que ninguna función se inserte si se encuentra en una profundidad (en el gráfico de llamadas) mayor que la profundidad de búsqueda de la heurística de alineación *n*.

## <a name="syntax"></a>Sintaxis

```
#pragma inline_depth( [n] )
```

## <a name="remarks"></a>Comentarios

Esta directiva pragma controla la inserción de las funciones marcadas como [inline](../cpp/inline-functions-cpp.md) y [__inline](../cpp/inline-functions-cpp.md) o insertadas automáticamente bajo el `/Ob2` opción.

*n* puede ser un valor comprendido entre 0 y 255, donde 255 significa una profundidad ilimitada en el gráfico de llamadas y cero impide la expansión alineada.  Cuando *n* no se especifica, se usa el valor predeterminado (254).

El **inline_depth** pragma controla el número de veces que se puede expandir una serie de llamadas de función. Por ejemplo, si la profundidad alineada es cuatro y A llama a B y B después llama a C, las tres llamadas se expandirán alineadas. Sin embargo, si la expansión alineada más próxima es de dos, solo se expanden A y B, y C permanece como una llamada a función.

Para usar esta directiva pragma, debe establecer el `/Ob` opción del compilador en 1 o 2. La profundidad establecida mediante esta directiva pragma surte efecto en la primera llamada a función después de pragma.

La profundidad alineada puede reducirse durante la expansión, pero no se puede aumentar. Si la profundidad alineada es seis y durante la expansión, el preprocesador encuentra una **inline_depth** pragma con un valor de ocho, la profundidad permanece en seis.

El **inline_depth** pragma no surte ningún efecto en las funciones marcadas con `__forceinline`.

> [!NOTE]
> Las funciones recursivas pueden sustituirse alineadas con una profundidad máxima de 16 llamadas.

## <a name="see-also"></a>Vea también

[Directives pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[inline_recursion](../preprocessor/inline-recursion.md)