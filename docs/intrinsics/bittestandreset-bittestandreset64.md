---
title: _bittestandreset, _bittestandreset64
ms.date: 09/02/2019
f1_keywords:
- _bittestandreset64_cpp
- _bittestandreset
- _bittestandreset_cpp
- _bittestandreset64
helpviewer_keywords:
- btr instruction
- _bittestandreset intrinsic
- _bittestandreset64 intrinsic
ms.assetid: 8dad63bb-a051-4cd7-a793-3357537dfeaf
ms.openlocfilehash: 9e0c869b926b2f9f3c04fd648f84ef33b8d16fcd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216925"
---
# <a name="_bittestandreset-_bittestandreset64"></a>_bittestandreset, _bittestandreset64

**Específicos de Microsoft**

Genere la instrucción para examinar el `b` bit de la `a`dirección, devuelva su valor actual y restablezca el bit en 0.

## <a name="syntax"></a>Sintaxis

```C
unsigned char _bittestandreset(
   long *a,
   long b
);
unsigned char _bittestandreset64(
   __int64 *a,
   __int64 b
);
```

### <a name="parameters"></a>Parámetros

*un*\
[in, out] Puntero a la memoria que se va a examinar.

*b*\
de Posición de bit que se va a probar.

## <a name="return-value"></a>Valor devuelto

El bit en la posición especificada.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_bittestandreset`|x86, ARM, x64, ARM64|
|`_bittestandreset64`|x64, ARM64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

Esta rutina solo está disponible como función intrínseca.

## <a name="example"></a>Ejemplo

```cpp
// bittestandreset.cpp
// processor: x86, IPF, x64
#include <stdio.h>
#include <limits.h>
#include <intrin.h>

#pragma intrinsic(_bittestandreset)

// Check the sign bit and reset to 0 (taking the absolute value)
// Returns 0 if the number is positive or zero
// Returns 1 if the number is negative
unsigned char absolute_value(long* p)
{
   const int SIGN_BIT = 31;
   return _bittestandreset(p, SIGN_BIT);
}

int main()
{
    long i = -112;
    unsigned char result;

    // Check the sign bit and reset to 0 (taking the absolute value)

    result = absolute_value(&i);
    if (result == 1)
        printf_s("The number was negative.\n");
}
```

```Output
The number was negative.
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
