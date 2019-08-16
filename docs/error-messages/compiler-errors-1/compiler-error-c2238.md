---
title: Error del compilador C2238
ms.date: 11/04/2016
f1_keywords:
- C2238
helpviewer_keywords:
- C2238
ms.assetid: 3d53060c-d6b7-4603-b9cf-d7c65eb64cd2
ms.openlocfilehash: dde413c2c38e97fe47a0063953d64b0381d313a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301427"
---
# <a name="compiler-error-c2238"></a>Error del compilador C2238

tokens inesperados delante de 'token'

Se encontró un token incorrecto.

El ejemplo siguiente genera la advertencia C2238:

```
// C2238.cpp
// compile with: /c
class v {
virtual: int vvv;   // C2238
};
```