---
title: Control de excepciones en Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: a155d56cc234c11534f5456ef92ea913e094f1a8
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627285"
---
# <a name="exception-handling-in-visual-c"></a>Control de excepciones en Visual C++

Una excepción es una condición de error, posiblemente fuera del control del programa, que evita que el programa continúe a lo largo de su ruta normal de ejecución. Determinadas operaciones, incluidas la creación de objetos, la entrada/salida de archivo y las llamadas de función realizadas desde otros módulos, son posibles orígenes de excepciones aunque el programa se ejecute correctamente. Un código robusto prevé y controla las excepciones.

Para detectar errores lógicos dentro de un programa o un módulo, utilice aserciones en lugar de excepciones (vea [utilizar aserciones](/visualstudio/debugger/c-cpp-assertions)).

Visual C++ admite tres tipos de control de excepciones:

- [Control de excepciones de C++](../cpp/cpp-exception-handling.md)

   Para la mayoría de los programas de C++, se debe utilizar el control de excepciones de C++, que tiene seguridad de tipos y garantiza que se llame a los destructores de objeto durante el desenredo de la pila.

- [Control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md)

   Windows suministra su propio mecanismo de excepción, denominado SEH. No se recomienda para la programación con C++ o con MFC. Utilice SEH sólo en programas de C que no son de MFC.

- [Excepciones de MFC](../mfc/exception-handling-in-mfc.md)

   Desde la versión 3.0, MFC ha utilizado las excepciones de C++ pero sigue admitiendo sus anteriores macros de control de excepciones, que son similares a las excepciones de C++ en su forma. Aunque estas macros no son recomendables para nueva programación, todavía se siguen admitiendo por razones de compatibilidad con versiones anteriores. En los programas que ya utilizan las macros, también puede utilizar libremente las excepciones de C++. Durante el preprocesamiento, las macros evalúan las palabras clave de control de excepciones definidas en la implementación de Visual C++ del lenguaje C++ a partir de la versión 2.0 de Visual C++. Puede dejar las macros de excepciones existentes en su sitio mientras empieza a utilizar las excepciones de C++.

Utilice la [/EH](../build/reference/eh-exception-handling-model.md) opción del compilador para especificar el tipo de control de excepciones para usar en un proyecto; Control de excepciones de C++ es el valor predeterminado. No combine los mecanismos de control de errores; por ejemplo, no use las excepciones de C++ con control de excepciones estructurado. Si usa el control de excepciones de C++, el código será más portátil y podrá controlar todo tipo de excepciones. Para obtener más información sobre los inconvenientes de control de excepciones estructurado, consulte [Structured Exception Handling](../cpp/structured-exception-handling-c-cpp.md). Para obtener más información sobre la combinación de macros de MFC y excepciones de C++, consulte [Excepciones: Uso de macros de MFC y excepciones de C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

Para obtener información sobre cómo controlar las excepciones en aplicaciones de CLR, vea [control de excepciones (C++ / c++ / CLI y c++ / CX)](../windows/exception-handling-cpp-component-extensions.md).

Para obtener información sobre el control de excepciones en x64 procesadores, consulte [x64 control de excepciones](../build/exception-handling-x64.md).

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)