---
title: automatización
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers, about Automation servers
- clients, Automation
- programmatic control [MFC]
- properties [MFC], Automation
- MFC, COM support
- OLE Automation
- Automation
- servers [MFC], Automation
- Automation clients
- sample applications [MFC], Automation
- methods [MFC]
- passing parameters, Automation
- Automation method [MFC]
- Automation, passing parameters
- Automation property [MFC]
- MFC COM, Automation
- methods [MFC], Automation
ms.assetid: 329117f0-c1aa-4680-a901-bfb71277dfba
ms.openlocfilehash: b26a08bbe9ef9b9151910871201abe05a44d2f6c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265575"
---
# <a name="automation"></a>automatización

La automatización (antes conocida como automatización OLE) permite que una aplicación manipule objetos implementados en otra aplicación o exponga objetos para que se puedan manipular.

Un [servidor de automatización](../mfc/automation-servers.md) es una aplicación (un tipo de servidor COM) que expone su funcionalidad a través de interfaces COM a otras aplicaciones, denominadas [clientes de automatización](../mfc/automation-clients.md). La exposición permite a los clientes de automatización automatizar determinadas funciones al acceder a objetos directamente y usar los servicios que proporcionan.

Los servidores y clientes de automatización usan interfaces COM que se derivan siempre de `IDispatch` y toman y devuelven un conjunto específico de tipos de datos denominados tipos de automatización. Puede automatizar cualquier objeto que exponga una interfaz de automatización, con lo que proporciona métodos y propiedades a los que puede acceder desde otras aplicaciones. La automatización está disponible para objetos COM y OLE. El objeto automatizado puede ser local o remoto (en otra máquina accesible a través de una red); por lo tanto, hay dos categorías de automatización:

- Automatización (local).

- Automatización remota (a través de una red, mediante COM distribuido o DCOM).

La exposición de objetos es beneficiosa si las aplicaciones proporcionan funcionalidad útil para otras aplicaciones. Por ejemplo, un control ActiveX es un tipo de servidor de automatización; la aplicación que hospeda el control ActiveX es el cliente de automatización de ese control.

Como otro ejemplo, un procesador de textos podría exponer su funcionalidad de revisión ortográfica a otros programas. La exposición de objetos permite a los proveedores mejorar sus aplicaciones mediante la funcionalidad lista para usar de otras aplicaciones. De esta manera, la automatización aplica algunos de los principios de la programación orientada a objetos, como la reusabilidad y la encapsulación, en el nivel de las propias aplicaciones.

Más importante es la compatibilidad que la automatización proporciona a los usuarios y a los proveedores de soluciones. Al exponer la funcionalidad de la aplicación mediante una interfaz común bien definida, la automatización permite generar soluciones completas en un único lenguaje de programación general, como Microsoft Visual Basic, en lugar de en lenguajes distintos de macro específicos de la aplicación.

Muchas aplicaciones comerciales, como Microsoft Excel y Microsoft Visual C++, permiten automatizar gran parte de su funcionalidad. Por ejemplo, en Visual C++, puede escribir macros de VBScript para automatizar las compilaciones, aspectos de edición o tareas de depuración de código.

##  <a name="_core_passing_parameters_in_automation"></a> Pasar parámetros en la automatización

Una dificultad a la hora de crear métodos de automatización es ayudar a proporcionar un mecanismo uniforme "seguro" para pasar datos entre clientes y servidores de automatización. La automatización usa el tipo **VARIANT** para pasar datos. El tipo **VARIANT** es una unión etiquetada. Tiene un miembro de datos para el valor (es decir, una unión anónima C++) y un miembro de datos que indica el tipo de información almacenada en la unión. El **VARIANT** tipo admite varios tipos de datos estándar: enteros de 2 y 4 bytes, números de punto flotante de 4 y 8 bytes, cadenas y valores booleanos. Además, admite la **HRESULT** (códigos de error OLE), **moneda** (un tipo numérico punto fijo), y **fecha** tipos (fecha y hora absolutas), así como punteros a `IUnknown` y `IDispatch` interfaces.

El tipo **VARIANT** se encapsula en la clase [COleVariant](../mfc/reference/colevariant-class.md) . Las clases auxiliares **CURRENCY** y **DATE** están encapsuladas en las clases [COleCurrency](../mfc/reference/colecurrency-class.md) y [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) .

## <a name="automation-samples"></a>Ejemplos de automatización

- [AUTOCLIK](../visual-cpp-samples.md) Use este ejemplo para aprender técnicas de automatización y como base para aprender sobre automatización remota.

- [ACDUAL](../visual-cpp-samples.md) Agrega interfaces duales a una aplicación de servidor de automatización.

- [CALCDRIV](../visual-cpp-samples.md) Aplicación de cliente de automatización que controla MFCCALC.

- [INPROC](../visual-cpp-samples.md) Ilustra una aplicación de servidor de automatización en proceso.

- [IPDRIVE](../visual-cpp-samples.md) Aplicación de cliente de automatización que controla INPROC.

- [MFCCALC](../visual-cpp-samples.md) Muestra una aplicación de cliente de automatización.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Clientes de automatización](../mfc/automation-clients.md)

- [Servidores de automatización](../mfc/automation-servers.md)

- [OLE](../mfc/ole-in-mfc.md)

- [tecnología activa](../mfc/mfc-com.md)

## <a name="what-do-you-want-to-do"></a>Qué quieres hacer

- [Agregar una clase de automatización](../mfc/automation-servers.md)

- [Usar bibliotecas de tipos](../mfc/automation-clients-using-type-libraries.md)

- [Acceder a servidores de automatización](../mfc/automation-servers.md)

- [Escribir clientes de automatización en C++](../mfc/automation-clients.md)

## <a name="see-also"></a>Vea también

[MFC COM](../mfc/mfc-com.md)
