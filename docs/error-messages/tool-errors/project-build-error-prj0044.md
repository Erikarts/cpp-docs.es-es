---
title: Error PRJ0044 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0044
helpviewer_keywords:
- PRJ0044
ms.assetid: 5d78c45a-f9e9-4d2b-a3b6-5a5d1421ab84
ms.openlocfilehash: 9321bb500f69c4d79da45ef9d74bc1644fb90280
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812166"
---
# <a name="project-build-error-prj0044"></a>Error PRJ0044 al compilar el proyecto

La propiedad 'Dependencias adicionales' para la regla de compilación personalizada 'rule' asignada al archivo 'archivo' no es válida. La propiedad contenía una cadena 'string' que se evalúa en 'value'.

El **dependencias adicionales** propiedad evaluado como una cadena vacía, o en una cadena que contiene caracteres no válidos (es decir, cualquier carácter que no pueden estar en un nombre de archivo o directorio). Las reglas de compilación personalizadas necesitan la salida de la acción de compilación.

Para obtener más información, consulte [Specifying Custom Build Tools](../../build/specifying-custom-build-tools.md).

## <a name="see-also"></a>Vea también

[Errores y advertencias de compilación del proyecto (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)