---
title: Error recuperable A2133 de ML
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2133
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
ms.openlocfilehash: 9e13dd48c77b9574229023e3cfc4cc2f2221d153
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62201215"
---
# <a name="ml-nonfatal-error-a2133"></a>Error recuperable A2133 de ML

**registrar valor sobrescrito INVOKE**

Un registro que se pasó como argumento a un procedimiento, pero el código generado por [INVOKE](../../assembler/masm/invoke.md) pasar otros argumentos destruye el contenido del registro.

Los registros AX, AL, AH, EAX, DX, DL, DH y EDX pueden utilizarse el ensamblador para realizar la conversión de datos.

Use un registro diferente.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>