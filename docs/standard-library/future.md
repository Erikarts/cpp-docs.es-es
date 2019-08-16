---
title: '&lt;future&gt;'
ms.date: 11/04/2016
f1_keywords:
- <future>
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
ms.openlocfilehash: d33b67ed17a95b6717878aaca2f61682b1807c15
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454002"
---
# <a name="ltfuturegt"></a>&lt;future&gt;

Incluya el encabezado estándar \<future> para definir clases de plantilla y plantillas auxiliares que simplifican la ejecución de una función, posiblemente en un subproceso diferente, y la recuperación de su resultado. El resultado es el valor devuelto por la función o una excepción que la función emite pero que no se detecta en la función.

Este encabezado utiliza el runtime de simultaneidad (ConcRT) para que pueda utilizarlo junto con otros mecanismos de ConcRT. Para obtener más información sobre ConcRT, vea [Runtime de simultaneidad](../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Sintaxis

```cpp
#include <future>
```

## <a name="remarks"></a>Comentarios

> [!NOTE]
> En el código compilado mediante **/CLR**, este encabezado está bloqueado.

Un *proveedor asincrónico* almacena el resultado de una llamada de función. Se usa un *objeto de devolución asincrónico* para recuperar el resultado de una llamada de función. Un *estado asincrónico asociado* proporciona la comunicación entre un proveedor asincrónico y uno o varios objetos de devolución asincrónicos.

Un programa no crea directamente ningún objeto con un estado asincrónico asociado. El programa crea un proveedor asincrónico cuando necesita uno y a partir de él crea un objeto de devolución asincrónico que comparte su estado asincrónico asociado con el proveedor. Los proveedores asincrónicos y los objetos de devolución asincrónicos administran los objetos que contienen su estado asincrónico asociado compartido. Cuando el último objeto que hace referencia al estado asincrónico asociado lo libera, se destruye el objeto que contiene el estado asincrónico asociado.

Un proveedor asincrónico o un objeto de devolución asincrónico que no tiene ningún estado asincrónico asociado está *vacío*.

Un estado asincrónico asociado está *listo* únicamente si su proveedor asincrónico ha almacenado un valor devuelto o una excepción.

La función de plantilla `async` y las clases de plantilla `promise` y `packaged_task` son proveedores asincrónicos. Las clases de plantilla `future` y `shared_future` describen objetos de devolución asincrónicos.

Cada una de las clases `promise`de `future`plantilla, `shared_future` , y tiene una especialización para el tipo **void** y una especialización parcial para almacenar y recuperar un valor por referencia. Estas especializaciones solo difieren de la plantilla principal en las signaturas y la semántica de las funciones que almacenan y recuperan el valor devuelto.

Las clases `future` de plantilla `shared_future` y nunca bloquean en sus destructores, excepto en un caso que se conserva por compatibilidad con versiones anteriores: A diferencia de los demás futuros, para un `future`(o el último `shared_future`) que está asociado a una tarea iniciada `std::async`con, el destructor se bloquea si la tarea no se ha completado; es decir, se bloquea si este subproceso `.get()` aún no ha llamado a o `.wait()`y la tarea todavía se está ejecutando. La siguiente nota de uso se ha agregado a la descripción `std::async` de en el borrador estándar: "[Nota: Si un futuro Obtenido de STD:: Async se mueve fuera del ámbito local, otro código que use el futuro debe ser consciente de que el destructor del futuro puede bloquearse para que el estado compartido se convierta en listo. — end Note] " `future` en `shared_future` todos los demás casos, y los destructores son necesarios y se garantiza que nunca se bloqueen.

## <a name="members"></a>Miembros

### <a name="classes"></a>Clases

|Name|DESCRIPCIÓN|
|----------|-----------------|
|[future (Clase)](../standard-library/future-class.md)|Describe un objeto de devolución asincrónico.|
|[future_error (Clase)](../standard-library/future-error-class.md)|Describe un objeto de excepción que pueden producir los métodos de tipos que administran objetos `future`.|
|[packaged_task (Clase)](../standard-library/packaged-task-class.md)|Describe un proveedor asincrónico que es un contenedor de llamadas y cuya signatura de llamada es `Ty(ArgTypes...)`. Su estado asincrónico asociado contiene una copia del objeto al que se puede llamar, además del resultado posible.|
|[promise (Clase)](../standard-library/promise-class.md)|Describe un proveedor asincrónico.|
|[shared_future (Clase)](../standard-library/shared-future-class.md)|Describe un objeto de devolución asincrónico. Al contrario que un objeto `future`, un proveedor asincrónico se puede asociar a cualquier número de objetos `shared_future`.|

### <a name="structures"></a>Estructuras

|Name|DESCRIPCIÓN|
|----------|-----------------|
|[is_error_code_enum (Estructura)](../standard-library/is-error-code-enum-structure.md)|Especialización que indica que se puede utilizar `future_errc` para almacenar un elemento `error_code`.|
|[uses_allocator (Estructura)](../standard-library/uses-allocator-structure.md)|Especialización que siempre contiene true.|

### <a name="functions"></a>Funciones

|Name|DESCRIPCIÓN|
|----------|-----------------|
|[async](../standard-library/future-functions.md#async)|Representa un proveedor asincrónico.|
|[future_category](../standard-library/future-functions.md#future_category)|Devuelve una referencia al objeto `error_category` que caracteriza los errores asociados a objetos `future`.|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|Crea un elemento `error_code` que tiene el objeto `error_category` que caracteriza los errores de `future`.|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|Crea un elemento `error_condition` que tiene el objeto `error_category` que caracteriza los errores de `future`.|
|[swap](../standard-library/future-functions.md#swap)|Intercambia el estado asincrónico asociado de un objeto `promise` con el de otro.|

### <a name="enumerations"></a>Enumeraciones

|Name|DESCRIPCIÓN|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|Proporciona nombres simbólicos para los errores notificados por la clase `future_error`.|
|[future_status](../standard-library/future-enums.md#future_status)|Proporciona nombres simbólicos para los motivos que una función que ha agotado el tiempo de espera puede devolver.|
|[launch](../standard-library/future-enums.md#launch)|Representa un tipo de máscara de bits que describe los posibles modos para la función de plantilla `async`.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
