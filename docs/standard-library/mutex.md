---
title: '&lt;mutex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <mutex>
ms.assetid: efb60c89-687a-4e38-8fe4-694e11c4e8a3
ms.openlocfilehash: 377ec995f4e61c957e8e620749f96523b60fed3e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240595"
---
# <a name="ltmutexgt"></a>&lt;mutex&gt;

Incluya el encabezado estándar \<mutex> para definir las clases `mutex`, `recursive_mutex`, `timed_mutex` y `recursive_timed_mutex`; las plantillas `lock_guard` y `unique_lock`; y tipos y funciones auxiliares que definen regiones de código de exclusión mutua.

> [!WARNING]
> A partir de Visual Studio 2015, los tipos de sincronización de la biblioteca estándar de C++ se basan en las primitivas de sincronización de Windows y ya no utilizan ConcRT (salvo cuando la plataforma de destino es Windows XP). Los tipos definidos en \<mutex> no deben usarse con ninguna función o tipo ConcRT.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<mutex >

**Espacio de nombres:** std

## <a name="remarks"></a>Comentarios

> [!NOTE]
> En el código que se compila con **/CLR**, este encabezado está bloqueado.

Las clases `mutex` y `recursive_mutex` son *tipos de exclusión mutua*. Un tipo de exclusión mutua tiene un constructor predeterminado y un destructor que no inicia excepciones. Estos objetos tienen métodos que proporcionan exclusión mutua cuando varios subprocesos intentan bloquear el mismo objeto. En concreto, un tipo de exclusión mutua contiene los métodos `lock`, `try_lock` y `unlock`:

- El método `lock` bloquea el subproceso que realiza la llamada hasta que el subproceso obtenga la propiedad de la exclusión mutua. Su valor devuelto se omite.

- El método `try_lock` intenta obtener la propiedad de la exclusión mutua sin bloquear. Su tipo de valor devuelto es convertible a **bool** y es **true** si el método obtiene la propiedad, pero en caso contrario es **false**.

- El método `unlock` libera la propiedad de la exclusión mutua del subproceso que llama.

Puede usar tipos de exclusión mutua como argumentos de tipo para crear instancias de las plantillas `lock_guard` y `unique_lock`. Puede usar objetos de estos tipos como el argumento `Lock` para las funciones miembro de espera en la plantilla [condition_variable_any](../standard-library/condition-variable-any-class.md).

Un *tipo de exclusión mutua cronometrado* satisface los requisitos de un tipo de exclusión mutua. Además, tiene la `try_lock_for` y `try_lock_until` métodos que deben ser invocables mediante el uso de un argumento y deben devolver un tipo que se pueda convertir a **bool**. Un tipo de exclusión mutua cronometrado puede definir estas funciones mediante argumentos adicionales, siempre que todos esos argumentos adicionales tengan valores predeterminados.

- Se debe poder llamar al método `try_lock_for` mediante el uso de un argumento, `Rel_time`, cuyo tipo es una creación de instancias de [chrono::duration](../standard-library/duration-class.md). El método intenta obtener la propiedad de la exclusión mutua, pero devuelve dentro del período de tiempo designado por `Rel_time`, independientemente de que la operación se haya realizado o no correctamente. El valor devuelto se convierte en **true** si el método obtiene la propiedad; en caso contrario, el valor devuelto convierte a **false**.

- Se debe poder llamar al método `try_lock_until` mediante el uso de un argumento, `Abs_time`, cuyo tipo es una creación de instancias de [chrono::time_point](../standard-library/time-point-class.md). El método intenta obtener la propiedad de la exclusión mutua, pero devuelve antes de que se supere el tiempo designado por `Abs_time`, independientemente de que la operación se haya realizado o no correctamente. El valor devuelto se convierte en **true** si el método obtiene la propiedad; en caso contrario, el valor devuelto convierte a **false**.

Un tipo de exclusión mutua también se conoce como un *tipo bloqueable*. Si no proporciona la función miembro `try_lock`, es un *tipo bloqueable básico*. Un tipo de exclusión mutua cronometrado también se conoce como un *tipo bloqueable cronometrado*.

