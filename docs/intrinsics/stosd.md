---
title: __stosd
ms.date: 11/04/2016
f1_keywords:
- __stosd
helpviewer_keywords:
- stosd instruction
- rep stosd instruction
- __stosd intrinsic
ms.assetid: 03104247-1cea-49f6-b6f8-287917bf5680
ms.openlocfilehash: 43a0efcfb94b7e53dacec16caccdacf86a96f5bb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032172"
---
# <a name="stosd"></a>__stosd

**Específicos de Microsoft**

Genera una instrucción de cadena de la tienda (`rep stosd`).

## <a name="syntax"></a>Sintaxis

```
void __stosd(
   unsigned long* Dest,
   unsigned long Data,
   size_t Count
);
```

#### <a name="parameters"></a>Parámetros

*dest*<br/>
[out] El destino de la operación.

*Data*<br/>
[in] Para almacenar los datos.

*Recuento*<br/>
[in] La longitud del bloque de palabras dobles para escribir.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__stosd`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

El resultado es que la palabra doble `Data` se escribe en un bloque de `Count` palabras dobles en la ubicación de memoria a la que señala a `Dest`.

Esta rutina solo está disponible como función intrínseca.

## <a name="example"></a>Ejemplo

```
// stosd.c
// processor: x86, x64

#include <stdio.h>
#include <memory.h>
#include <intrin.h>

#pragma intrinsic(__stosd)

int main()
{
    unsigned long val = 99999;
    unsigned long a[10];

    memset(a, 0, sizeof(a));
    __stosd(a+1, val, 2);

printf_s( "%u %u %u %u",
              a[0], a[1], a[2], a[3]);
}
```

```Output
0 99999 99999 0
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)