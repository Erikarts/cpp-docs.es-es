---
title: Advertencia del compilador (nivel 3) C4622
ms.date: 11/04/2016
f1_keywords:
- C4622
helpviewer_keywords:
- C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
ms.openlocfilehash: 88a41c7f9edb1d2a9f6d4547336a77bd5e362882
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401753"
---
# <a name="compiler-warning-level-3-c4622"></a>Advertencia del compilador (nivel 3) C4622

Reemplazando la información de depuración formada durante la creación del encabezado precompilado en el archivo objeto: 'file'

Se perdió la información de CodeView del archivo especificado al compilarse con la opción [/Yu](../../build/reference/yu-use-precompiled-header-file.md) (use encabezados precompilado.).

Cambie el nombre del archivo objeto (mediante [/fo](../../build/reference/fo-object-file-name.md)) al crear o usar el archivo de encabezado precompilado y vincúlelo con el nuevo archivo de objeto.