## <a name="members"></a>Miembros

### <a name="classes"></a>Clases

|||
|-|-|
|[lock_guard (Clase)](../standard-library/lock-guard-class.md)|Representa una plantilla de la que se pueden crear instancias para crear un objeto cuyo destructor desbloquea una `mutex`.|
|[mutex (Clase, biblioteca estándar de C++)](../standard-library/mutex-class-stl.md)|Representa un tipo de exclusión mutua. Use objetos de este tipo para aplicar la exclusión mutua dentro de un programa.|
|[recursive_mutex (Clase)](../standard-library/recursive-mutex-class.md)|Representa un tipo de exclusión mutua. Al contrario que la clase `mutex`, el comportamiento de la llamada a métodos de bloqueos para objetos que ya estén bloqueados está bien definido.|
|[recursive_timed_mutex (Clase)](../standard-library/recursive-timed-mutex-class.md)|Representa un tipo de exclusión mutua cronometrado. Use objetos de este tipo para aplicar una exclusión mutua que tenga un bloqueo limitado por tiempo dentro de un programa. A diferencia de los objetos de tipo `timed_mutex`, el efecto de llamar a métodos de bloqueos de objetos `recursive_timed_mutex` está bien definido.|
|[Clase scoped_lock](../standard-library/scoped-lock-class.md)||
|[timed_mutex (Clase)](../standard-library/timed-mutex-class.md)|Representa un tipo de exclusión mutua cronometrado. Use objetos de este tipo para aplicar una exclusión mutua que tenga un bloqueo limitado por tiempo dentro de un programa.|
|[unique_lock (Clase)](../standard-library/unique-lock-class.md)|Representa una plantilla de la que se pueden crear instancias para crear objetos que administren el bloqueo y desbloqueo de una `mutex`.|

### <a name="functions"></a>Funciones

|||
|-|-|
|[call_once](../standard-library/mutex-functions.md#call_once)|Proporciona un mecanismo para llamar exactamente una vez durante la ejecución a un objeto especificado que se puede llamar.|
|[lock](../standard-library/mutex-functions.md#lock)|Intenta bloquear todos los argumentos sin interbloqueo.|
|[swap](../standard-library/mutex-functions.md#swap)||
|[try_lock](../standard-library/mutex-functions.md#try_lock)||

### <a name="structs"></a>Estructuras

|||
|-|-|
|[adopt_lock_t (Estructura)](../standard-library/adopt-lock-t-structure.md)|Representa un tipo que se utiliza para definir un `adopt_lock`.|
|[defer_lock_t (Estructura)](../standard-library/defer-lock-t-structure.md)|Representa un tipo que define un objeto `defer_lock` que se utiliza para seleccionar uno de los constructores sobrecargados de `unique_lock`.|
|[once_flag (Estructura)](../standard-library/once-flag-structure.md)|Representa un **struct** que se utiliza con la función de plantilla `call_once` para asegurarse de que la inicialización se llama al código una sola vez, incluso en presencia de varios subprocesos de ejecución.|
|[try_to_lock_t (Estructura)](../standard-library/try-to-lock-t-structure.md)|Representa un **struct** que define un `try_to_lock` de objetos y se utiliza para seleccionar uno de los constructores sobrecargados de `unique_lock`.|

### <a name="variables"></a>variables

|||
|-|-|
|[adopt_lock](../standard-library/mutex-functions.md#adopt_lock)|Representa un objeto que se puede pasar a los constructores para `lock_guard` y `unique_lock` para indicar que el objeto de exclusión mutua que también se pasa al constructor está bloqueado.|
|[defer_lock](../standard-library/mutex-functions.md#defer_lock)|Representa un objeto que se puede pasar al constructor de `unique_lock` para indicar que el constructor no debería bloquear el objeto de exclusión mutua que también se pasa a él.|
|[try_to_lock](../standard-library/mutex-functions.md#try_to_lock)|Representa un objeto que se puede pasar al constructor de `unique_lock` para indicar que el constructor debería intentar desbloquear la `mutex` que también se pasa a él sin bloquearla.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
