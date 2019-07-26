---
title: system_clock (Estructura)
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::system_clock
- chrono/std::chrono::system_clock::from_time_t
- chrono/std::chrono::system_clock::now
- chrono/std::chrono::system_clock::to_time_t
- chrono/std::chrono::system_clock::is_monotonic Constant
- chrono/std::chrono::system_clock::is_steady Constant
ms.assetid: a97bd46e-267a-4836-9f7d-af1f664e99ae
ms.openlocfilehash: 7a9fd83840883de5172df8b2e1e451984a95ea47
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450188"
---
# <a name="systemclock-structure"></a>system_clock (Estructura)

Representa un *tipo de reloj* basado en el reloj en tiempo real del sistema.

## <a name="syntax"></a>Sintaxis

```cpp
struct system_clock;
```

## <a name="remarks"></a>Comentarios

Se usa un *tipo de reloj* para obtener la hora actual en formato UTC. El tipo personifica una creación de instancias de [duration](../standard-library/duration-class.md) y la plantilla de clase [time_point](../standard-library/time-point-class.md), y define una función miembro estática `now()` que devuelve la hora.

Un reloj es *monotónico* si el valor devuelto por la primera llamada a `now()` siempre es menor o igual que el valor devuelto por una llamada posterior a `now()`.

Un reloj es *constante* si es *monotónico* y si el tiempo entre los ciclos de reloj es constante.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`system_clock::duration`|Sinónimo de `duration<rep, period>`.|
|`system_clock::period`|Sinónimo del tipo que se utiliza para representar el período de ciclo en la creación de instancias contenida de `duration`.|
|`system_clock::rep`|Sinónimo del tipo que se utiliza para representar el número de ciclos del reloj en la creación de instancias contenida de `duration`.|
|`system_clock::time_point`|Sinónimo de `time_point<Clock, duration>`, donde `Clock` es un sinónimo del tipo de reloj propiamente dicho o de otro tipo de reloj basado en la mismo tiempo base y tiene el mismo tipo `duration` anidado.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[from_time_t](#from_time_t)|Estático. Devuelve el `time_point` que más se aproxima a una hora especificada.|
|[now](#now)|Estático. Devuelve la hora actual.|
|[to_time_t](#to_time_t)|Estático. Devuelve el objeto `time_t` que más se aproxima a un `time_point` especificado.|

### <a name="public-constants"></a>Constantes públicas

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[system_clock::is_monotonic (Constante)](#is_monotonic_constant)|Especifica si el tipo de reloj es monotónico.|
|[system_clock::is_steady (Constante)](#is_steady_constant)|Especifica si el tipo de reloj es constante.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> crónico

**Espacio de nombres:** std::chrono

## <a name="from_time_t"></a>  system_clock::from_time_t

Método estático que devuelve el [time_point](../standard-library/time-point-class.md) que más se aproxima a la hora representada por *TM*.

```cpp
static time_point from_time_t(time_t Tm) noexcept;
```

### <a name="parameters"></a>Parámetros

*TM*\
Un objeto [time_t](../c-runtime-library/standard-types.md).

## <a name="is_monotonic_constant"></a>  system_clock::is_monotonic (Constante)

Valor estático que especifica si el tipo del reloj es monotónico.

```cpp
static const bool is_monotonic = false;
```

### <a name="return-value"></a>Valor devuelto

En esta implementación, `system_clock::is_monotonic` siempre devuelve **false**.

### <a name="remarks"></a>Comentarios

Un reloj es *monotónico* si el valor devuelto por la primera llamada a `now()` siempre es menor o igual que el valor devuelto por una llamada posterior a `now()`.

## <a name="is_steady_constant"></a>  system_clock::is_steady (Constante)

Valor estático que especifica si el tipo del reloj es *constante*.

```cpp
static const bool is_steady = false;
```

### <a name="return-value"></a>Valor devuelto

En esta implementación, `system_clock::is_steady` siempre devuelve **false**.

### <a name="remarks"></a>Comentarios

Un reloj es *constante* si es [monotónico](#is_monotonic_constant) y si el tiempo entre los ciclos de reloj es constante.

## <a name="now"></a>  system_clock::now

Método estático que devuelve la hora actual.

```cpp
static time_point now() noexcept;
```

### <a name="return-value"></a>Valor devuelto

Un objeto [time_point](../standard-library/time-point-class.md) que representa la hora actual.

## <a name="to_time_t"></a>  system_clock::to_time_t

Método estático que devuelve el [time_t](../c-runtime-library/standard-types.md) que más se aproxima a la hora representada por *Time*.

```cpp
static time_t to_time_t(const time_point& Time) noexcept;
```

### <a name="parameters"></a>Parámetros

*Tiempo*\
Un objeto [time_point](../standard-library/time-point-class.md).

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[steady_clock (struct)](../standard-library/steady-clock-struct.md)
