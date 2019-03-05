---
title: Clase CFolderPickerDialog
ms.date: 11/04/2016
f1_keywords:
- CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog::CFolderPickerDialog
helpviewer_keywords:
- CFolderPickerDialog [MFC], CFolderPickerDialog
ms.assetid: 8db01684-dd1d-4e9c-989e-07a2318a8156
ms.openlocfilehash: f1718919a4fe9019ef591d83473c118eba966900
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276187"
---
# <a name="cfolderpickerdialog-class"></a>Clase CFolderPickerDialog

Clase CFolderPickerDialog implementa CFileDialog en el modo de selector de carpeta.

## <a name="syntax"></a>Sintaxis

```
class CFolderPickerDialog : public CFileDialog;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CFolderPickerDialog::~CFolderPickerDialog](#cfolderpickerdialog__~cfolderpickerdialog)|Destructor.|
|[CFolderPickerDialog::CFolderPickerDialog](#cfolderpickerdialog)|Constructor.|

## <a name="remarks"></a>Comentarios

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[CFileDialog](../../mfc/reference/cfiledialog-class.md)

`CFolderPickerDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

##  <a name="cfolderpickerdialog"></a>  CFolderPickerDialog::CFolderPickerDialog

Constructor.

```
explicit CFolderPickerDialog(
    LPCTSTR lpszFolder = NULL,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL,
    DWORD dwSize = 0);
```

### <a name="parameters"></a>Parámetros

*lpszFolder*<br/>
Carpeta inicial.

*dwFlags*<br/>
Una combinación de uno o más marcadores que le permiten personalizar el cuadro de diálogo.

*pParentWnd*<br/>
Un puntero a la ventana de primario o el propietario del objeto de cuadro de diálogo.

*dwSize*<br/>
El tamaño de la estructura OPENFILENAME.

### <a name="remarks"></a>Comentarios

##  <a name="_dtorcfolderpickerdialog"></a>  CFolderPickerDialog::~CFolderPickerDialog

Destructor.

```
virtual ~CFolderPickerDialog();
```

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
