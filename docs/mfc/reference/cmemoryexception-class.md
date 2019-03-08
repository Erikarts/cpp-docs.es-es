---
title: CMemoryException (clase)
ms.date: 11/04/2016
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
ms.openlocfilehash: 11be0eba080085c507ed718ea23219ca1c93aeba
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294751"
---
# <a name="cmemoryexception-class"></a>CMemoryException (clase)

Representa una condición de excepción de memoria insuficiente.

## <a name="syntax"></a>Sintaxis

```
class CMemoryException : public CSimpleException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMemoryException::CMemoryException](#cmemoryexception)|Construye un objeto `CMemoryException`.|

## <a name="remarks"></a>Comentarios

Calificación adicional no es necesaria ni posible. Se producen excepciones de memoria de forma automática **nuevo**. Si escribe sus propias funciones de memoria, uso `malloc`, por ejemplo, a continuación, que es responsables de producir excepciones de memoria.

Para obtener más información sobre `CMemoryException`, consulte el artículo [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="cmemoryexception"></a>  CMemoryException::CMemoryException

Construye un objeto `CMemoryException`.

```
CMemoryException();
```

### <a name="remarks"></a>Comentarios

No utilice este constructor directamente, pero en su lugar llame a la función global [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). Esta función global puede tener éxito en una situación de memoria insuficiente porque construye el objeto de excepción de memoria asignado previamente. Para obtener más información sobre el procesamiento de excepciones, vea el artículo [excepciones](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Vea también

[CException (clase)](cexception-class.md)<br/>
[Gráfico de jerarquías](../hierarchy-chart.md)
