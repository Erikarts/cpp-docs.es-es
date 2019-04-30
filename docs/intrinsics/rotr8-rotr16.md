---
title: _rotr8, _rotr16
ms.date: 11/04/2016
f1_keywords:
- _rotr16
- _rotr8
helpviewer_keywords:
- _rotr8 intrinsic
- _rotr16 intrinsic
ms.assetid: dfbd2c82-82b4-427a-ad52-51609027ebff
ms.openlocfilehash: 27c3a9d914d04ecdffb7fa74dc3c8f79a442445c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390404"
---
# <a name="rotr8-rotr16"></a>_rotr8, _rotr16

**Específicos de Microsoft**

Girar los valores de entrada a la derecha hacia el bit menos significativo (LSB) según un número especificado de posiciones de bit.

## <a name="syntax"></a>Sintaxis

```
unsigned char _rotr8(
   unsigned char value,
   unsigned char shift
);
unsigned short _rotr16(
   unsigned short value,
   unsigned char shift
);
```

#### <a name="parameters"></a>Parámetros

*value*<br/>
[in] El valor se va a girar.

*shift*<br/>
[in] El número de bits que se va a girar.

## <a name="return-value"></a>Valor devuelto

El valor girado.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_rotr8`|x86, ARM, x64|
|`_rotr16`|x86, ARM, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

A diferencia de una operación de desplazamiento a la derecha, al ejecutar un giro a la derecha, los bits de valor inferior baja que caen fuera del extremo inferior se mueven a las posiciones de los bits de valor superior.

## <a name="example"></a>Ejemplo

```
// rotr.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_rotr8, _rotr16)

int main()
{
    unsigned char c = 'A', c1, c2;

    for (int i = 0; i < 8; i++)
    {
       printf_s("Rotating 0x%x right by %d bits gives 0x%x\n", c,
                i, _rotr8(c, i));
    }

    unsigned short s = 0x12;
    int nBit = 10;

    printf_s("Rotating unsigned short 0x%x right by %d bits "
             "gives 0x%x\n",
            s, nBit, _rotr16(s, nBit));
}
```

```Output
Rotating 0x41 right by 0 bits gives 0x41
Rotating 0x41 right by 1 bits gives 0xa0
Rotating 0x41 right by 2 bits gives 0x50
Rotating 0x41 right by 3 bits gives 0x28
Rotating 0x41 right by 4 bits gives 0x14
Rotating 0x41 right by 5 bits gives 0xa
Rotating 0x41 right by 6 bits gives 0x5
Rotating 0x41 right by 7 bits gives 0x82
Rotating unsigned short 0x12 right by 10 bits gives 0x480
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_rotl8, _rotl16](../intrinsics/rotl8-rotl16.md)<br/>
[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)