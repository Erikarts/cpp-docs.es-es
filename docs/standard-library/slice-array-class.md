---
title: slice_array (Clase)
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice_array
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
ms.openlocfilehash: 9577447b2201c1c9e53192b99abad1979f45d15f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412545"
---
# <a name="slicearray-class"></a>slice_array (Clase)

Clase de plantilla auxiliar e interna que admite objetos de segmentos proporcionando operaciones entre matrices de subconjuntos definidas por el segmento de una valarray.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type>
class slice_array : public slice {
public:
    typedef Type value_type;
    void operator=(const valarray<Type>& x) const;
    void operator=(const Type& x) const;
    void operator*=(const valarray<Type>& x) const;
    void operator/=(const valarray<Type>& x) const;
    void operator%=(const valarray<Type>& x) const;
    void operator+=(const valarray<Type>& x) const;
    void operator-=(const valarray<Type>& x) const;
    void operator^=(const valarray<Type>& x) const;
    void operator&=(const valarray<Type>& x) const;
    void operator|=(const valarray<Type>& x) const;
    void operator<<=(const valarray<Type>& x) const;
    void operator>>=(const valarray<Type>& x) const;
    // The rest is private or implementation defined
}
```

## <a name="remarks"></a>Comentarios

La clase describe un objeto que almacena una referencia a un objeto de la clase [valarray](../standard-library/valarray-class.md)**\<Type>**, junto con un objeto de la clase [slice](../standard-library/slice-class.md), que describe la secuencia de los elementos que se pueden seleccionar desde el objeto **valarray\<Type>**.

La clase de plantilla se crea indirectamente por determinadas operaciones valarray y no se puede usar directamente en el programa. Una clase de plantilla auxiliar interna que usa el operador de subíndice de segmento:

`slice_array`\< **Type**> `valarray`< **Type**:: `operator[]` ( `slice`).

Construir un `slice_array<Type>` objeto escribiendo una expresión de formato [va&#91;sl&#93;](../standard-library/valarray-class.md#op_at), para un segmento `sl` de valarray `va`. Las funciones miembro de la clase slice_array se comportarán como las firmas de función correspondientes definidas para `valarray<Type>`, excepto que solo la secuencia de elementos seleccionados se ve afectada. La secuencia controlada por slice_array se define mediante los tres parámetros del constructor de segmento, el índice del primer elemento en el segmento, el número de elementos y la distancia entre los elementos. Una slice_array obtenida de valarray `va` declarado por **va**[ `slice`(2, 5, 3)] selecciona elementos con índices de 2, 5, 8, 11 y 14 de `va`. Los índices deben ser válidos para que el procedimiento sea válido.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [slice::slice](../standard-library/slice-class.md#slice) para ver cómo se declara y usa una slice_array.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<valarray>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
