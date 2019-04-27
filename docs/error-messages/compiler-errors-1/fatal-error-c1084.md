---
title: Error irrecuperable C1084
ms.date: 11/04/2016
f1_keywords:
- C1084
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
ms.openlocfilehash: 8c90616165a7b47d4251ace998fd49c613f244b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208820"
---
# <a name="fatal-error-c1084"></a>Error irrecuperable C1084

No se puede leer el archivo tipodearchivo: 'archivo': mensaje

Este error suele deberse a un error en una llamada API del sistema interno realizada por el compilador. El mensaje mostrado cuando se produce este error se genera a menudo, ya sea por [_wcserror_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) o [FormatMessage](/windows/desktop/api/winbase/nf-winbase-formatmessage).

Con los siguientes pasos, puede que resulte más fácil resolver C1084:

- Compruebe que el archivo especificado existe.

- Compruebe que están establecidos los permisos adecuados para acceder al archivo especificado.

- Asegúrese de que cumple las reglas descritas en la sintaxis de línea de comandos [sintaxis de línea de comandos del compilador](../../build/reference/compiler-command-line-syntax.md).

- Asegúrese de que las variables de entorno **TMP** y **TEMP** están correctamente en conjunto, así como los permisos adecuados para tener acceso a los directorios consulte estas variables de entorno. Asegúrese también de que las unidades de disco al que hace referencia el **TMP** y **TEMP** variables de entorno contienen una cantidad suficiente de espacio libre.

- Si en el mensaje se indica “número de archivo incorrecto”, puede que el archivo especificado se estuviera cerrando en primer plano mientras se compilaba en segundo plano.

Después de llevar a cabo los diagnósticos anteriores, realice una compilación limpia.