---
title: try-except (Instrucción)
ms.date: 10/09/2018
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- EXCEPTION_CONTINUE_SEARCH
- _exception_info
- __except
- _except
- EXCEPTION_CONTINUE_EXECUTION
- _exception_code
- __except_cpp
- _exception_info_cpp
- EXCEPTION_EXECUTE_HANDLER
- _abnormal_termination
helpviewer_keywords:
- __try keyword [C++]
- EXCEPTION_CONTINUE_EXECUTION macro
- EXCEPTION_CONTINUE_SEARCH macro
- EXCEPTION_EXECUTE_HANDLER macro
- GetExceptionCode function
- try-catch keyword [C++], try-except keyword [C++]
- _exception_code keyword [C++]
- try-except keyword [C++]
- _exception_info keyword [C++]
- _abnormal_termination keyword [C++]
ms.assetid: 30d60071-ea49-4bfb-a8e6-7a420de66381
ms.openlocfilehash: 400c831eec1c570f26dfc010b4e4c61e7d21b1c4
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326659"
---
# <a name="try-except-statement"></a>try-except (Instrucción)

**Específicos de Microsoft**

El **intente-excepto** instrucción es una extensión de Microsoft C y lenguajes C++ que admite el control estructurado de excepciones.

## <a name="syntax"></a>Sintaxis

> **\_\_try**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;código protegido<br/>
> }<br/>
> **\_\_excepto** ( *expresión* )<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;código del controlador de excepción<br/>
> }<br/>

## <a name="remarks"></a>Comentarios

El **intente-excepto** instrucción es una extensión de Microsoft C y lenguajes C++ que permite a las aplicaciones de destino obtener controlan cuando se producen los eventos que normalmente finalizan la ejecución del programa. Estos eventos se denominan *excepciones*, y el mecanismo que se ocupa de las excepciones se denomina *control estructurado de excepciones* (SEH).

Para obtener información relacionada, consulte el [instrucción try-finally](../cpp/try-finally-statement.md).

Las excepciones pueden estar basadas en hardware o software. Aunque las aplicaciones no pueden recuperarse completamente de las excepciones de hardware o software, el control de excepciones estructurado permite mostrar información de error y capturar el estado interno de la aplicación para ayudar a diagnosticar el problema. Esto es especialmente útil en el caso de problemas intermitentes que no se pueden reproducir fácilmente.

> [!NOTE]
> El control de excepciones estructurado funciona con Win32 para archivos de código fuente de C y C++. Sin embargo, no está diseñado específicamente para C++. Para asegurarse de que el código será más portable, use el control de excepciones de C++. Además, el control de excepciones de C++ es más flexible, ya que puede controlar excepciones de cualquier tipo. Para los programas de C++, se recomienda utilizar el mecanismo de control de excepciones de C++ ([try, catch y throw](../cpp/try-throw-and-catch-statements-cpp.md) instrucciones).

La instrucción compuesta después de la **__try** cláusula es el cuerpo o la sección protegida. La instrucción compuesta después de la **__except** cláusula es el controlador de excepciones. El controlador especifica un conjunto de acciones que se realizarán si se inicia una excepción durante la ejecución del cuerpo de la sección protegida. La ejecución continúa de la siguiente manera:

1. Se ejecuta la sección protegida.

1. Si se produce ninguna excepción durante la ejecución de la sección protegida, la ejecución continúa en la instrucción después del **__except** cláusula.

1. Si se produce una excepción durante la ejecución de la sección protegida o en cualquier rutina que llame la sección protegida, la **__except** *expresión* (denominado el *filtro* expresión) se evalúa y el valor determina cómo se controla la excepción. Hay tres valores posibles:

   - Se descarta la excepción EXCEPTION_CONTINUE_EXECUTION (-1). La ejecución continúa en el punto donde se ha producido la excepción.

   - No se reconoce la excepción exception_continue_search (0). La búsqueda de un controlador continúa hacia la parte superior de la pila, primero con las instrucciones **try-except** contenedoras y, después, con los controladores siguientes que tengan mayor prioridad.

   - Exception_execute_handler (1) excepción se reconoce. Transferir el control al controlador de excepciones mediante la ejecución de la **__except** una instrucción compuesta, a continuación, continuar la ejecución después de la **__except** bloque.

