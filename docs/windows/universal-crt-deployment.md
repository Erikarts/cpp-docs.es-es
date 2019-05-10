---
title: Implementación de CRT universal
ms.date: 05/11/2018
helpviewer_keywords:
- deploying the CRT [C++]
- application CRT deployment [C++]
ms.openlocfilehash: 7952d2ec6e8f502b0edf776811a492c67f495cce
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857229"
---
# <a name="universal-crt-deployment"></a>Implementación de CRT universal

Desde Visual Studio .NET hasta Visual Studio 2013, en cada versión principal del compilador y las herramientas de C++ se ha incluido una versión nueva e independiente de la Biblioteca en tiempo de ejecución de C (CRT) de Microsoft. Estas versiones independientes de la biblioteca CRT eran independientes entre ellas y, a diferentes niveles, incompatibles. Por ejemplo, la biblioteca CRT que se usaba en Visual Studio 2012 era la versión 11, denominada msvcr110.dll, y la biblioteca CRT que se usaba en Visual Studio 2013 era la versión 12, denominada msvcr120.dll. A partir de Visual Studio 2015, esto ya no es así. En Visual Studio 2015 y versiones posteriores de Visual Studio se usa CRT universal.

CRT universal es un componente del sistema operativo Microsoft Windows. Se incluye como parte del sistema operativo en Windows 10 y está disponible a través de Windows Update para sistemas operativos anteriores, de Windows Vista a Windows 8.1. Además, se admite la implementación local de CRT universal, con algunas restricciones.

## <a name="central-deployment"></a>Implementación central

El método preferido para instalar de forma centralizada CRT universal consiste en usar Microsoft Windows Update. CRT universal es una actualización recomendada para todos los sistemas operativos Microsoft Windows compatibles, por lo que de forma predeterminada, en la mayoría de los equipos se instala como parte del proceso de actualización habitual. La versión inicial de la biblioteca CRT universal fue [KB2999226](https://support.microsoft.com/kb/2999226); se realizó una actualización posterior con varias correcciones de errores en [KB3118401](https://support.microsoft.com/kb/3118401), y se han realizado actualizaciones adicionales con más correcciones de errores y características nuevas. Para obtener las actualizaciones más recientes, busque "tiempo de ejecución de C universal" o "CRT universal" en [support.microsoft.com](https://support.microsoft.com).

No en todos los equipos Microsoft Windows se instalan las actualizaciones periódicamente mediante Windows Update, y es posible que en algunos no se instalen todas las actualizaciones recomendadas. Para admitir el uso de las aplicaciones compiladas con los conjuntos de herramientas de C++ para Visual Studio 2015 y versiones posteriores en esos equipos, existen paquetes redistribuibles de CRT universal para la distribución sin conexión. Estos archivos redistribuibles se pueden descargar desde uno de los vínculos de KB anteriores. Tenga en cuenta que los archivos redistribuibles de CRT universal requieren que el equipo se haya actualizado con el Service Pack actual. Por tanto, por ejemplo, el paquete redistribuible para Windows 7 solo se instalará en Windows 7 SP1, no en Windows 7 RTM.

Dado que el CRT Universal es una dependencia fundamental de la C++ bibliotecas, el objeto Visual C++ (VCRedist) redistribuible instala la versión inicial de CRT Universal (versión 10.0.10240) en equipos que no tienen una versión instalada. Esta versión es suficiente para satisfacer la C++ las dependencias de biblioteca. Si la aplicación depende de una versión más reciente de CRT Universal, debe usar Windows Update para poner el equipo completamente actualizado o instalan esa versión explícitamente. Es mejor tener ya instalado a través de Windows Update o a través de MSU antes de instalar VCRedist, para evitar posibles Universal C Runtime varios reinicios necesarios.

No todos los sistemas operativos son aptos para la más reciente Universal C Runtime a través de Windows Update. En Windows 10, la versión implementada de forma centralizada coincide con la versión del sistema operativo. Además, para actualizar el tiempo de ejecución de C Universal debe actualizar el sistema operativo. Para Windows Vista a través de Windows 8.1, la más reciente disponible Universal C Runtime actualmente se basa en la versión incluida en la actualización de aniversario de Windows 10, con correcciones adicionales (versión 10.0.14393).

## <a name="local-deployment"></a>Implementación local

Se admite la implementación local de aplicación de CRT universal, aunque no se recomienda por motivos de rendimiento y seguridad.  Los archivos DLL para la implementación local se incluyen como parte de Windows SDK, en el subdirectorio Windows Kits\\10\\Redist\\ucrt\\DLLs, por cada arquitectura de equipo. Los archivos DLL necesarios incluyen ucrtbase.dll y un conjunto de archivos DLL de reenviador APISet denominado api-ms-win-\*.dll. El conjunto de archivos DLL necesarios en cada sistema operativo varía, por lo que se recomienda incluirlos todos cuando se realice la implementación local.

En la implementación local hay que tener en cuenta dos restricciones:

- En Windows 10, siempre se usa CRT universal en el directorio del sistema, incluso si una aplicación incluye una copia local de la aplicación de CRT universal. Esto ocurre incluso si la copia local de CRT universal es más reciente. El motivo es que CRT universal es un componente esencial del sistema operativo en Windows 10.

- En las versiones de Windows anteriores a Windows 8, CRT universal no se puede empaquetar de manera local con un complemento que se encuentre en otro directorio que no sea el que contiene el archivo ejecutable principal de la aplicación. En este caso, los archivos DLL de reenviador APISet no pueden resolver correctamente el archivo ucrtbase.dll. Algunas soluciones alternativas recomendadas son las siguientes:

  - Vincular CRT universal de forma estática,
  - Implementar CRT universal de forma centralizada, o bien
  - Colocar los archivos de CRT universal en el mismo directorio que la aplicación.

## <a name="deployment-on-microsoft-windows-xp"></a>Implementación en Microsoft Windows XP

En Visual Studio 2015 y Visual Studio 2017 se sigue admitiendo el desarrollo de software para su uso en Microsoft Windows XP. Para ello, una versión de CRT universal funciona en Microsoft Windows XP. El soporte técnico principal o ampliado para el sistema operativo Microsoft Windows XP ya ha finalizado, por lo que la implementación central de CRT universal en Microsoft Windows XP es diferente a la de otros sistemas operativos.

Cuando se instala el paquete redistribuible de Visual C++ en Windows XP, se instala directamente CRT universal y todas sus dependencias en el directorio del sistema, sin necesidad de instalar ni depender de ninguna actualización de Windows. Los módulos de combinación redistribuibles, los archivos Microsoft_VC*versión*_CRT_\*.msm, hacen lo mismo.

La implementación local de CRT universal en Windows XP es la misma que la de otros sistemas operativos compatibles.

## <a name="see-also"></a>Vea también

- [Implementación en Visual C++](deployment-in-visual-cpp.md)
