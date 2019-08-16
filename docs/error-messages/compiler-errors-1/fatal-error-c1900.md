---
title: Error irrecuperable C1900
ms.date: 11/04/2016
f1_keywords:
- C1900
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
ms.openlocfilehash: c4622dd4552f7bfcc822a3aab4d5783146d68ac7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165728"
---
# <a name="fatal-error-c1900"></a>Error irrecuperable C1900

> IL no coinciden '*tool1*'version'*Número1*'y'*tool2*'version'*número2*'

Las herramientas ejecutadas en varias transferencias del compilador no coinciden. *Número1* y *número2* hacen referencia a las fechas de los archivos. Por ejemplo, en la transferencia 1, el front-end del compilador ejecuta (c1.dll) y, en la transferencia 2, el back-end del compilador ejecuta (c2.dll). Las fechas de los archivos deben coincidir.

Para corregir este problema, asegúrese de que se han aplicado todas las actualizaciones a Visual Studio. Si el problema continúa, use **programas y características** en el Panel de Control de Windows para reparar o reinstalar Visual Studio.