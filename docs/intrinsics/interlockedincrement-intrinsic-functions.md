---
title: Funciones intrínsecas _InterlockedIncrement
ms.date: 12/17/2018
f1_keywords:
- _InterlockedIncrement_acq
- _InterlockedIncrement16_rel_cpp
- _InterlockedIncrement16_cpp
- _InterlockedIncrement64_rel
- _InterlockedIncrement_rel
- _InterlockedIncrement64_nf
- _InterlockedIncrement16_acq_cpp
- _InterlockedIncrement_rel_cpp
- _InterlockedIncrement64
- _InterlockedIncrement64_rel_cpp
- _InterlockedIncrement16_nf
- _InterlockedIncrement16_rel
- _InterlockedIncrement16_acq
- _InterlockedIncrement_nf
- _InterlockedIncrement_acq_cpp
- _InterlockedIncrement64_cpp
- _InterlockedIncrement64_acq_cpp
- _InterlockedIncrement
- _InterlockedIncrement_cpp
- _InterlockedIncrement64_acq
- _InterlockedIncrement16
helpviewer_keywords:
- _InterlockedIncrement64_rel intrinsic
- _InterlockedIncrement16_rel intrinsic
- InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16 intrinsic
- _InterlockedIncrement16_acq intrinsic
- _InterlockedIncrement_nf intrinsic
- _InterlockedIncrement_rel intrinsic
- _InterlockedIncrement64_nf intrinsic
- InterlockedIncrement_rel intrinsic
- InterlockedIncrement_acq intrinsic
- _InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16_nf intrinsic
- _InterlockedIncrement intrinsic
- _InterlockedIncrement64 intrinsic
- InterlockedIncrement64_rel intrinsic
- InterlockedIncrement64 intrinsic
- InterlockedIncrement16 intrinsic
- _InterlockedIncrement_acq intrinsic
- InterlockedIncrement intrinsic
ms.assetid: 37700615-f372-438b-bcef-d76e11839482
ms.openlocfilehash: 3054a9eab21f6f7ec149f7f1c23c3c40fca3b9e1
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2018
ms.locfileid: "53626938"
---
# <a name="interlockedincrement-intrinsic-functions"></a>Funciones intrínsecas _InterlockedIncrement

**Específicos de Microsoft**

Proporciona compatibilidad intrínseca del compilador para el SDK de Windows de Win32 [InterlockedIncrement](/windows/desktop/api/winbase/nf-winbase-interlockedincrement) función.

## <a name="syntax"></a>Sintaxis

```
long _InterlockedIncrement(
   long * lpAddend
);
long _InterlockedIncrement_acq(
   long * lpAddend
);
long _InterlockedIncrement_rel(
   long * lpAddend
);
long _InterlockedIncrement_nf(
   long * lpAddend
);
short _InterlockedIncrement16(
   short * lpAddend
);
short _InterlockedIncrement16_acq(
   short * lpAddend
);
short _InterlockedIncrement16_rel(
   short * lpAddend
);
short _InterlockedIncrement16_nf (
   short * lpAddend
);
__int64 _InterlockedIncrement64(
   __int64 * lpAddend
);
__int64 _InterlockedIncrement64_acq(
   __int64 * lpAddend
);
__int64 _InterlockedIncrement64_rel(
   __int64 * lpAddend
);
__int64 _InterlockedIncrement64_nf(
   __int64 * lpAddend
);
```

#### <a name="parameters"></a>Parámetros

*lpAddend*<br/>
[in, out] Puntero a la variable que se va a incrementar.

## <a name="return-value"></a>Valor devuelto

El valor devuelto es el valor incrementado resultante.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|Header|
|---------------|------------------|------------|
|`_InterlockedIncrement`, `_InterlockedIncrement16`, `_InterlockedIncrement64`|x86, ARM, x64|\<INTRIN.h >|
|`_InterlockedIncrement_acq`, `_InterlockedIncrement_rel`, `_InterlockedIncrement_nf`, `_InterlockedIncrement16_acq`, `_InterlockedIncrement16_rel`, `_InterlockedIncrement16_nf`, `_InterlockedIncrement64_acq`, `_InterlockedIncrement64_rel`, `_InterlockedIncrement64_nf`|ARM|\<INTRIN.h >|

## <a name="remarks"></a>Comentarios

Hay diversas variaciones en `_InterlockedIncrement` que varían en función de los tipos de datos que implican y de si se utiliza la liberación o la adquisición de semántica específica del procesador.

Mientras que la función `_InterlockedIncrement` opera con valores enteros de 32 bits, `_InterlockedIncrement16` opera con valores enteros de 16 bits y `_InterlockedIncrement64` opera con valores enteros de 64 bits.

En plataformas ARM, utilice los intrínsecos con sufijos `_acq` y `_rel` si necesita adquirir y liberar semántica, como al principio y al final de una sección crítica. Los intrínsecos con un sufijo `_nf` ("sin límite") no actúan como una barrera de memoria.

La variable a la que apunta el parámetro `lpAddend` debe estar alineada en un límite de 32 bits; de lo contrario, esta función produce un error en sistemas x86 multiprocesadores y en sistemas que no son x86. Para obtener más información, consulte [alinear](../cpp/align-cpp.md).

La función de Win32 se declara en `Wdm.h` o `Ntddk.h`.

Estas rutinas solo están disponibles como intrínsecos.

## <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo usar `_InterlockedIncrement`, consulte [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Conflictos con el compilador de x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)