---
title: Sintaxis de nombres de archivo de CL
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- syntax, compiler filename
- paths, CL compiler filename syntax
- cl.exe compiler, filename syntax
- extensions, specifying to compiler
- file names [C++], CL compiler
- file names [C++]
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
ms.openlocfilehash: d2dd51370fd346c4cd7dad7bb97bfa76a9f759d9
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420731"
---
# <a name="cl-filename-syntax"></a>Sintaxis de nombres de archivo de CL

CL acepta archivos con nombres que siguen las convenciones de nomenclatura FAT, HPFS o NTFS. Todos los nombres de archivo pueden incluir una ruta de acceso completa o parcial. Una ruta de acceso completa incluye un nombre de unidad y uno o más nombres de directorio. CL acepta nombres de archivo separan por barras diagonales inversas (\\) o barras diagonales (/). Los nombres de archivo que contienen espacios deben encerrarse entre comillas dobles. Una ruta de acceso parcial omite el nombre de la unidad, que CL supone que es la unidad actual. Si no se especifica una ruta de acceso, CL supone que el archivo se encuentra en el directorio actual.

La extensión del nombre de archivo determina cómo se procesan los archivos. Los archivos de C y C++, que tienen la extensión .c, .cxx o .cpp, se compilan. Otros archivos, incluidos los archivos .obj, las bibliotecas (.lib) y los archivos de definición de módulos (.def), se transfieren al vinculador sin procesarse.

## <a name="see-also"></a>Vea también

[Sintaxis de la línea de comandos del compilador](../../build/reference/compiler-command-line-syntax.md)
