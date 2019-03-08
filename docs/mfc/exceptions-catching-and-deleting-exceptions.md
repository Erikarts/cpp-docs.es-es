---
title: 'Excepciones: Detectar y eliminar excepciones'
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
ms.openlocfilehash: 511850c3c17a4eb70529202f4b0c2b36132fc8ff
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287209"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Excepciones: Detectar y eliminar excepciones

Las instrucciones y los ejemplos siguientes muestran cómo detectar y eliminar excepciones. Para obtener más información sobre la **intente**, **catch**, y **throw** palabras clave, consulte [control de excepciones de C++](../cpp/cpp-exception-handling.md).

Los controladores de excepciones deben eliminar los objetos de excepción que controlan, porque el error al eliminar la excepción produce una pérdida de memoria siempre que ese código detecta una excepción.

Su **catch** bloque debe eliminar una excepción cuando:

- El **catch** bloque produce una excepción de nuevo.

   Por supuesto, no debe eliminar la excepción si se produce la misma excepción:

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- Devuelve la ejecución desde el **catch** bloque.

> [!NOTE]
>  Al eliminar un `CException`, utilice el `Delete` función miembro para eliminar la excepción. No utilice el **eliminar** palabra clave, ya que se puede producir un error si la excepción no está en el montón.

#### <a name="to-catch-and-delete-exceptions"></a>Para detectar y eliminar excepciones

1. Use la **intente** palabra clave para configurar un **intente** bloque. Ejecutar ninguna instrucción del programa que podría producir una excepción dentro de un **intente** bloque.

   Use la **catch** palabra clave para configurar un **catch** bloque. Coloque el código de control de excepciones en un **catch** bloque. El código en el **catch** bloque se ejecuta sólo si el código dentro de la **intente** bloque produce una excepción del tipo especificado en el **catch** instrucción.

   El esquema siguiente se muestra cómo **intente** y **catch** bloques se organizan normalmente:

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   Cuando se produce una excepción, el control pasa al primer **catch** bloque cuya declaración de excepción coincide con el tipo de la excepción. Puede controlar selectivamente los diferentes tipos de excepciones con secuencial **catch** bloquea como se muestra a continuación:

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Para obtener más información, consulte [excepciones: Convertir desde Macros de excepción de MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>Vea también

[Control de excepciones](../mfc/exception-handling-in-mfc.md)
