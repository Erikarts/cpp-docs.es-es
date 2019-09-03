---
title: __faststorefence
ms.date: 09/02/2019
f1_keywords:
- __faststorefence_cpp
- __faststorefence
helpviewer_keywords:
- __faststorefence intrinsic
- sfence instruction
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
ms.openlocfilehash: d11a20666612fe1bca22f5d46b93e898dae375f6
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222177"
---
# <a name="__faststorefence"></a>__faststorefence

**Específicos de Microsoft**

Garantiza que cada referencia de memoria anterior, incluidas las referencias de memoria de almacenamiento y de carga, sea visible globalmente antes que cualquier referencia de memoria posterior.

## <a name="syntax"></a>Sintaxis

```C
void __faststorefence();
```

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__faststorefence`|x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

Genera una secuencia de instrucciones de barrera de memoria completa que garantiza que las operaciones de carga y almacenamiento emitidas antes de que el intrínseco sea visible globalmente antes de que continúe la ejecución. El efecto es comparable a la función intrínseca `_mm_mfence` en todas plataformas x64, pero más rápido.

En la plataforma AMD64, esta rutina genera una instrucción que actúa como una barrera de almacenamiento más rápida que la instrucción `sfence`. Para código crítico en el tiempo, use esta función intrínseca en lugar de `_mm_sfence` únicamente en plataformas AMD64. En plataformas Intel x64, la instrucción `_mm_sfence` es más rápida.

Esta rutina solo está disponible como función intrínseca.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
