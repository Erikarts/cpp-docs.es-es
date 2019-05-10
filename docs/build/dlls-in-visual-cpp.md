---
title: Crear archivos DLL de C o C++ en Visual Studio
ms.date: 05/06/2019
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
ms.openlocfilehash: 7f1c2b71a58c59bf0662aa4ffec53344ce657df0
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220759"
---
# <a name="create-cc-dlls-in-visual-studio"></a>Crear archivos DLL de C o C++ en Visual Studio

En Windows, una biblioteca de vínculos dinámicos (DLL) es un tipo de archivo ejecutable que actúa como una biblioteca compartida de funciones y recursos. La vinculación dinámica es una funcionalidad de sistema operativo que permite a un archivo ejecutable llamar a funciones o usar los recursos almacenados en un archivo independiente. Estas funciones y recursos se pueden compilar e implementar de forma independiente con respecto a los archivos ejecutables que los usan. Un archivo DLL no es un archivo ejecutable independiente; se ejecuta en el contexto de una aplicación que lo llama. El sistema operativo puede cargar el archivo DLL al espacio de memoria de la aplicación cuando se carga la aplicación (*vinculación implícita*), o a petición en tiempo de ejecución (*vinculación explícita*). Los archivos DLL también hacen que sea más fácil compartir funciones y recursos en archivos ejecutables. Distintas aplicaciones pueden acceder al mismo tiempo al contenido de una única copia de un archivo DLL en la memoria.

## <a name="differences-between-dynamic-linking-and-static-linking"></a>Diferencias entre la vinculación dinámica y la vinculación estática

Vinculación estática copia todo el código de objeto en una biblioteca estática en los archivos ejecutables que se usan cuando se generan. La vinculación dinámica solo incluye la información necesaria para Windows en tiempo de ejecución para buscar y cargar la DLL que contiene un elemento de datos o una función. Cuando se crea un archivo DLL, también crear una biblioteca de importación que contiene esta información. Cuando se compila un archivo ejecutable que llama al archivo DLL, el vinculador utiliza los símbolos exportados en la biblioteca de importación para almacenar esta información para el cargador de Windows. Cuando el cargador carga un archivo DLL, el archivo DLL se asigna en el espacio de memoria de la aplicación. Si está presente, función especial en el archivo DLL, `DllMain`, se llama para realizar cualquier inicialización que requiere el archivo DLL.

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>Diferencias entre aplicaciones y archivos DLL

Aunque los archivos DLL y las aplicaciones son ambos módulos ejecutables, se diferencian de varias maneras. Para el usuario final, la diferencia más obvia es que los archivos DLL no es aplicaciones que se pueden ejecutar directamente. Desde el punto de vista del sistema, hay dos diferencias fundamentales entre las aplicaciones y los archivos DLL:

- Una aplicación puede tener varias instancias ejecutándose simultáneamente en el sistema, mientras que sólo se puede ejecutar una instancia de un archivo DLL.

- Se puede cargar una aplicación como un proceso que puede ser propietaria de elementos como una pila, subprocesos de ejecución, la memoria global, identificadores de archivo y una cola de mensajes, pero no de un archivo DLL.

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>Ventajas de utilizar archivos DLL

Vinculación dinámica en lugar de la vinculación estática al código y recursos ofrece varias ventajas. Al usar archivos DLL, puede ahorrar espacio de memoria y reducir el intercambio. Si varias aplicaciones pueden usar una única copia de un archivo DLL, puede ahorrar espacio en disco y ancho de banda de descarga. Los archivos DLL se pueden implementar y actualizar por separado, lo que le permite proporcionar actualizaciones de software y soporte técnico post-venta sin tener que volver a compilar y enviar todo el código. Los archivos DLL son una manera cómoda de proporcionar recursos específicos de una configuración regional, lo que puede proporcionar compatibilidad con programas multilenguaje y facilitar la creación de versiones internacionales de sus aplicaciones. Vinculación explícita puede permitir que la aplicación a detecte y cargue los archivos DLL en tiempo de ejecución, como las extensiones que proporcionan nuevas capacidades.

