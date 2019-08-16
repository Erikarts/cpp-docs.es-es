---
title: Error grave de NMAKE U1056
ms.date: 11/04/2016
f1_keywords:
- U1056
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
ms.openlocfilehash: b15b14c04dd91ae648ea4311612c122f04f90477
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367270"
---
# <a name="nmake-fatal-error-u1056"></a>Error grave de NMAKE U1056

no se puede encontrar el procesador de comandos

El procesador de comandos no estaba en la ruta de acceso especificada en el **COMSPEC** o **ruta** variables de entorno.

NMAKE utiliza COMMAND.COM o CMD. EXE como un procesador de comandos al ejecutar comandos. Busca primero el procesador de comandos en la ruta de acceso establecido **COMSPEC**. Si **COMSPEC** no existe, los directorios especificados en las búsquedas NMAKE **ruta de acceso**.