---
title: /RELEASE (Establecer la suma de comprobación)
ms.date: 11/04/2016
f1_keywords:
- /release
- VC.Project.VCLinkerTool.SetChecksum
helpviewer_keywords:
- -RELEASE linker option
- /RELEASE linker option
- checksum setting
- RELEASE linker option
ms.assetid: 93bcadf4-29ac-4824-914b-6997e3751d22
ms.openlocfilehash: 1dc09b38beeb763733f8fa6a8ffa972059b30e03
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "57819473"
---
# <a name="release-set-the-checksum"></a>/RELEASE (Establecer la suma de comprobación)

```
/RELEASE
```

## <a name="remarks"></a>Comentarios

La opción /RELEASE establece la suma de comprobación en el encabezado de un archivo .exe.

El sistema operativo requiere la suma de comprobación para los controladores de dispositivos. Establecer la suma de comprobación para las versiones de los controladores de dispositivos para garantizar la compatibilidad con futuros sistemas operativos.

La opción /RELEASE se establece de forma predeterminada cuando la [/SUBSYSTEM: Native](subsystem-specify-subsystem.md) se especifica la opción.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **avanzadas** página de propiedades.

1. Modificar el **establecer suma de comprobación** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SetChecksum%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