La vinculación dinámica ofrece las siguientes ventajas:

- La vinculación dinámica ahorra memoria y reduce el intercambio. Muchos procesos pueden utilizar un archivo DLL al mismo tiempo, compartiendo una sola copia de las partes de sólo lectura de un archivo DLL en la memoria. En cambio, todas las aplicaciones que se compila mediante una biblioteca estática vinculada tiene una copia completa del código de biblioteca que Windows deben cargar en memoria.

- La vinculación dinámica ahorra ancho de banda y espacio en disco. Varias aplicaciones pueden compartir una única copia del archivo DLL en disco. En cambio, las aplicaciones compiladas mediante una biblioteca de vínculos estáticos tiene el código de biblioteca vinculado en la imagen ejecutable, que se utiliza más espacio en disco y tarda más ancho de banda para transferir.

- Revisiones de seguridad de mantenimiento, y las actualizaciones pueden ser más fáciles. Cuando las aplicaciones usan funciones comunes en un archivo DLL, a continuación, siempre que no cambian los argumentos de función y valores devueltos, puede implementar correcciones de errores e implementar actualizaciones en el archivo DLL. Cuando se actualiza los archivos DLL, las aplicaciones que los usan no es necesario volver a compilar y vincular, y hacen uso de la nueva DLL tan pronto como se implementa. En cambio, correcciones de código del objeto vinculado estáticamente requieren volver a vincular y volver a implementar todas las aplicaciones que lo usan.

- Puede utilizar archivos DLL para proporcionar asistencia post-venta. Por ejemplo, se puede modificar un archivo DLL de un controlador de vídeo de forma que permita una presentación que no estaba disponible en la versión comercial. Puede utilizar la vinculación explícita para cargar las extensiones de aplicación como archivos DLL y agregar nuevas funciones a la aplicación sin volver a generar o volver a implementarlo.

- La vinculación dinámica resulta más fácil admitir aplicaciones escritas en lenguajes de programación diferentes. Programas creados con distintos lenguajes de programación pueden llamar a la misma función DLL siempre que sigan la convención de llamada a la función. Los programas y la función DLL deben coincidir en los siguientes aspectos: el orden de inserción de los argumentos de la función en la pila, si la función o la aplicación es responsable de limpiar la pila y si se pasan argumentos en registros.

- La vinculación dinámica proporciona un mecanismo para extender las clases de la biblioteca MFC. Puede derivar clases a partir de las clases MFC existentes y colocarlas en un archivo DLL de extensión de MFC para que las utilicen las aplicaciones MFC.

- La vinculación dinámica facilita la creación de versiones internacionales de la aplicación. Al colocar los recursos específicos de la configuración regional en un archivo DLL, es mucho más fácil crear versiones internacionales de una aplicación. En lugar de muchas de las versiones localizadas de la aplicación de envío, puede colocar las cadenas y las imágenes para cada idioma en una archivo DLL de recursos independiente y, a continuación, la aplicación puede cargar los recursos adecuados para esa configuración regional en tiempo de ejecución.

Una posible desventaja de utilizar archivos DLL es que la aplicación no es independiente; depende de la existencia de un módulo DLL independiente que debe implementar o comprobar por sí mismo como parte de la instalación.

## <a name="more-information-on-how-to-create-and-use-dlls"></a>Para obtener más información sobre cómo crear y utilizar archivos DLL

Los temas siguientes proporcionan información detallada sobre cómo crear C /C++ archivos DLL en Visual Studio.

