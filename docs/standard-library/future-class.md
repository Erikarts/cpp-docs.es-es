---
title: future (Clase)
ms.date: 11/04/2016
f1_keywords:
- future/std::future
- future/std::future::future
- future/std::future::get
- future/std::future::share
- future/std::future::valid
- future/std::future::wait
- future/std::future::wait_for
- future/std::future::wait_until
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
helpviewer_keywords:
- std::future [C++]
- std::future [C++], future
- std::future [C++], get
- std::future [C++], share
- std::future [C++], valid
- std::future [C++], wait
- std::future [C++], wait_for
- std::future [C++], wait_until
ms.openlocfilehash: 9ca18e62038d93a50b592868f71223962a22857d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159332"
---
# <a name="future-class"></a>future (Clase)

Describe un *objeto de devolución asincrónico*.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
class future;
```

## <a name="remarks"></a>Comentarios

Cada *proveedor asincrónico* estándar devuelve un objeto cuyo tipo es una creación de instancia de esta plantilla. Un objeto `future` proporciona el único acceso al proveedor asincrónico con el que está asociado. Si necesita varios objetos de devolución asincrónicos que están asociados con el mismo proveedor asincrónico, copie el objeto `future` en un objeto [shared_future](../standard-library/shared-future-class.md).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[future](#future)|Construye un objeto `future`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[get](#get)|Recupera el resultado almacenado en el estado asincrónico asociado.|
|[share](#share)|Convierte el objeto en un `shared_future`.|
|[valid](#valid)|Especifica si el objeto no está vacío.|
|[wait](#wait)|Bloquea el subproceso actual hasta que el estado asincrónico asociado esté listo.|
|[wait_for](#wait_for)|Se bloquea hasta que el estado asincrónico asociado está listo, o bien hasta que el tiempo especificado haya transcurrido.|
|[wait_until](#wait_until)|Se bloquea hasta que el estado asincrónico asociado está listo o hasta un punto determinado en el tiempo.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[future::operator=](#op_eq)|Transfiere el estado asincrónico asociado de un objeto especificado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<futura >

**Espacio de nombres:** std

## <a name="future"></a>  future::future (Constructor)

Construye un objeto `future`.

```cpp
future() noexcept;
future(future&& Other) noexcept;
```

### <a name="parameters"></a>Parámetros

*Otros problemas*<br/>
Objeto `future`.

### <a name="remarks"></a>Comentarios

El primer constructor crea un objeto `future` que no tiene ningún estado asincrónico asociado.

El segundo constructor crea un `future` objeto y transfiere el estado asincrónico asociado de *otros*. *Otros* ya no tiene un estado asincrónico asociado.

## <a name="get"></a>  future::get

Recupera el resultado almacenado en el estado asincrónico asociado.

```cpp
Ty get();
```

### <a name="return-value"></a>Valor devuelto

Si el resultado es una excepción, el método la reinicia. De lo contrario, se devuelve el resultado.

### <a name="remarks"></a>Comentarios

Antes de recuperar el resultado, este método bloquea el subproceso actual hasta que el estado asincrónico asociado esté listo.

Para la especialización parcial `future<Ty&>`, el valor almacenado es realmente una referencia al objeto que se ha pasado al proveedor asincrónico como el valor devuelto.

Dado que no existe ningún valor almacenado para la especialización `future<void>`, el método devuelve **void**.

En otras especializaciones, el método mueve su valor devuelto del valor almacenado. Por tanto, llame a este método solo una vez.

## <a name="op_eq"></a>  future::operator=

Transfiere un estado asincrónico asociado de un objeto especificado.

```cpp
future& operator=(future&& Right) noexcept;
```

### <a name="parameters"></a>Parámetros

*Derecha*<br/>
Objeto `future`.

### <a name="return-value"></a>Valor devuelto

`*this`

### <a name="remarks"></a>Comentarios

Después de la transferencia, *derecha* ya no tiene un estado asincrónico asociado.

## <a name="share"></a>  future::share

Convierte el objeto en un objeto [shared_future](../standard-library/shared-future-class.md).

```cpp
shared_future<Ty> share();
```

### <a name="return-value"></a>Valor devuelto

`shared_future(move(*this))`

## <a name="valid"></a>  future::valid

Especifica si el objeto tiene un estado asincrónico asociado.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Valor devuelto

**True** si el objeto tiene un estado asincrónico asociado; en caso contrario, **false**.

## <a name="wait"></a>  future::wait

Bloquea el subproceso actual hasta que el estado asincrónico asociado esté *listo*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Comentarios

Un estado asincrónico asociado está *listo* únicamente si su proveedor asincrónico ha almacenado un valor devuelto o una excepción.

## <a name="wait_for"></a>  future::wait_for

Bloquea el subproceso actual hasta que el estado asincrónico asociado esté *listo* o hasta que haya transcurrido un tiempo especificado.

```cpp
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parámetros

*Rel_time*<br/>
Un objeto [chrono::duration](../standard-library/duration-class.md) que especifica un intervalo de tiempo máximo que el subproceso bloquea.

### <a name="return-value"></a>Valor devuelto

Un [future_status](../standard-library/future-enums.md#future_status) que indica el motivo que se va a devolver.

### <a name="remarks"></a>Comentarios

Un estado asincrónico asociado está listo solo si su proveedor asincrónico ha almacenado un valor devuelto o ha almacenado una excepción.

## <a name="wait_until"></a>  future::wait_until

Bloquea el subproceso actual hasta que el estado asincrónico asociado esté *listo* o hasta después de un punto de tiempo especificado.

```cpp
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parámetros

*Abs_time*<br/>
Un objeto [chrono::time_point](../standard-library/time-point-class.md) que especifica un tiempo después del cual se puede desbloquear el subproceso.

### <a name="return-value"></a>Valor devuelto

Un [future_status](../standard-library/future-enums.md#future_status) que indica el motivo que se va a devolver.

### <a name="remarks"></a>Comentarios

Un estado asincrónico asociado está *listo* únicamente si su proveedor asincrónico ha almacenado un valor devuelto o una excepción.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<future>](../standard-library/future.md)<br/>