Dado que el **__except** expresión se evalúa como una expresión de C, se limita a un solo valor, el operador de expresión condicional u operador de coma. Si se requiere un mayor procesamiento, la expresión puede llamar a una rutina que devuelva uno de los tres valores enumerados anteriormente.

Cada aplicación puede tener su propio controlador de excepciones.

No es válido saltar dentro un **__try** instrucción, pero sí fuera. No se llama al controlador de excepción si un proceso se termina en medio de ejecución de un **intente-excepto** instrucción.

Para ofrecer compatibilidad con versiones anteriores, **_try**, **_except**, y **_leave** son sinónimos para **__try**, **__except** , y **__leave** a menos que la opción de compilador [/Za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) se especifica.

### <a name="the-leave-keyword"></a>La palabra clave __leave

El **__leave** palabra clave sólo es válida en la sección protegida de un **intente-excepto** instrucción y su efecto es saltar al final de la sección protegida. La ejecución de la primera instrucción continúa después del controlador de excepciones.

Un **goto** instrucción también puede saltar fuera de la sección protegida, y no afecta al rendimiento como lo hace en un **try-finally** instrucción porque el desenredo de pila no aparece. Sin embargo, se recomienda que utilice el **__leave** palabra clave en lugar de un **goto** instrucción porque es menos probable que sea un error de programación si la sección protegida es grande o compleja.

### <a name="structured-exception-handling-intrinsic-functions"></a>Funciones intrínsecas de control de excepciones estructurado

Control de excepciones estructurado proporciona dos funciones intrínsecas que están disponibles para su uso con el **intente-excepto** instrucción: `GetExceptionCode` y `GetExceptionInformation`.

`GetExceptionCode` Devuelve el código (un entero de 32 bits) de la excepción.

La función intrínseca `GetExceptionInformation` devuelve un puntero a una estructura que contiene información adicional sobre la excepción. A través de este puntero, se puede tener acceso al estado que tenía el equipo en el momento de producirse una excepción de hardware. La estructura es como se detalla a continuación:

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

Los tipos de puntero `PEXCEPTION_RECORD` y `PCONTEXT` se definen en el archivo de inclusión \<winnt.h >, y `_EXCEPTION_RECORD` y `_CONTEXT` se definen en el archivo de inclusión \<excpt.h >

Puede usar `GetExceptionCode` dentro del controlador de excepciones. Sin embargo, puede usar `GetExceptionInformation` solo dentro de la expresión de filtro de excepción. La información a la que señala está normalmente en la pila y ya no está disponible cuando el control se transfiere al controlador de excepciones.

La función intrínseca `AbnormalTermination` está disponible dentro de un controlador de terminación. Devuelve 0 si el cuerpo de la **try-finally** instrucción finaliza secuencialmente. En todos los demás casos, devuelve 1.

excpt.h define algunos nombres alternativos para estos intrínsecos:

`GetExceptionCode` es equivalente a `_exception_code`

`GetExceptionInformation` es equivalente a `_exception_info`

`AbnormalTermination` es equivalente a `_abnormal_termination`

## <a name="example"></a>Ejemplo

```cpp
// exceptions_try_except_Statement.cpp
// Example of try-except and try-finally statements
#include <stdio.h>
#include <windows.h> // for EXCEPTION_ACCESS_VIOLATION
#include <excpt.h>

int filter(unsigned int code, struct _EXCEPTION_POINTERS *ep)
{
    puts("in filter.");
    if (code == EXCEPTION_ACCESS_VIOLATION)
    {
        puts("caught AV as expected.");
        return EXCEPTION_EXECUTE_HANDLER;
    }
    else
    {
        puts("didn't catch AV, unexpected.");
        return EXCEPTION_CONTINUE_SEARCH;
    };
}

int main()
{
    int* p = 0x00000000;   // pointer to NULL
    puts("hello");
    __try
    {
        puts("in try");
        __try
        {
            puts("in try");
            *p = 13;    // causes an access violation exception;
        }
        __finally
        {
            puts("in finally. termination: ");
            puts(AbnormalTermination() ? "\tabnormal" : "\tnormal");
        }
    }
    __except(filter(GetExceptionCode(), GetExceptionInformation()))
    {
        puts("in except");
    }
    puts("world");
}
```

### <a name="output"></a>Salida

```Output
hello
in try
in try
in filter.
caught AV as expected.
in finally. termination:
        abnormal
in except
world
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Escribir un controlador de excepciones](../cpp/writing-an-exception-handler.md)<br/>
[Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
