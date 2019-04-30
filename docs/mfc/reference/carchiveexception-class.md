---
title: CArchiveException (clase)
ms.date: 11/04/2016
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
helpviewer_keywords:
- CArchiveException [MFC], CArchiveException
- CArchiveException [MFC], m_cause
- CArchiveException [MFC], m_strFileName
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
ms.openlocfilehash: 731735bccf9225e67d82b1fe90336c92a630b368
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391314"
---
# <a name="carchiveexception-class"></a>CArchiveException (clase)

Representa una condición de excepción de serialización

## <a name="syntax"></a>Sintaxis

```
class CArchiveException : public CException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CArchiveException::CArchiveException](#carchiveexception)|Construye un objeto `CArchiveException`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CArchiveException::m_cause](#m_cause)|Indica la causa de la excepción.|
|[CArchiveException::m_strFileName](#m_strfilename)|Especifica el nombre del archivo para esta condición de excepción.|

## <a name="remarks"></a>Comentarios

La `CArchiveException` clase incluye un miembro de datos públicos que indica la causa de la excepción.

`CArchiveException` los objetos se construyen y se produce dentro de [CArchive](../../mfc/reference/carchive-class.md) funciones miembro. Puede tener acceso a estos objetos dentro del ámbito de un **CATCH** expresión. El código de la causa es independiente del sistema operativo. Para obtener más información sobre el procesamiento de excepciones, vea [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="carchiveexception"></a>  CArchiveException::CArchiveException

Construye un `CArchiveException` objeto, que almacena el valor de *provocar* en el objeto.

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parámetros

*cause*<br/>
Una variable de tipo enumerado que indica el motivo de la excepción. Para obtener una lista de los enumeradores, consulte la [m_cause](#m_cause) miembro de datos.

*lpszArchiveName*<br/>
Señala a una cadena que contiene el nombre de la `CArchive` objeto ocasionando la excepción.

### <a name="remarks"></a>Comentarios

Puede crear un `CArchiveException` en el montón de objeto y producir usted mismo o dejar que la función global [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) controle automáticamente.

No utilice este constructor directamente; en su lugar, llame a la función global `AfxThrowArchiveException`.

##  <a name="m_cause"></a>  CArchiveException::m_cause

Especifica la causa de la excepción.

```
int m_cause;
```

### <a name="remarks"></a>Comentarios

Este miembro de datos es una variable pública de tipo **int**. Sus valores se definen mediante un `CArchiveException` tipo enumerado. A continuación se indican los enumeradores y el significado de cada uno de ellos:

- `CArchiveException::none` Se produjo ningún error.

- `CArchiveException::genericException` Error no especificado.

- `CArchiveException::readOnly` Se intentó escribir en un archivo abierto para la carga.

- `CArchiveException::endOfFile` Se ha llegado al final del archivo al leer un objeto.

- `CArchiveException::writeOnly` Se intentó leer de un archivo abierto para almacenar.

- `CArchiveException::badIndex` Formato de archivo no válido.

- `CArchiveException::badClass` Se intentó leer un objeto en un objeto del tipo incorrecto.

- `CArchiveException::badSchema` Se intentó leer un objeto con una versión diferente de la clase.

    > [!NOTE]
    >  Estos enumeradores de causa de `CArchiveException` son distintos de los enumeradores de causa de `CFileException`.

    > [!NOTE]
    > `CArchiveException::generic` está desusada. Utilice `genericException` en su lugar. Si **genérico** se usa en una aplicación y se compila con/CLR, habrá errores de sintaxis que no son fáciles de descifrar.

##  <a name="m_strfilename"></a>  CArchiveException::m_strFileName

Especifica el nombre del archivo para esta condición de excepción.

```
CString m_strFileName;
```

## <a name="see-also"></a>Vea también

[CException (clase)](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CArchive (clase)](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[Procesamiento de excepciones](../../mfc/reference/exception-processing.md)
