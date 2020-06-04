---
title: ctype&lt;char&gt; (Clase)
ms.date: 11/04/2016
f1_keywords:
- ctype<char>
- locale/std::ctype<char>
helpviewer_keywords:
- ctype<char> class
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
ms.openlocfilehash: 08bf2c5c814eaed7b409295fcf50c66577f6a5d9
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688150"
---
# <a name="ctypeltchargt-class"></a>ctype&lt;char&gt; (Clase)

La clase es una especialización explícita de la plantilla de clase `ctype\<CharType>` al tipo **Char**, que describe un objeto que puede actuar como una faceta de configuración regional para caracterizar las distintas propiedades de un carácter de tipo **Char**.

## <a name="syntax"></a>Sintaxis

```cpp
template <>
class ctype<char>
: public ctype_base
{
public:
    typedef char _Elem;
    typedef _Elem char_type;
    bool is(
    mask _Maskval,
    _Elem _Ch) const;

    const _Elem* is(
    const _Elem* first,
    const _Elem* last,
    mask* dest) const;

    const _Elem* scan_is(
    mask _Maskval,
    const _Elem* first,
    const _Elem* last) const;

    const _Elem* scan_not(
    mask _Maskval,
    const _Elem* first,
    const _Elem* last) const;

    _Elem tolower(
    _Elem _Ch) const;

    const _Elem* tolower(
    _Elem* first,
    const _Elem* last) const;

    _Elem toupper(
    _Elem _Ch) const;

    const _Elem* toupper(
    _Elem* first,
    const _Elem* last) const;

    _Elem widen(
    char _Byte) const;

    const _Elem* widen(
    const char* first,
    const char* last,
    _Elem* dest) const;

    const _Elem* _Widen_s(
    const char* first,
    const char* last,
    _Elem* dest,
    size_t dest_size) const;

    _Elem narrow(
    _Elem _Ch,
    char _Dflt = '\0') const;

    const _Elem* narrow(
    const _Elem* first,
    const _Elem* last,
    char _Dflt,
    char* dest) const;

    const _Elem* _Narrow_s(
    const _Elem* first,
    const _Elem* last,
    char _Dflt,
    char* dest,
    size_t dest_size) const;

    static locale::id& id;
    explicit ctype(
    const mask* _Table = 0,
    bool _Deletetable = false,
    size_t _Refs = 0);

protected:
    virtual ~ctype();
//other protected members
};
```

## <a name="remarks"></a>Comentarios

La especialización explícita difiere de la plantilla de clase de varias maneras:

- Un objeto de la clase ctype < `char` > almacena un puntero al primer elemento de una tabla de máscara ctype, una matriz de elementos UCHAR_MAX + 1 de tipo `ctype_base::mask`. También almacena un objeto booleano que indica si se debe eliminar la matriz (con `operator delete[]`) cuando se destruye el objeto ctype\< **Elem**>.

- Su único constructor público le permite especificar `tab`, la tabla de máscara ctype y el `del`, el objeto booleano que es true si la matriz se debe eliminar cuando se destruye el objeto ctype < `char` >, así como las referencias de parámetro de recuento de referencias.

- La función miembro protegida `table` devuelve la tabla de máscara ctype almacenada.

- El objeto miembro estático `table_size` especifica el número mínimo de elementos de una tabla de máscara ctype.

- La función miembro estática protegida `classic_table` (devuelve la tabla de máscara ctype adecuada a la configuración regional "C".

- No hay ninguna función miembro virtual protegida [do_is](../standard-library/ctype-class.md#do_is), [do_scan_is](../standard-library/ctype-class.md#do_scan_is) o [do_scan_not](../standard-library/ctype-class.md#do_scan_not). Las funciones miembro públicas correspondientes realizan las operaciones equivalentes ellas mismas.

Las funciones miembro [do_narrow](../standard-library/ctype-class.md#do_narrow) y [do_widen](../standard-library/ctype-class.md#do_widen) copian elementos sin modificaciones.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[facet (Clase)](locale-class.md#facet_class)\
[ctype_base (Clase)](../standard-library/ctype-base-class.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
