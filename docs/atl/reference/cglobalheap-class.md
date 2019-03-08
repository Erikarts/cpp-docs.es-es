---
title: CGlobalHeap (clase)
ms.date: 11/04/2016
f1_keywords:
- CGlobalHeap
- ATLMEM/ATL::CGlobalHeap
- ATLMEM/ATL::CGlobalHeap::Allocate
- ATLMEM/ATL::CGlobalHeap::Free
- ATLMEM/ATL::CGlobalHeap::GetSize
- ATLMEM/ATL::CGlobalHeap::Reallocate
helpviewer_keywords:
- CGlobalHeap class
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
ms.openlocfilehash: cba15421fd0329df7a66a35979ed54b863b7cca0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278306"
---
# <a name="cglobalheap-class"></a>CGlobalHeap (clase)

Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones del montón global de Win32.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class CGlobalHeap : public IAtlMemMgr
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CGlobalHeap::Allocate](#allocate)|Llame a este método para asignar un bloque de memoria.|
|[CGlobalHeap::Free](#free)|Llame a este método para liberar un bloque de memoria asignada por este administrador de memoria.|
|[CGlobalHeap::GetSize](#getsize)|Llame a este método para obtener el tamaño de un bloque de memoria asignado por este administrador de memoria asignado.|
|[CGlobalHeap::Reallocate](#reallocate)|Llame a este método para reasignar la memoria asignada por este administrador de memoria.|

## <a name="remarks"></a>Comentarios

`CGlobalHeap` implementa funciones de asignación de memoria mediante las funciones del montón global de Win32.

> [!NOTE]
>  Las funciones del montón global son más lentas que otras funciones de administración de memoria y no proporcionan tantas características. Por lo tanto, las aplicaciones nuevas deben usar el [funciones de montón](/windows/desktop/Memory/heap-functions). Están disponibles en el [CWin32Heap](../../atl/reference/cwin32heap-class.md) clase. Todavía se utilizan las funciones globales, DDE y las funciones de Portapapeles.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IAtlMemMgr`

`CGlobalHeap`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlmem.h

##  <a name="allocate"></a>  CGlobalHeap::Allocate

Llame a este método para asignar un bloque de memoria.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
Número de bytes solicitado en el nuevo bloque de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al principio del bloque de memoria recién asignado.

### <a name="remarks"></a>Comentarios

Llame a [cglobalheap:: Free](#free) o [cglobalheap:: ReAllocate](#reallocate) para liberar la memoria asignada por este método.

Implementa mediante [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) con un parámetro de marca de GMEM_FIXED.

##  <a name="free"></a>  CGlobalHeap::Free

Llame a este método para liberar un bloque de memoria asignada por este administrador de memoria.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria. NULL es un valor válido y no hace nada.

### <a name="remarks"></a>Comentarios

Implementa mediante [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree).

##  <a name="getsize"></a>  CGlobalHeap::GetSize

Llame a este método para obtener el tamaño de un bloque de memoria asignado por este administrador de memoria asignado.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve el tamaño del bloque de memoria asignada en bytes.

### <a name="remarks"></a>Comentarios

Implementa mediante [GlobalSize](/windows/desktop/api/winbase/nf-winbase-globalsize).

##  <a name="reallocate"></a>  CGlobalHeap::Reallocate

Llame a este método para reasignar la memoria asignada por este administrador de memoria.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria.

*nBytes*<br/>
Número de bytes solicitado en el nuevo bloque de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al principio del bloque de memoria recién asignado.

### <a name="remarks"></a>Comentarios

Llame a [cglobalheap:: Free](#free) para liberar la memoria asignada por este método.

Implementa mediante [GlobalReAlloc](/windows/desktop/api/winbase/nf-winbase-globalrealloc).

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[CComHeap (clase)](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap (clase)](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap (clase)](../../atl/reference/clocalheap-class.md)<br/>
[CCRTHeap (clase)](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr (clase)](../../atl/reference/iatlmemmgr-class.md)
