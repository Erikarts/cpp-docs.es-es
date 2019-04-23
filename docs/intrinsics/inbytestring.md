---
title: __inbytestring
ms.date: 11/04/2016
f1_keywords:
- __inbytestring
- __inbytestring_cpp
helpviewer_keywords:
- rep insb instruction
- __inbytestring intrinsic
ms.assetid: fe549556-e7a3-4af3-8ebf-8a7dc3cb233b
ms.openlocfilehash: e515c6452d18ca022707fa2f9e36e2045523ccd5
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038588"
---
# <a name="inbytestring"></a>__inbytestring

**Específicos de Microsoft**

Lee datos desde el puerto especificado mediante el `rep insb` instrucción.

## <a name="syntax"></a>Sintaxis

```
void __inbytestring(
   unsigned short Port,
   unsigned char* Buffer,
   unsigned long Count
);
```

#### <a name="parameters"></a>Parámetros

*Puerto*<br/>
[in] Para leer desde el puerto.

*búfer*<br/>
[out] Los datos leídos desde el puerto se escriben aquí.

*Recuento*<br/>
[in] El número de bytes de datos que se va a leer.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__inbytestring`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Esta rutina solo está disponible como función intrínseca.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)