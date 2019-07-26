---
title: '&lt;condition_variable&gt;'
ms.date: 11/04/2016
f1_keywords:
- <condition_variable>
ms.assetid: 8567f7cc-20bd-42a7-9137-87c46f878009
ms.openlocfilehash: e63dc5a494f471997c28be8b2cd237aba45a6fd6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457383"
---
# <a name="ltconditionvariablegt"></a>&lt;condition_variable&gt;

Define las clases [condition_variable](../standard-library/condition-variable-class.md) y [condition_variable_any](../standard-library/condition-variable-any-class.md) que se usan para crear objetos que esperan que una condición sea True.

Este encabezado utiliza el runtime de simultaneidad (ConcRT) para que pueda utilizarlo junto con otros mecanismos de ConcRT. Para obtener más información sobre ConcRT, vea [Runtime de simultaneidad](../parallel/concrt/concurrency-runtime.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> condition_variable

**Espacio de nombres:** std

> [!NOTE]
> En el código compilado mediante **/CLR**, este encabezado está bloqueado.

### <a name="remarks"></a>Comentarios

El código que espera una variable de condición también debe usar una `mutex`. Un subproceso de llamada debe bloquear la `mutex` antes de llamar a las funciones que esperan la variable de condición. La `mutex` se bloquea al volver la función llamada. La `mutex` no está bloqueada mientras el subproceso espera que la condición sea True. Para que no haya resultados imprevisibles, cada subproceso que espera por una variable de condición debe usar el mismo objeto `mutex`.

Se pueden usar objetos de tipo `condition_variable_any` con una exclusión mutua de cualquier tipo. El tipo de la exclusión mutua que se usa no tiene que proporcionar el método `try_lock`. Solo se pueden usar objetos de tipo `condition_variable` con una exclusión mutua de tipo `unique_lock<mutex>`. Los objetos de este tipo pueden ser más rápidos que los objetos de tipo `condition_variable_any<unique_lock<mutex>>`.

Para esperar un evento, bloquee primero la exclusión mutua y después llame a uno de los métodos `wait` en la variable de condición. La llamada a `wait` se bloquea hasta que otro subproceso señala la variable de condición.

Las *reactivaciones falsas* se producen cuando los subprocesos que están esperando a las variables de condición se desbloquean sin notificaciones adecuadas. Para reconocer estas reactivaciones falsas, el código que espera a que una condición sea True debe comprobar de forma explícita esa condición cuando el código vuelva de una función wait. Normalmente, esto se realiza mediante un bucle; puede usar `wait(unique_lock<mutex>& lock, Predicate pred)` para que realice este bucle por usted.

```cpp
while (condition is false)
    wait for condition variable;
```

Las clases `condition_variable_any` y `condition_variable` tienen tres métodos que esperan una condición.

- `wait` espera durante un período de tiempo ilimitado.

- `wait_until` espera hasta una `time` especificada.

- `wait_for` espera durante un `time interval` especificado.

Cada uno de estos métodos tiene dos versiones sobrecargadas. Uno solo espera y se puede reactivar en falso. El otro toma un argumento de plantilla adicional que define un predicado. El método no vuelve hasta que el predicado sea **true**.

Cada clase también tiene dos métodos que se usan para notificar a una variable de condición que su condición es **verdadera**.

- `notify_one` reactiva uno de los subprocesos que está esperando la variable de condición.

- `notify_all` reactiva todos los subprocesos que están esperando la variable de condición.

## <a name="functions-and-enums"></a>Funciones y enumeraciones

```cpp
void notify_all_at_thread_exit(condition_variable& cond, unique_lock<mutex> lk);

enum class cv_status { no_timeout, timeout };
```

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[condition_variable (Clase)](../standard-library/condition-variable-class.md)\
[condition_variable_any (Clase)](../standard-library/condition-variable-any-class.md)
