---
title: ctype_base (Clase)
ms.date: 11/04/2016
f1_keywords:
- locale/std::ctype_base
helpviewer_keywords:
- ctype_base class
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
ms.openlocfilehash: 83ef35f9fac438cfa217decf222abd365ff84269
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394187"
---
# <a name="ctypebase-class"></a>ctype_base (Clase)

La clase actúa como clase base para las facetas de la clase de plantilla [ctype](../standard-library/ctype-class.md). Una clase base para la clase ctype que se utiliza para definir los tipos de enumeración usados para clasificar o comprobar caracteres individualmente o dentro de intervalos completos.

## <a name="syntax"></a>Sintaxis

```cpp
struct ctype_base : public locale::facet
{
    enum
    {
        alnum,
        alpha,
        cntrl,
        digit,
        graph,
        lower,
        print,
        punct,
        space,
        upper,
        xdigit
    };
    typedef short mask;

    ctype_base( size_t _Refs = 0 );
    ~ctype_base();
};
```

## <a name="remarks"></a>Comentarios

Define una máscara de enumeración. Cada constante de enumeración caracteriza una manera diferente de clasificar caracteres, según lo definen las funciones con nombres similares que se declaran en el encabezado \<ctype.h>. Las constantes son:

- **space** (función [isspace](../standard-library/locale-functions.md#isspace))

- **print** (función [isprint](../standard-library/locale-functions.md#isprint))

- **cntrl** (función [iscntrl](../standard-library/locale-functions.md#iscntrl))

- **upper** (función [isupper](../standard-library/locale-functions.md#isupper))

- **lower** (función [islower](../standard-library/locale-functions.md#islower))

- **digit** (función [isdigit](../standard-library/locale-functions.md#isdigit))

- **punct** (función [ispunct](../standard-library/locale-functions.md#ispunct))

- **xdigit** (función [isxdigit](../standard-library/locale-functions.md#isxdigit))

- **alpha** (función [isalpha](../standard-library/locale-functions.md#isalpha))

- **alnum** (función [isalnum](../standard-library/locale-functions.md#isalnum))

- **graph** (función [isgraph](../standard-library/locale-functions.md#isgraph))

Puede caracterizar una combinación de clasificaciones al aplicar la operación OR a estas constantes. En concreto, es siempre true que **alnum** == ( **alfa** &#124; **dígitos** \) y **graph** \= \= \( **alnum** &#124; **punct**).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
