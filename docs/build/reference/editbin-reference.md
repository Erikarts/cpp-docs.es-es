---
title: Referencia de EDITBIN
ms.date: 11/04/2016
f1_keywords:
- editbin
helpviewer_keywords:
- binary data, editing
- object files, modifying
- EDITBIN program
- COFF files, editing
ms.assetid: efdda03b-3dfc-4d31-90e6-caf5b3977914
ms.openlocfilehash: 39fdcfd3221599f20617092118e5cef5267e3d2b
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418794"
---
# <a name="editbin-reference"></a>Referencia de EDITBIN

El Editor de archivos de Microsoft COFF Binary (EDITBIN. (EXE) modifica los archivos binarios de formato de archivo de objeto común (COFF). Puede utilizar EDITBIN para modificar archivos de objetos, archivos ejecutables y bibliotecas de vínculos dinámicos (DLL).

> [!NOTE]
>  Puede iniciar esta herramienta solo desde el símbolo del sistema de Visual Studio. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.

EDITBIN no está disponible para su uso en los archivos producidos con la [/GL](../../build/reference/gl-whole-program-optimization.md) opción del compilador. Las modificaciones en los archivos binarios generados con/GL tendrán que se logra volver a compilar y vincular.

- [Línea de comandos EDITBIN](../../build/reference/editbin-command-line.md)

- [Opciones de EDITBIN](../../build/reference/editbin-options.md)

## <a name="see-also"></a>Vea también

[Herramientas de compilación de C/C++](../../build/reference/c-cpp-build-tools.md)
