---
title: Configuraciones regionales y páginas de códigos
ms.date: 11/04/2016
helpviewer_keywords:
- locales [C++], about locales
- locale IDs [C++]
- locales [C++]
- code pages [C++]
- code pages [C++], dynamically changing
- character sets [C++], code pages
- multibyte code pages [C++]
- character sets [C++], locales
- localization [C++], code pages
- localization [C++], locales
- code pages [C++], locales
- conventions [C++], international character support
ms.assetid: bd937361-b6d3-4c98-af95-beb7c903187b
ms.openlocfilehash: c0cfc7f192b65738984feb1933ea720fdf18fc6d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410647"
---
# <a name="locales-and-code-pages"></a>Configuraciones regionales y páginas de códigos

Un identificador de configuración regional refleja el idioma y las convenciones locales de una determinada zona geográfica. Un idioma determinado se puede hablar en varios países o regiones; por ejemplo, el portugués se habla en Portugal y Brasil. A la inversa, una región o un país pueden tener más de un idioma oficial. Por ejemplo, Canadá tiene dos idiomas: Inglés y francés. Por lo tanto, Canadá tiene dos configuraciones regionales distintas: Canadá en inglés y francés de Canadá. Entre las categorías dependientes de la configuración regional se encuentran el formato de fechas y el formato de presentación de valores de moneda.

El idioma determina las convenciones de formato de datos y texto, mientras que el país o la región determinan las convenciones locales. Cada idioma tiene una asignación única, representada por páginas de códigos, que incluye caracteres distintos de los del alfabeto (como los signos de puntuación y los números). Una página de códigos es un juego de caracteres y está relacionada con el idioma. Por lo tanto, un [configuración regional](../c-runtime-library/locale.md) es una combinación única de idioma, país o región y página de códigos. La configuración de página de configuración regional y el código puede cambiarse en tiempo de ejecución mediante una llamada a la [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) función.

Idiomas distintos pueden utilizar páginas de códigos distintas. Por ejemplo, la página de códigos ANSI 1252 se utiliza para el inglés y para la mayoría de idiomas europeos, mientras que la página de códigos ANSI 932 se utiliza para los caracteres Kanji del japonés. La práctica totalidad de páginas de códigos comparten el juego de caracteres ASCII para los 128 caracteres inferiores (de 0x00 a 0x7F).

Una página de códigos de un solo byte se puede representar en una tabla (con 256 entradas) como una asignación de valores de byte a caracteres (incluidos números y signos de puntuación), o glifos. Una página de códigos multibyte también se puede representar como una tabla de gran tamaño (con 64.000 entradas) de valores de doble byte a caracteres. Sin embargo, en la práctica, normalmente se representan como una tabla para los primeros 256 caracteres (un solo byte) y como intervalos para los valores de doble byte.

Para obtener más información sobre las páginas de códigos, vea [Code Pages](../c-runtime-library/code-pages.md).

La biblioteca en tiempo de ejecución de C tiene dos tipos de páginas de códigos internas: regionales y multibyte. Puede cambiar la página de códigos actual durante la ejecución del programa (consulte la documentación de la [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) y [_setmbcp](../c-runtime-library/reference/setmbcp.md) funciones). Además, la biblioteca en tiempo de ejecución podría obtener y usar el valor de la página de códigos del sistema operativo, que es una constante para la duración de la ejecución del programa.

Cuando la página de códigos regional cambia, el comportamiento del conjunto de funciones dependiente de la configuración regional cambia a lo que indica la página de códigos elegida. De forma predeterminada, todas las funciones dependientes de la configuración regional empiezan a ejecutarse con una página de códigos regional única de la configuración regional "C". Se puede cambiar la página de códigos regional interna (así como otras propiedades específicas de la configuración regional) llamando a la función `setlocale`. Una llamada a la función `setlocale`(LC_ALL, "") establece la configuración regional en lo que indica la configuración regional de usuario del sistema operativo.

De forma similar, cuando la página de códigos multibyte cambia, el comportamiento de las funciones multibyte cambia a lo que indica la página de códigos elegida. De forma predeterminada, todas las funciones multibyte empiezan a ejecutarse con una página de códigos multibyte correspondiente a la página de códigos predeterminada del sistema operativo. Se puede cambiar la página de códigos multibyte interna llamando a la función `_setmbcp`.

La función en tiempo de ejecución de C `setlocale` establece, cambia o consulta una parte o la totalidad de la información relativa a la configuración regional del programa actual. El [_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) rutina es una versión con caracteres anchos de `setlocale`; los argumentos y valores devueltos de `_wsetlocale` son cadenas de caracteres anchos.

## <a name="see-also"></a>Vea también

[Unicode y MBCS](../text/unicode-and-mbcs.md)<br/>
[Ventajas de la portabilidad de los juegos de caracteres](../text/benefits-of-character-set-portability.md)
