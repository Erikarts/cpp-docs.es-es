---
title: Aserción y mensajes proporcionados por el usuario (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- user-supplied messages [C++], run time
- user-supplied messages [C++], preprocessor time
- '#error%2C assert%2C static_assert [C++]'
- user-supplied messages [C++], compile time
ms.assetid: ebf7d885-61c8-4233-b0ae-1c9a38e0f385
ms.openlocfilehash: d76f0c2f7dc5a4202bff3f93e097a1c186f4601a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190565"
---
# <a name="assertion-and-user-supplied-messages-c"></a>Aserción y mensajes proporcionados por el usuario (C++)

El C++ lenguaje admite tres mecanismos de control de errores que le ayudarán a depurar la aplicación: la [Directiva #error](../preprocessor/hash-error-directive-c-cpp.md), la palabra clave [static_assert](../cpp/static-assert.md) y la [macro Assert, _assert _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) macro. Los tres mecanismos emiten mensajes de error y dos de ellos también prueban las aserciones de software. Una aserción de software especifica una condición que se espera que sea cierta (valor true) en un determinado punto del programa. Si se produce un error de aserción en tiempo de compilación, el compilador emite un mensaje de diagnóstico y un error de compilación. Si se produce un error de aserción en tiempo de ejecución, el sistema operativo emite un mensaje de diagnóstico y cierra la aplicación.

## <a name="remarks"></a>Observaciones

La duración de la aplicación se compone de una fase de preprocesamiento, una de compilación y una de tiempo de ejecución. Cada mecanismo de control de errores tiene acceso a la información de depuración disponible durante una de estas fases. Para depurar eficazmente, seleccione el mecanismo que proporciona la información adecuada sobre esa fase:

- La [directiva #error](../preprocessor/hash-error-directive-c-cpp.md) está en vigor en el tiempo de preprocesamiento. Emite incondicionalmente un mensaje definido por el usuario y hace que se produzca un error de compilación. El mensaje puede contener texto que se manipula mediante directivas de preprocesador, pero no se evalúa ninguna expresión resultante.

- La declaración [static_assert](../cpp/static-assert.md) está en vigor en tiempo de compilación. Prueba una aserción de software que está representada por una expresión de tipo entero definida por el usuario que se puede convertir en un valor booleano. Si la expresión se evalúa como cero (false), el compilador emite el mensaje definido por el usuario y se produce un error de compilación.

   La declaración `static_assert` resulta especialmente útil para depurar plantillas, porque los argumentos de plantilla se pueden incluir en la expresión especificada por el usuario.

- La [macro Assert, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) macro está en vigor en tiempo de ejecución. Evalúa una expresión definida por el usuario y, si el resultado es cero, el sistema emite un mensaje de diagnóstico y cierra la aplicación. Muchas otras macros, como[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) y _ASSERTE, se asemejan a esta macro pero emiten diferentes mensajes de diagnóstico definidos por el sistema o definidos por el usuario.

## <a name="see-also"></a>Consulte también

[#error (directiva) (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)<br/>
[assert (macro), _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR Macros](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)<br/>
[static_assert](../cpp/static-assert.md)<br/>
[_STATIC_ASSERT (Macro)](../c-runtime-library/reference/static-assert-macro.md)<br/>
[Templates](../cpp/templates-cpp.md) (Plantillas [C++])
