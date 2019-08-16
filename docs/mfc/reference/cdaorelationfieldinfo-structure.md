---
title: CDaoRelationFieldInfo (Estructura)
ms.date: 11/04/2016
f1_keywords:
- CDaoRelationFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationFieldInfo structure [MFC]
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
ms.openlocfilehash: 85dd853a9aae41a87bbe7ef5c69e22846678cf8a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206113"
---
# <a name="cdaorelationfieldinfo-structure"></a>CDaoRelationFieldInfo (Estructura)

El `CDaoRelationFieldInfo` estructura contiene información sobre un campo en una relación definida para objetos de acceso a datos (DAO).

## <a name="syntax"></a>Sintaxis

```
struct CDaoRelationFieldInfo
{
    CString m_strName;           // Primary
    CString m_strForeignName;    // Primary
};
```

#### <a name="parameters"></a>Parámetros

*m_strName*<br/>
El nombre del campo en la tabla principal de la relación.

*m_strForeignName*<br/>
El nombre del campo en la tabla externa de la relación.

## <a name="remarks"></a>Comentarios

Un objeto de relación DAO especifica los campos de una tabla principal y los campos de una tabla externa que definen a la relación. Las referencias a principal en la definición de estructura anterior indican cómo se devuelve la información en el `m_pFieldInfos` miembro de un [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) objeto obtenido mediante una llamada a la [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)función miembro de clase `CDaoDatabase`.

Objetos de relación y los objetos de campo de relación no están representados por una clase MFC. En su lugar, DAO objetos objetos MFC subyacentes de la clase [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) contienen una colección de objetos de relación, llama a la colección de relaciones. Cada objeto de relación, a su vez, contiene una colección de objetos de campo de la relación. Cada objeto de campo de la relación correlaciona un campo de la tabla principal con un campo en la tabla externa. En conjunto, los objetos de campo de la relación definen un grupo de campos de cada tabla, que conjuntamente definen a la relación. `CDaoDatabase` le permite acceder a los objetos de relación con un `CDaoRelationInfo` objeto mediante una llamada a la `GetRelationInfo` función miembro. El `CDaoRelationInfo` objeto, a continuación, tiene un miembro de datos, `m_pFieldInfos`, que señala a una matriz de `CDaoRelationFieldInfo` objetos.

Llame a la [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) función miembro de la que contiene `CDaoDatabase` en cuya almacenan está interesado en el objeto de relación es la colección de relaciones de objeto. A continuación, obtener acceso a la `m_pFieldInfos` miembro de la [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) objeto. `CDaoRelationFieldInfo` También define un `Dump` se basa en función de miembro en modo de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoRelationFieldInfo` objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoRelationInfo (estructura)](../../mfc/reference/cdaorelationinfo-structure.md)
