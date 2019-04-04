---
title: HStringReference (Clase)
ms.date: 09/25/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::Get
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HStringReference class
- Microsoft::WRL::Wrappers::HStringReference::CopyTo method
- Microsoft::WRL::Wrappers::HStringReference::Get method
- Microsoft::WRL::Wrappers::HStringReference::HStringReference, constructor
- Microsoft::WRL::Wrappers::HStringReference::operator= operator
- Microsoft::WRL::Wrappers::HStringReference::operator== operator
- Microsoft::WRL::Wrappers::HStringReference::operator!= operator
- Microsoft::WRL::Wrappers::HStringReference::operator< operator
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
ms.openlocfilehash: b9d2e49d0a7e1321e2259c06e1313a90d55dc90e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785867"
---
# <a name="hstringreference-class"></a>HStringReference (Clase)

Representa un objeto HSTRING que se crea a partir de una cadena existente.

## <a name="syntax"></a>Sintaxis

```cpp
class HStringReference;
```

## <a name="remarks"></a>Comentarios

El tiempo de ejecución de Windows no administra la duración del búfer de respaldo en la nueva HSTRING. El llamador asigna una cadena de origen en el marco de pila para evitar una asignación del montón y para eliminar el riesgo de pérdida de memoria. Además, el llamador debe asegurarse de que la cadena original permanece intacta durante la duración de HSTRING adjunto. Para obtener más información, consulte [WindowsCreateStringReference función](/windows/desktop/api/winstring/nf-winstring-windowscreatestringreference).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                                                    | Descripción
------------------------------------------------------- | -----------------------------------------------------------
[HStringReference::HStringReference](#hstringreference) | Inicializa una nueva instancia de la clase `HStringReference`.

### <a name="public-methods"></a>Métodos públicos

Miembro                              | Descripción
----------------------------------- | ------------------------------------------------------------------
[HStringReference::CopyTo](#copyto) | Copia actual `HStringReference` objeto a un objeto HSTRING.
[HStringReference::Get](#get)       | Recupera el valor del identificador HSTRING subyacente.

### <a name="public-operators"></a>Operadores públicos

Name                                                  | Descripción
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference::operator=](#operator-assign)       | Mueve el valor de otro `HStringReference` el objeto actual `HStringReference` objeto.
[HStringReference::operator==](#operator-equality)    | Indica si los dos parámetros son iguales.
[HStringReference::operator!=](#operator-inequality)  | Indica si los dos parámetros no son iguales.
[HStringReference::operator&lt;](#operator-less-than) | Indica si el primer parámetro es menor que el segundo parámetro.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HStringReference`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers

## <a name="copyto"></a>HStringReference::CopyTo

Copia actual `HStringReference` objeto a un objeto HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parámetros

*str*<br/>
La HSTRING que recibe la copia.

### <a name="remarks"></a>Comentarios

Este método llama a la [WindowsDuplicateString](/windows/desktop/api/winstring/nf-winstring-windowsduplicatestring) función.

## <a name="get"></a>HStringReference::Get

Recupera el valor del identificador HSTRING subyacente.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Valor devuelto

El valor de identificador HSTRING subyacente.

## <a name="hstringreference"></a>HStringReference::HStringReference

Inicializa una nueva instancia de la clase `HStringReference`.

```cpp
template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest]) throw();

template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest],
                 unsigned int len) throw();

HStringReference(HStringReference&& other) throw();
```

### <a name="parameters"></a>Parámetros

*sizeDest*<br/>
Un parámetro de plantilla que especifica el tamaño del destino `HStringReference` búfer.

*str*<br/>
Una referencia a una cadena de caracteres anchos.

*len*<br/>
La longitud máxima de la *str* búfer de parámetro para utilizar en esta operación. Si el *len* parámetro no se especifica, toda la *str* se usa el parámetro. Si *len* es mayor que *sizeDest*, *len* está establecido en *sizeDest*-1.

*other*<br/>
Otro `HStringReference` objeto.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa un nuevo `HStringReference` objeto que el mismo tamaño que el parámetro *str*.

El segundo constructor inicializa una nueva `HStringReference` objeto al que el specifeid tamaño por parámetro *len*.

El tercer constructor inicializa una nueva `HStringReference` objeto por el valor de la *otros* parámetro y, a continuación, se destruye el *otros* parámetro.

## <a name="operator-assign"></a>HStringReference::operator=

Mueve el valor de otro `HStringReference` el objeto actual `HStringReference` objeto.

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Objeto `HStringReference` existente.

### <a name="remarks"></a>Comentarios

El valor de la existente *otros* objeto se copia a la actual `HStringReference` objeto y, a continuación, el *otros* se destruye el objeto.

## <a name="operator-equality"></a>HStringReference::operator==

Indica si los dos parámetros son iguales.

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
El primer parámetro para comparar. *LHS* puede ser un `HStringReference` objeto o un identificador HSTRING.

*rhs*<br/>
El segundo parámetro para comparar.  *RHS* puede ser un `HStringReference` objeto o un identificador HSTRING.

### <a name="return-value"></a>Valor devuelto

**True** si el *lhs* y *rhs* parámetros son iguales; en caso contrario, **false**.

## <a name="operator-inequality"></a>HStringReference::operator!=

Indica si los dos parámetros no son iguales.

```cpp
inline bool operator!=(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
El primer parámetro para comparar. *LHS* puede ser un `HStringReference` objeto o un identificador HSTRING.

*rhs*<br/>
El segundo parámetro para comparar.  *RHS* puede ser un `HStringReference` objeto o un identificador HSTRING.

### <a name="return-value"></a>Valor devuelto

**True** si el *lhs* y *rhs* parámetros no son iguales; en caso contrario, **false**.

## <a name="operator-less-than"></a>HStringReference::operator&lt;

Indica si el primer parámetro es menor que el segundo parámetro.

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
El primer parámetro para comparar. *LHS* puede ser una referencia a un `HStringReference`.

*rhs*<br/>
El segundo parámetro para comparar.  *RHS* puede ser una referencia a un `HStringReference`.

### <a name="return-value"></a>Valor devuelto

**True** si el *lhs* parámetro es menor que el *rhs* parámetro; en caso contrario, **false**.
