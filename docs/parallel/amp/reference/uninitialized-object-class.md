---
title: uninitialized_object (clase)
ms.date: 11/04/2016
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
ms.openlocfilehash: 5dc03964e8ddef0cd1aab785316eabd98c39e59e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544539"
---
# <a name="uninitializedobject-class"></a>uninitialized_object (clase)

La excepción que se produce cuando se usa un objeto no inicializado.

## <a name="syntax"></a>Sintaxis

```
class uninitialized_object : public runtime_exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[uninitialized_object (Constructor)](#ctor)|Inicializa una nueva instancia de la clase `uninitialized_object`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt.h

**Espacio de nombres:** Concurrency
## <a name="uninitialized_object__ctor"></a> unsupported_feature)

Crea una nueva instancia de la excepción unsupported_feature.

### <a name="syntax"></a>Sintaxis

```
explicit unsupported_feature(
    const char * _Message ) throw();

unsupported_feature() throw();
```

### <a name="parameters"></a>Parámetros

*_Cuerpo*<br/>
Descripción del error.

### <a name="return-value"></a>Valor devuelto

Objeto `unsupported_feature`.

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
