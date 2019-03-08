---
title: CMapPtrToWord (clase)
ms.date: 11/04/2016
f1_keywords:
- CMapPtrToWord
- AFXCOLL/CMapPtrToWord
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
helpviewer_keywords:
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 4631c6b6-d49f-49d9-adc0-1e0491e32d7b
ms.openlocfilehash: eec254852c00e1b7f3a536e4e63c874fd1f3b12a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260470"
---
# <a name="cmapptrtoword-class"></a>CMapPtrToWord (clase)

Admite mapas de palabras de 16 bits con clave de punteros void.

## <a name="syntax"></a>Sintaxis

```
class CMapPtrToWord : public CObject
```

## <a name="members"></a>Miembros

Las funciones miembro de `CMapPtrToWord` son similares a las funciones miembro de clase [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Debido a esta similitud, puede utilizar la documentación de referencia de `CMapStringToOb` para obtener información específica de la función miembro. Siempre que vea un `CObject` puntero como un parámetro de función o el valor devuelto, sustituya WORD. Siempre que vea un `CString` o un **const** puntero a **char** como un parámetro de función o valor devuelto, utilice un puntero a **void**.

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

por ejemplo, se traduce en

`BOOL CMapPtrToWord::Lookup( const void* <key>, WORD& <rValue> ) const;`

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMapStringToOb::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Devuelve el número de elementos de esta asignación.|
|[CMapStringToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Determina el número actual de elementos de la tabla hash.|
|[CMapStringToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Obtiene el elemento siguiente para efectuar una iteración.|
|[CMapStringToOb::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Devuelve el número de elementos de esta asignación.|
|[CMapStringToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Devuelve la posición del primer elemento.|
|[CMapStringToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Calcula el valor hash de una clave especificada.|
|[CMapStringToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicializa la tabla hash.|
|[CMapStringToOb::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Comprueba si la condición de mapa está vacío (no hay elementos).|
|[CMapStringToOb::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Busca un puntero void en función de la clave de un puntero void. El valor de puntero, no la entidad que señala, se usa para la comparación de la clave.|
|[CMapStringToOb::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Devuelve una referencia a la clave asociada con el valor de clave especificado.|
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Quita todos los elementos de esta asignación.|
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Quita un elemento especificado por una clave.|
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Inserta un elemento en el mapa; reemplaza un elemento existente si se encuentra una clave coincidente.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CMapStringToOb::operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Inserta un elemento en el mapa: sustitución de operador para `SetAt`.|

## <a name="remarks"></a>Comentarios

`CMapWordToPtr` incorpora la macro IMPLEMENT_DYNAMIC para admitir el acceso a los tipos de tiempo de ejecución y el volcado en un `CDumpContext` objeto. Si necesita un volcado de elementos de mapa individual, debe establecer la profundidad del contexto de volcado en 1 o mayor.

No se pueden serializar los mapas de puntero a word.

Cuando un `CMapPtrToWord` se elimina el objeto, o cuando se quitan sus elementos, se quitan los punteros y las palabras. No se quitan las entidades al que hace referencia la claves punteros.

Para obtener más información sobre `CMapPtrToWord`, consulte el artículo [colecciones](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMapPtrToWord`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcoll.h

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
