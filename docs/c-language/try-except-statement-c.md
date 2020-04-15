---
title: try-except (Instrucción) (C)
ms.date: 11/04/2016
helpviewer_keywords:
- try-except keyword [C]
- structured exception handling, try-except
- try-catch keyword [C]
- __try keyword [C]
- __except keyword [C]
- __except keyword [C], in try-except
- try-catch keyword [C], try-except keyword [C]
ms.assetid: f76db9d1-fc78-417f-b71f-18e545fc01c3
ms.openlocfilehash: 2ca5299a5ab20b8985a520f25bb654ead0c25e2b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349737"
---
# <a name="try-except-statement-c"></a>try-except (Instrucción) (C)

**Microsoft Specific**

La instrucción **try-except** es una extensión de Microsoft para el lenguaje C que permite a las aplicaciones obtener el control de un programa cuando se producen los eventos que normalmente finalizan la ejecución de un programa. Estos eventos se denominan excepciones y el mecanismo que se encarga de las excepciones se denomina control de excepciones estructurado.

Las excepciones pueden estar basadas en hardware o en software. Aunque las aplicaciones no pueden recuperarse completamente de las excepciones de hardware o software, el control de excepciones estructurado permite mostrar información de error y capturar el estado interno de la aplicación para ayudar a diagnosticar el problema. Esto es especialmente útil en el caso de problemas intermitentes que no se pueden reproducir fácilmente.

## <a name="syntax"></a>Sintaxis

*try-except-statement*: **__try**  *compound-statement*

**__except (expresión***expression***)***declaración compuesta*      

La instrucción compuesta detrás de la cláusula `__try` es la sección protegida. La instrucción compuesta detrás de la cláusula `__except` es el controlador de excepción. El controlador especifica un conjunto de acciones que se realizarán si se inicia una excepción durante la ejecución de la sección protegida. La ejecución continúa de la siguiente manera:

1. Se ejecuta la sección protegida.

1. Si no se produce ninguna excepción durante la ejecución de la sección protegida, continúa la ejecución de la instrucción después de la cláusula `__except`.

1. Si se produce una excepción durante la ejecución de la sección protegida o en cualquier rutina a la que llame la sección protegida, se evalúa la expresión `__except` y el valor devuelto determina cómo se controla la excepción. Existen tres valores:

   `EXCEPTION_CONTINUE_SEARCH` La excepción no se reconoce. La búsqueda de un controlador continúa hacia la parte superior de la pila, primero con las instrucciones **try-except** contenedoras y, después, con los controladores siguientes que tengan mayor prioridad.

   `EXCEPTION_CONTINUE_EXECUTION` La excepción se reconoce pero se descarta. La ejecución continúa en el punto donde se ha producido la excepción.

   `EXCEPTION_EXECUTE_HANDLER` La excepción se reconoce. El control se transfiere al controlador de excepciones ejecutando la instrucción compuesta `__except`, después la ejecución continúa en el punto donde se produjo la excepción.

Dado que la expresión `__except` se evalúa como expresión de C, se limita a un valor único: el operador de expresión condicional u operador de coma. Si se requiere un mayor procesamiento, la expresión puede llamar a una rutina que devuelva uno de los tres valores enumerados anteriormente.

> [!NOTE]
> El control estructurado de excepciones funciona con archivos de código fuente de C y C++. Sin embargo, no está diseñado específicamente para C++. Para asegurarse de que el código será más portable, use el control de excepciones de C++. Además, el mecanismo de control de excepciones de C++ es mucho más flexible, ya que puede controlar excepciones de cualquier tipo.

> [!NOTE]
> Para los programas de C++, se debe usar el control de excepciones de C++ en lugar del control estructurado de excepciones. Para obtener más información, vea [Control de excepciones](../cpp/exception-handling-in-visual-cpp.md) en la *Referencia del lenguaje C++*.

Cada rutina de una aplicación puede tener su propio controlador de excepciones. La expresión `__except` se ejecuta en el ámbito del cuerpo de `__try`. Esto significa que tiene acceso a cualquier variable local declarada allí.

La palabra clave `__leave` es válida dentro de un bloque de instrucciones **try-except**. El efecto de `__leave` es saltar al final del bloque **try-except**. La ejecución se reanuda después del final del controlador de excepciones. Aunque se puede utilizar una instrucción `goto` para lograr el mismo resultado, una instrucción `goto` produce el desenredado de la pila. La instrucción `__leave` es más eficaz porque no produce el desenredado de la pila.

La salida de una instrucción **try-except** mediante el uso de la función en tiempo de ejecución `longjmp` se considera una finalización anómala. No es válido saltar dentro de una instrucción `__try`, pero sí fuera. No se llama al controlador de excepciones si un proceso se elimina en medio de la ejecución de una instrucción **try-except**.

## <a name="example"></a>Ejemplo

A continuación se muestra un ejemplo de un controlador de excepciones y un controlador de terminación. Vea [try-finally (Instrucción)](../c-language/try-finally-statement-c.md) para obtener más información sobre los controladores de terminación.

```
.
.
.
puts("hello");
__try{
   puts("in try");
   __try{
      puts("in try");
      RAISE_AN_EXCEPTION();
   }__finally{
      puts("in finally");
   }
}__except( puts("in filter"), EXCEPTION_EXECUTE_HANDLER ){
   puts("in except");
}
puts("world");
```

Este es el resultado del ejemplo, con el comentario agregado a la derecha:

```
hello
in try              /* fall into try                     */
in try              /* fall into nested try                */
in filter           /* execute filter; returns 1 so accept  */
in finally          /* unwind nested finally                */
in except           /* transfer control to selected handler */
world               /* flow out of handler                  */
```

**END Microsoft Specific**

## <a name="see-also"></a>Consulte también

[try-except (Instrucción)](../cpp/try-except-statement.md)
