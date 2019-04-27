---
title: CDaoRelationInfo (Estructura)
ms.date: 06/25/2018
f1_keywords:
- CDaoRelationInfo
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationInfo structure [MFC]
ms.assetid: 92dda090-fe72-4090-84ec-429498a48aad
ms.openlocfilehash: 7d1c86732966d8222582dc6d4527af89963a5cdc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152831"
---
# <a name="cdaorelationinfo-structure"></a>CDaoRelationInfo (Estructura)

El `CDaoRelationInfo` estructura contiene información sobre una relación definida entre los campos de dos tablas en un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto.

## <a name="syntax"></a>Sintaxis

```cpp
struct CDaoRelationInfo
{
    CDaoRelationInfo();                     // Constructor
    CString m_strName;                      // Primary
    CString m_strTable;                     // Primary
    CString m_strForeignTable;              // Primary
    long m_lAttributes;                     // Secondary
    CDaoRelationFieldInfo* m_pFieldInfos;   // Secondary
    short m_nFields;                        // Secondary
    // Below the // Implementation comment:
    // Destructor, not otherwise documented
};
```

#### <a name="parameters"></a>Parámetros

*m_strName*<br/>
Nombres de forma exclusiva el objeto de relación. Para obtener más información, vea el tema "Nombre de la propiedad" en la Ayuda de DAO.

*m_strTable*<br/>
Nombre de la tabla principal en la relación.

*m_strForeignTable*<br/>
Nombre de la tabla externa en la relación. Una tabla externa es una tabla que se usa para contener las claves externas. Por lo general, usa una tabla externa para imponer la integridad referencial. La tabla externa está normalmente en el lado "varios" de una relación uno a varios. Algunos ejemplos de tablas externas son tablas que contienen códigos para los Estados estadounidenses o canadienses provincias o de pedidos del cliente.

*m_lAttributes*<br/>
Contiene información sobre el tipo de relación. El valor de este miembro puede ser cualquiera de las siguientes acciones:

- `dbRelationUnique` La relación es uno a uno.

- `dbRelationDontEnforce` Relación no es aplicar (ninguna integridad referencial).

- `dbRelationInherited` Relación existe en una base de datos no actual que contiene las dos tablas asociadas.

- `dbRelationLeft` La relación es una combinación izquierda. Una combinación externa izquierda incluye todos los registros de la primera (izquierda) de dos tablas, incluso si no existen valores coincidentes para los registros en la segunda tabla (derecha).

- `dbRelationRight` La relación es una combinación derecha. Una combinación externa derecha incluye todos los registros de la segunda (derecha) de dos tablas, incluso si no existen valores coincidentes para los registros en la primera tabla (izquierda).

- `dbRelationUpdateCascade` Las actualizaciones se realizará en cascada.

- `dbRelationDeleteCascade` Las eliminaciones se realizará en cascada.

*m_pFieldInfos*<br/>
Un puntero a una matriz de [CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md) estructuras. La matriz contiene un objeto para cada campo de la relación. El `m_nFields` miembro de datos proporciona un recuento de los elementos de matriz.

*m_nFields*<br/>
El número de `CDaoRelationFieldInfo` objetos en el `m_pFieldInfos` miembro de datos.

## <a name="remarks"></a>Comentarios

Las referencias a principal y secundaria anterior indican cómo devuelve la información de la [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) función miembro de clase `CDaoDatabase`.

Objetos de relación no están representados por una clase MFC. En su lugar, el objeto DAO subyacente de un objeto MFC de la `CDaoDatabase` clase mantiene una colección de objetos de relación: `CDaoDatabase` proporciona funciones de miembro para tener acceso a algunos elementos individuales de información de la relación, o bien pueden tener acceso a ellos a la vez con un `CDaoRelationInfo` objeto mediante una llamada a la `GetRelationInfo` función de miembro del objeto contenedor base de datos.

Información recuperada por el [CDaoDatabase::GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) función miembro se almacena en un `CDaoRelationInfo` estructura. `CDaoRelationInfo` También define un `Dump` se basa en función de miembro en modo de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoRelationInfo` objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="see-also"></a>Vea también

[CDaoRelationFieldInfo (estructura)](../../mfc/reference/cdaorelationfieldinfo-structure.md)
