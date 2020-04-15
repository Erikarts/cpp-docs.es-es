---
title: Platform::Collections::MapView (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::MapView::MapView
- COLLECTION/Platform::Collections::MapView::First
- COLLECTION/Platform::Collections::MapView::HasKey
- COLLECTION/Platform::Collections::MapView::Lookup
- COLLECTION/Platform::Collections::MapView::Size
- COLLECTION/Platform::Collections::MapView::Split
helpviewer_keywords:
- MapView Class
ms.assetid: 9577dde7-f599-43c6-b1e4-7d653706fd62
ms.openlocfilehash: 24995f553c5fcb8626c0d51758577b948c9c67ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354438"
---
# <a name="platformcollectionsmapview-class"></a>Platform::Collections::MapView (Clase)

Representa una vista de solo lectura en un *mapa*, que es una colección de pares clave-valor.

## <a name="syntax"></a>Sintaxis

```
template <
   typename K,
   typename V,
   typename C = ::std::less<K>>
ref class MapView sealed;
```

#### <a name="parameters"></a>Parámetros

*K*<br/>
Tipo de la clave del par clave-valor.

*Ⅴ*<br/>
Tipo del valor del par clave-valor.

*C*<br/>
Un tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto MapView. De forma predeterminada, [std::less\<K>](../standard-library/less-struct.md).

### <a name="remarks"></a>Observaciones

MapView es una implementación concreta de C++ de la interfaz [de>\<Windows::Foundation::Collections::IMapView K,V](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) que se pasa a través de la interfaz binaria de la aplicación (ABI). Para obtener más información, consulta [Colecciones (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[MapView::MapView](#ctor)|Inicializa una nueva instancia de la clase MapView.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[MapView::First](#first)|Devuelve un iterador que se inicializa el primer elemento en la vista de mapa.|
|[MapView::HasKey](#haskey)|Determina si el objeto MapView actual contiene la clave especificada.|
|[MapView::Lookup](#lookup)|Recupera el elemento en la clave especificada del objeto MapView actual.|
|[MapView::Size](#size)|Devuelve el número de elementos del objeto MapView actual.|
|[MapView::Split](#split)|Divide un objeto MapView original en dos objetos MapView.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`MapView`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres:** Platform::Collections

## <a name="mapviewfirst-method"></a><a name="first"></a>MapView::Primer método

Devuelve un iterador que especifica el primer elemento de la vista de mapa.

### <a name="syntax"></a>Sintaxis

```
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Valor devuelto

Un iterador que especifica el primer elemento de la vista de mapa.

### <a name="remarks"></a>Observaciones

Una forma cómoda de contener el iterador devuelto por First() es asignar el valor devuelto a una variable que se declara con la palabra clave de deducción de tipo **automático.** Por ejemplo, `auto x = myMapView->First();`.

## <a name="mapviewhaskey-method"></a><a name="haskey"></a>MapView::HasKey Método

Determina si el objeto MapView actual contiene la clave especificada.

### <a name="syntax"></a>Sintaxis

```

bool HasKey(K key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave que se usa para ubicar el elemento MapView. El tipo de *clave* es typename *K*.

### <a name="return-value"></a>Valor devuelto

**true** si se encuentra la clave; de lo contrario, **false**.

## <a name="mapviewlookup-method"></a><a name="lookup"></a>MapView::Método de búsqueda

Recupera el valor de tipo V asociado a la clave especificada de tipo K.

### <a name="syntax"></a>Sintaxis

```
V Lookup(K key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave utilizada para buscar un elemento en el objeto MapView. El tipo `key` de es typename *K*.

### <a name="return-value"></a>Valor devuelto

El valor que se empareja con `key`. El tipo del valor devuelto es typename *V*.

## <a name="mapviewmapview-constructor"></a><a name="ctor"></a>MapView::MapView Constructor

Inicializa una nueva instancia de la clase MapView.

### <a name="syntax"></a>Sintaxis

```cpp
explicit MapView(const C& comp = C());

explicit MapView(const ::std::map<K, V, C>& m);

explicit MapView(std::map<K, V, C>&& m);

template <typename InIt> MapView(
    InIt first,
    InIt last,
    const C& comp = C());

MapView(
    ::std::initializer_list<std::pair<const K, V>> il,
    const C& comp = C());
```

### <a name="parameters"></a>Parámetros

*Init*<br/>
El typename del objeto MapView actual.

*Comp*<br/>
Objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto MapView.

*M*<br/>
Una referencia o [Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) a un `map Class` que se utiliza para inicializar el MapView actual.

*Primero*<br/>
El iterador de entrada del primer elemento en un intervalo de elementos utilizados para inicializar el objeto MapView actual.

*Última*<br/>
El iterador de entrada del primer elemento tras un intervalo de elementos utilizados para inicializar el objeto MapView actual.

*Il*<br/>
Un [std::initializer_list<std::pair\<K,V>>](../standard-library/initializer-list-class.md) cuyos elementos se insertarán en el MapView.

## <a name="mapviewsize-method"></a><a name="size"></a>MapView::Método de tamaño

Devuelve el número de elementos del objeto MapView actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos del objeto MapView actual.

## <a name="mapviewsplit-method"></a><a name="split"></a>MapView::Split Método

Divide el objeto MapView actual en dos objetos MapView. Este método no es operativo.

### <a name="syntax"></a>Sintaxis

```
void Split(
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * secondPartition);
```

### <a name="parameters"></a>Parámetros

*firstPartition*<br/>
La primera parte del objeto MapView original.

*secondPartition*<br/>
La segunda parte del objeto MapView original.

### <a name="remarks"></a>Observaciones

Este método no es operativo; no realiza ninguna acción.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](platform-namespace-c-cx.md)