[Tutorial: Creación y uso de una biblioteca de vínculos dinámicos (C++)](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
Describe cómo crear y usar una DLL con Visual Studio.

[Tipos de archivos DLL](kinds-of-dlls.md)<br/>
Proporciona información sobre las distintas clases de archivos DLL que se pueden compilar.

[Preguntas más frecuentes sobre archivos DLL](dll-frequently-asked-questions.md)<br/>
Proporciona respuestas a las preguntas más frecuentes sobre los archivos DLL.

[Vincular un ejecutable a un archivo DLL](linking-an-executable-to-a-dll.md)<br/>
Describe el vínculo a un archivo DLL explícito e implícito.

[Inicializar un archivo DLL](run-time-library-behavior.md#initializing-a-dll)<br/>
Describe el código de inicialización de DLL que deberá ejecutarse cuando se cargue el archivo DLL.

[Archivos DLL y comportamiento de la biblioteca en tiempo de ejecución de Visual C++](run-time-library-behavior.md)<br/>
Describe cómo la biblioteca en tiempo de ejecución realiza la secuencia de inicio del archivo DLL.

[LoadLibrary y AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)<br/>
Describe el uso de **LoadLibrary** y `AfxLoadLibrary` para vincularse explícitamente a un archivo DLL en tiempo de ejecución.

[GetProcAddress](getprocaddress.md)<br/>
Describe el uso de **GetProcAddress** para obtener la dirección de una función exportada en el archivo DLL.

[FreeLibrary y AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)<br/>
Describe el uso de **FreeLibrary** y `AfxFreeLibrary` cuando ya no se necesita el módulo de DLL.

[Orden de búsqueda de la biblioteca de vínculos dinámicos](/windows/desktop/Dlls/dynamic-link-library-search-order)<br/>
Describe la ruta de acceso de búsqueda que usa el sistema operativo Windows para encontrar un archivo DLL en el sistema.

[Estados de módulos de un archivo DLL de MFC estándar vinculado dinámicamente a MFC](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)<br/>
Describe los Estados de módulos de DLL de MFC vinculado dinámicamente a MFC normal.

[Archivos DLL de extensión MFC](extension-dlls-overview.md)<br/>
Muestra un archivo DLL que implementa clases reutilizables derivadas de las clases existentes de la biblioteca MFC (Microsoft Foundation Classes).

[Creación de un archivo DLL de recursos](creating-a-resource-only-dll.md)<br/>
Describe un archivo DLL sólo de recursos, que únicamente contiene recursos, como iconos, mapas de bits, cadenas y cuadros de diálogo.

[Recursos localizados en aplicaciones MFC: archivos DLL satélite](localized-resources-in-mfc-applications-satellite-dlls.md)<br/>
Proporciona compatibilidad mejorada con archivos DLL satélite, una característica que le ayuda a crear aplicaciones en múltiples idiomas.

[Importar y exportar](importing-and-exporting.md)<br/>
Describe símbolos públicos de importación a una aplicación o funciones de exportación de un archivo DLL.

[Tecnología activa y archivos DLL](active-technology-and-dlls.md)<br/>
Permite a los servidores de objetos implementarse dentro de un archivo DLL.

[Automatización en un archivo DLL](automation-in-a-dll.md)<br/>
Describe qué proporciona la opción Automation en el Asistente para archivos DLL de MFC.

[Convenciones de nomenclatura para archivos DLL de MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)<br/>
Explica cómo los archivos DLL y las bibliotecas incluidos en MFC utilizan una convención de nomenclatura estructurada.

[Llamar a funciones DLL desde aplicaciones de Visual Basic](calling-dll-functions-from-visual-basic-applications.md)<br/>
Describe cómo llamar a funciones DLL desde aplicaciones de Visual Basic.

## <a name="related-sections"></a>Secciones relacionadas

[Usar MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)<br/>
Describe los archivos DLL de MFC estándar, que le permiten usar la biblioteca MFC como parte de una biblioteca de vínculos dinámicos de Windows.

[Versión de DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)<br/>
Describe cómo puede usar MFCxx.dll y MFCxxD.dll (donde x es el número de versión MFC) comparten las bibliotecas de vínculos dinámicos con las aplicaciones MFC y archivos DLL de extensión MFC.
