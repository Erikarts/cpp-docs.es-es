---
title: __popcnt16, __popcnt, __popcnt64
ms.date: 11/04/2016
f1_keywords:
- __popcnt64
- __popcnt
- __popcnt16
helpviewer_keywords:
- popcnt instruction
- __popcnt16
- __popcnt64
- __popcnt
ms.assetid: e525b236-adc8-42df-9b9b-8b7d8c245d3b
ms.openlocfilehash: d6cc9a0ce784ab79f5e4225675a082fc55bd53e7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037015"
---
# <a name="popcnt16-popcnt-popcnt64"></a>__popcnt16, __popcnt, __popcnt64

**Específicos de Microsoft**

Cuenta el número de uno de los bits (recuento de llenado) en un 16, 32 o entero sin signo de 64 bits.

## <a name="syntax"></a>Sintaxis

```
unsigned short __popcnt16(
   unsigned short value
);
unsigned int __popcnt(
   unsigned int value
);
unsigned __int64 __popcnt64(
   unsigned __int64 value
);
```

#### <a name="parameters"></a>Parámetros

*value*<br/>
[in] El 16, 32 o entero sin signo de 64 bits para el que queremos que el recuento de llenado.

## <a name="return-value"></a>Valor devuelto

El número de bits de uno de los `value` parámetro.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__popcnt16`|Manipulación de bits avanzada|
|`__popcnt`|Manipulación de bits avanzada|
|`__popcnt64`|Manipulación de bits avanzada en modo de 64 bits.|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Cada una de estas funciones intrínsecas genera el `popcnt` instrucción. En el modo de 32 bits no hay ningún 64-bit registros de uso general, por lo tanto, no de 64 bits `popcnt`.

Para determinar la compatibilidad de hardware para el `popcnt` instrucción, llamada la `__cpuid` intrínseca con `InfoType=0x00000001` y comprobar poco 23 de `CPUInfo[2] (ECX)`. Este bit es 1 si se admite la instrucción y 0 en caso contrario. Si ejecuta el código que usa esta función intrínseca en hardware que no es compatible con la `popcnt` instrucciones, los resultados son impredecibles.

## <a name="example"></a>Ejemplo

```
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
  unsigned short us[3] = {0, 0xFF, 0xFFFF};
  unsigned short usr;
  unsigned int   ui[4] = {0, 0xFF, 0xFFFF, 0xFFFFFFFF};
  unsigned int   uir;

  for (int i=0; i<3; i++) {
    usr = __popcnt16(us[i]);
    cout << "__popcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;
  }

  for (int i=0; i<4; i++) {
    uir = __popcnt(ui[i]);
    cout << "__popcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;
  }
}
```

```Output
__popcnt16(0x0) = 0
__popcnt16(0xff) = 8
__popcnt16(0xffff) = 16
__popcnt(0x0) = 0
__popcnt(0xff) = 8
__popcnt(0xffff) = 16
__popcnt(0xffffffff) = 32
```

**FIN de Específicos de Microsoft**

Copyright 2007 by Advanced Micro Devices, Inc. Todos los derechos reservados. Reprodujo con permiso de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
