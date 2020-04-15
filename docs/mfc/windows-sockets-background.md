---
title: 'Windows Sockets: Nociones'
ms.date: 11/04/2016
helpviewer_keywords:
- record-oriented data [MFC]
- e-mail [MFC]
- Internet Protocol Suite
- mail [MFC]
- communications [MFC], domain
- Windows Sockets [MFC], stream sockets
- mail [MFC], programming for
- sockets [MFC], stream sockets
- datagram sockets [MFC]
- SOCKET handle
- data types [MFC], socket
- e-mail [MFC], programming for
- X Window servers
- sequenced data flow
- stream sockets [MFC]
ms.assetid: f60d4ed2-bf23-4a0e-98d2-fee77e8473dd
ms.openlocfilehash: 1c4a6dc6740660d1097785578cdac355983cad18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360129"
---
# <a name="windows-sockets-background"></a>Windows Sockets: Nociones

En este artículo se explica la naturaleza y la finalidad de Windows Sockets. También incluye lo siguiente:

- [Define el término "socket".](#_core_definition_of_a_socket)

- [Describe el tipo](#_core_the_socket_data_type)de datos de identificador SOCKET .

- [Describe los usos para sockets](#_core_uses_for_sockets).

La especificación de Windows Sockets define una interfaz de programación de red compatibles a nivel binario para Microsoft Windows. Windows Sockets se basa en la implementación de sockets de UNIX en la distribución de software de Berkeley (BSD, versión 4.3) de la Universidad de California en Berkeley. La especificación incluye rutinas de socket de estilo BSD y extensiones específicas de Windows. El uso de Windows Sockets permite a la aplicación comunicarse a través de cualquier red que se ajuste a la API de Windows Sockets. En Win32, Windows Sockets proporciona seguridad para subprocesos.

Muchos proveedores de software de red admiten Windows Sockets en los protocolos de red, entre los que se incluyen el Protocolo de control de transmisión/Protocolo de Internet (TCP/IP), Xerox Network System (XNS), protocolo DECNet de Digital Equipment Corporation, Internet Packet Exchange/Sequenced Packed Exchange (IPX/SPX) de Novell Corporation y otros. Aunque la actual especificación de Windows Sockets define la abstracción de sockets para TCP/IP, cualquier protocolo de red puede cumplir con Windows Sockets si proporciona su propia versión de la biblioteca de vínculos dinámicos (DLL) que implementa Windows Sockets. Entre los ejemplos de aplicaciones comerciales escritas con Windows Sockets se incluyen los servidores X de Windows, los emuladores de terminales y los sistemas de correo electrónico.

> [!NOTE]
> El propósito de Windows Sockets es reducir la red subyacente para que no sea necesario estar bien informado sobre esa red y para que la aplicación pueda ejecutarse en cualquier red que admita sockets. Por consiguiente, en esta documentación no se analizan los detalles de los protocolos de red.

La biblioteca Microsoft Foundation Class (MFC) proporciona dos clases para admitir la programación con la API de Windows Sockets. Una de estas clases, `CSocket`, proporciona un mayor nivel de abstracción para simplificar la programación de las comunicaciones de red.

La especificación Windows Sockets: Interfaz abierta para la informática de red en Microsoft Windows, ahora en la versión 1.1, la desarrolló como estándar abierto de red un gran grupo de personas y compañías de la comunidad de TCP/IP y está libremente disponible para su uso. El modelo de programación de sockets admite actualmente un "dominio de comunicación", que utiliza el conjunto de protocolos de Internet. La especificación está disponible en el Windows SDK.

> [!TIP]
> Dado que los sockets utilizan el conjunto de protocolos de Internet, son la ruta preferida para las aplicaciones que admiten comunicaciones compatibles con Internet en la "autopista de la información".

## <a name="definition-of-a-socket"></a><a name="_core_definition_of_a_socket"></a>Definición de un Socket

Un socket es un extremo de comunicación, es decir, un objeto a través del cual una aplicación de Windows Sockets envía o recibe los paquetes de datos a través de una red. Un socket tiene un tipo y se asocia a un proceso en ejecución y puede tener un nombre. Actualmente, los sockets intercambian datos normalmente solo con otros sockets del mismo "dominio de comunicación", que utiliza el conjunto de protocolos de Internet.

Ambas clases de sockets son bidireccionales; son flujos de datos que pueden comunicarse en ambas direcciones simultáneamente (dúplex completo).

Hay dos tipos de socket disponibles:

- Sockets de secuencias

   Los sockets de secuencias proporcionan un flujo de datos sin límites de registro: una secuencia de bytes. Se garantiza que las secuencias se entreguen y estén correctamente ordenadas y no duplicadas.

- Sockets de datagrama

   Los sockets de datagrama admiten un flujo de datos orientado a registros cuya entrega no se garantiza y que pueden no estar secuenciados tal como se envían o sin duplicar.

"Secuenciado" significa que los paquetes se entregarán en el orden enviado. "Sin duplicar" significa que un paquete determinado solo se obtiene una vez.

> [!NOTE]
> En algunos protocolos de red, como XNS, las secuencias pueden estar orientadas a registros, como secuencias de registros en lugar de secuencias de bytes. Sin embargo, en el protocolo TCP/IP más común, se trata de secuencias de bytes. Windows Sockets proporciona un nivel de independiente de la abstracción del protocolo subyacente.

Para obtener información acerca de estos tipos y qué tipo de socket se debe usar en qué situaciones, vea [Windows Sockets: Stream Sockets](../mfc/windows-sockets-stream-sockets.md) y Windows [Sockets: Datagram Sockets](../mfc/windows-sockets-datagram-sockets.md).

## <a name="the-socket-data-type"></a><a name="_core_the_socket_data_type"></a>El tipo de datos SOCKET

Cada objeto de socket de MFC encapsula un identificador para un objeto de Windows Sockets. El tipo de datos de este identificador es **SOCKET**. Un identificador **SOCKET** es `HWND` análogo al for a window. Las clases de socket de MFC proporcionan operaciones en el identificador encapsulado.

El tipo de datos **SOCKET** se describe en detalle en el Windows SDK. Vea "Tipo de datos y valores de error de socket" en Windows Sockets.

## <a name="uses-for-sockets"></a><a name="_core_uses_for_sockets"></a>Usos para Sockets

Los sockets son muy útiles en al menos tres contextos de comunicación:

- Modelos cliente/servidor.

- Escenarios punto a punto, como las aplicaciones de mensajería.

- Realizar llamadas a procedimiento remoto (RPC) y hacer que la aplicación receptora interprete un mensaje como una llamada de función.

> [!TIP]
> El caso ideal para utilizar sockets de MFC es cuando se escribe en ambos extremos de la comunicación y se usa MFC en ambos extremos. Para obtener más información sobre este tema, incluido cómo administrar el caso cuando se comunica con aplicaciones que no son MFC, vea [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md).

Para obtener más información, consulte Especificación de Windows Sockets: **ntohs**, **ntohl**, **htons**, **htonl**. También puede consultar los temas siguientes:

- [Windows Sockets: Usar sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Ejemplo de sockets que usan archivos](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

## <a name="see-also"></a>Consulte también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)
