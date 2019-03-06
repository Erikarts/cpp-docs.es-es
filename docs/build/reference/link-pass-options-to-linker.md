---
title: /link (Pasar opciones al vinculador)
ms.date: 11/04/2016
f1_keywords:
- /link
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
ms.openlocfilehash: f5e57a19f337653cdab6f66404b9458e1e7fed0d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412840"
---
# <a name="link-pass-options-to-linker"></a>/link (Pasar opciones al vinculador)

Pasa una o más opciones del vinculador al vinculador.

## <a name="syntax"></a>Sintaxis

```
/link linkeroptions
```

## <a name="arguments"></a>Argumentos

*linkeroptions*<br/>
La opción del vinculador o las opciones que se pasarán al vinculador.

## <a name="remarks"></a>Comentarios

El **/link** opción y sus opciones del vinculador deben aparecer detrás de los nombres de archivo y las opciones de CL. Se requiere un espacio entre **/link** y `linkeroptions`. Para obtener más información, consulte [opciones de configuración del vinculador](../../build/reference/setting-linker-options.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en una página de propiedades del enlazador.

1. Modificar una o varias propiedades.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- No se puede cambiar esta opción del compilador mediante programación.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
