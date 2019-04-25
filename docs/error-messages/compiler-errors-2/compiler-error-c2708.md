---
title: Error del compilador C2708
ms.date: 11/04/2016
f1_keywords:
- C2708
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
ms.openlocfilehash: a128613cabb201142c29b833959924dbf8a6e0ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160963"
---
# <a name="compiler-error-c2708"></a>Error del compilador C2708

'identifier': la longitud de parámetros reales en bytes difiere de la llamada anterior o referencia

Un [__stdcall](../../cpp/stdcall.md) función debe ir precedida de un prototipo. En caso contrario, el compilador interpreta la primera llamada a la función como un prototipo y este error se produce cuando el compilador encuentra una llamada que no coincide.

Para corregir este error, agregue un prototipo de función.