---
title: Inicialización y terminación del motor de bases de datos DAO
ms.date: 11/04/2016
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 1b8186627f00105cf782586060b41ae0fb627d76
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611938"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Inicialización y terminación del motor de bases de datos DAO

Al utilizar objetos DAO de MFC, el motor de base de datos DAO primero debe inicializar y, a continuación, finaliza antes de que se cierra la aplicación o DLL. Las dos funciones, `AfxDaoInit` y `AfxDaoTerm`, realizar estas tareas.

### <a name="dao-database-engine-initialization-and-termination"></a>Inicialización y terminación del motor de bases de datos DAO

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|Inicializa el motor de base de datos DAO.|
|[AfxDaoTerm](#afxdaoterm)|Finaliza el motor de base de datos DAO.|

##  <a name="afxdaoinit"></a>  AfxDaoInit

Esta función inicializa el motor de base de datos DAO.

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>Comentarios

En la mayoría de los casos, no es necesario llamar a `AfxDaoInit` porque la aplicación llama automáticamente a él cuando sea necesario.

Para obtener información relacionada y para obtener un ejemplo de llamada `AfxDaoInit`, consulte [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

##  <a name="afxdaoterm"></a>  AfxDaoTerm

Esta función termina el motor de base de datos DAO.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>Comentarios

Normalmente, solo necesita llamar a esta función en una DLL de MFC; normal una aplicación llama automáticamente a `AfxDaoTerm` cuando sea necesario.

En los archivos DLL de MFC estándar, llame a `AfxDaoTerm` antes el `ExitInstance` función, pero después de que se han destruido todos los objetos DAO de MFC.

Para obtener información relacionada, consulte [Nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdao.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
