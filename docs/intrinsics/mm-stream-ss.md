---
title: _mm_stream_ss
ms.date: 11/04/2016
f1_keywords:
- _mm_stream_ss
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
ms.openlocfilehash: 76c6c848351df773b9857b2f83726b64db982d9f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263235"
---
# <a name="mmstreamss"></a>_mm_stream_ss

**Específicos de Microsoft**

Escribe datos de 32 bits en una ubicación de memoria sin contaminar las memorias caché.

## <a name="syntax"></a>Sintaxis

```
void _mm_stream_ss(
   float * Dest,
   __m128 Source
);
```

#### <a name="parameters"></a>Parámetros

*dest*<br/>
[out] Un puntero a la ubicación donde se escriben los datos de origen.

*Origen*<br/>
[in] Un número de 128 bits que contiene el `float` valor escribirse en la parte inferior de 32 bits...

## <a name="return-value"></a>Valor devuelto

Ninguno.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_mm_stream_ss`|SSE4a|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Esta función intrínseca genera el `movntss` instrucción. Para determinar la compatibilidad de hardware para esta instrucción, llame a la `__cpuid` intrínseca con `InfoType=0x80000001` y comprobar poco 6 de `CPUInfo[2] (ECX)`. Este bit es 1 cuando se admite la instrucción y 0 en caso contrario.

Si ejecuta el código que utiliza el `_mm_stream_ss` intrínseco en hardware que no es compatible con la `movntss` instrucciones, los resultados son impredecibles.

## <a name="example"></a>Ejemplo

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128 vals;
    float f[4];

    f[0] = -1.;
    f[1] = -2.;
    f[2] = -3.;
    f[3] = -4.;
    vals.m128_f32[0] = 0.;
    vals.m128_f32[1] = 1.;
    vals.m128_f32[2] = 2.;
    vals.m128_f32[3] = 3.;
    _mm_stream_ss(&f[3], vals);
    cout << "f[0] = " << f[0] << ", f[1] = " << f[1] << endl;
    cout << "f[1] = " << f[1] << ", f[3] = " << f[3] << endl;
}
```

```Output
f[0] = -1, f[1] = -2
f[2] = -3, f[3] = 3
```

**FIN de Específicos de Microsoft**

Copyright 2007 by Advanced Micro Devices, Inc. Todos los derechos reservados. Reprodujo con permiso de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Vea también

[_mm_stream_sd](../intrinsics/mm-stream-sd.md)<br/>
[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)<br/>
[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)<br/>
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)<br/>
[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)