---
title: Platform::Collections::UnorderedMapView (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMapView
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
ms.openlocfilehash: 8f8bc3490fba28232cdab3ea189dd9cfcc8d0650
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354392"
---
# <a name="platformcollectionsunorderedmapview-class"></a>Platform::Collections::UnorderedMapView (Clase)

Representa una vista de solo lectura en un *mapa*, que es una colección de pares clave-valor.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   typename K,
   typename V,
   typename C = ::std::equal_to<K>>
ref class UnorderedMapView sealed;
```

#### <a name="parameters"></a>Parámetros

*K*<br/>
Tipo de la clave del par clave-valor.

*Ⅴ*<br/>
Tipo del valor del par clave-valor.

*C*<br/>
Un tipo que proporciona un objeto de función que puede comparar dos valores de clave para determinar si son iguales. De forma predeterminada, [std::equal_to\<K>](../standard-library/equal-to-struct.md)

### <a name="remarks"></a>Observaciones

UnorderedMapView es una implementación concreta de C++ de la interfaz [de>\<Windows::Foundation::Collections::IMapView K,V](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) que se pasa a través de la interfaz binaria de la aplicación (ABI). Para obtener más información, consulta [Colecciones (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[UnorderedMapView::UnorderedMapView](#ctor)|Inicializa una nueva instancia de la clase UnorderedMapView.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[UnorderedMapView::First](#first)|Devuelve un iterador que se inicializa el primer elemento en la vista de mapa.|
|[UnorderedMapView::HasKey](#haskey)|Determina si el objeto UnorderedMapView actual contiene la clave especificada.|
|[UnorderedMapView::Lookup](#lookup)|Recupera el elemento en la clave especificada del objeto UnorderedMapView actual.|
|[UnorderedMapView::Tamaño](#size)|Devuelve el número de elementos del objeto UnorderedMapView actual.|
|[UnorderedMapView::Split](#split)|Divide un objeto UnorderedMapView original en dos objetos UnorderedMapView.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`UnorderedMapView`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres:** Platform::Collections

## <a name="unorderedmapviewfirst-method"></a><a name="first"></a>UnorderedMapView::First Método

Devuelve un iterador que especifica el primer elemento [Windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) en el mapa desordenado.

### <a name="syntax"></a>Sintaxis

```cpp
virtual Windows::Foundation::Collections::IIterator<
    Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
    First();
```

### <a name="return-value"></a>Valor devuelto

Un iterador que especifica el primer elemento de la vista de mapa.

### <a name="remarks"></a>Observaciones

Una forma cómoda de contener el iterador devuelto por First() es asignar el valor devuelto a una variable que se declara con la palabra clave de deducción de tipo **automático.** Por ejemplo, `auto x = myMapView->First();`.

## <a name="unorderedmapviewhaskey-method"></a><a name="haskey"></a>UnorderedMapView::HasKey Método

Determina si el objeto UnorderedMap actual contiene la clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave utilizada para buscar el elemento. El tipo `key` de es typename *K*.

### <a name="return-value"></a>Valor devuelto

**true** si se encuentra la clave; de lo contrario, **false**.

## <a name="unorderedmapviewlookup-method"></a><a name="lookup"></a>UnorderedMapView::Lookup Método

Recupera el valor de tipo V asociado a la clave especificada de tipo K.

### <a name="syntax"></a>Sintaxis

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave usada para buscar un elemento en UnorderedMapView. El tipo `key` de es typename *K*.

### <a name="return-value"></a>Valor devuelto

El valor que se empareja con `key`. El tipo del valor devuelto es typename *V*.

## <a name="unorderedmapviewsize-method"></a><a name="size"></a>UnorderedMapView::Size Método

Devuelve el número de [Windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) elementos en el UnorderedMapView.

### <a name="syntax"></a>Sintaxis

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos del objeto MapView sin ordenar.

## <a name="unorderedmapviewsplit-method"></a><a name="split"></a>UnorderedMapView::Split Método

Divide el objeto UnorderedMapView actual en dos objetos UnorderedMapView. Este método no es operativo.

### <a name="syntax"></a>Sintaxis

```cpp
void Split(
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * secondPartition);
```

### <a name="parameters"></a>Parámetros

*firstPartition*<br/>
La primera parte del objeto UnorderedMapView original.

*secondPartition*<br/>
La segunda parte del objeto UnorderedMapView original.

### <a name="remarks"></a>Observaciones

Este método no es operativo; no realiza ninguna acción.

## <a name="unorderedmapviewunorderedmapview-constructor"></a><a name="ctor"></a>UnorderedMapView::UnorderedMapView Constructor

Inicializa una nueva instancia de la clase UnorderedMapView.

### <a name="syntax"></a>Sintaxis

```cpp
UnorderedMapView();
explicit UnorderedMapView(size_t n);
UnorderedMapView(size_t n, const H& h);
UnorderedMapView(size_t n, const H& h, const P& p);

explicit UnorderedMapView(
    const std::unordered_map<K, V, H, P>& m);
explicit UnorderedMapView(
    std::unordered_map<K, V, H, P>&& m);

template <typename InIt> UnorderedMapView(InIt first, InIt last );
template <typename InIt> UnorderedMapView(InIt first, InIt last, size_t n );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p );

UnorderedMapView(std::initializer_list<std::pair<const K, V>);

UnorderedMapView(std::initializer_list< std::pair<const K, V>> il, size_t n

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h);

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p );
```

### <a name="parameters"></a>Parámetros

*N*<br/>
Número de elementos para los que se preasigna espacio.

*Init*<br/>
Typename del objeto UnorderedMapView.

*H*<br/>
Objeto de función que puede generar un valor hash para una clave. El valor predeterminado [es\<std::hash K>](../standard-library/hash-class.md) para los tipos que `std::hash` admite.

*P*<br/>
Tipo que proporciona un objeto de función que puede comparar dos claves para determinar si son iguales. El valor predeterminado [es\<std::equal_to K>](../standard-library/equal-to-struct.md).

*M*<br/>
Una referencia o [Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) a un [std::unordered_map](../standard-library/unordered-map-class.md) que se utiliza para inicializar el UnorderedMapView.

*Primero*<br/>
Iterador de entrada del primer elemento en un intervalo de elementos utilizados para inicializar el objeto UnorderedMapView.

*Última*<br/>
Iterador de entrada del primer elemento tras un intervalo de elementos utilizados para inicializar el objeto UnorderedMapView.

## <a name="see-also"></a>Consulte también

[Platform::Collections (Espacio de nombres)](../cppcx/platform-collections-namespace.md)<br/>
[Windows::Foundation::IMapView](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_)
