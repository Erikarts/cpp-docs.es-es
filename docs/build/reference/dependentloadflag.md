---
title: / DEPENDENTLOADFLAG (marcas de carga dependiente de conjunto de forma predeterminada)
description: La opción /DEPENDENTLOADFLAG establece marcas predeterminadas para los archivos DLL cargados mediante LoadLibrary
ms.date: 05/18/2018
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 94998e06f23a7e70524221d3cb75166b5d3f2c44
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815975"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/ DEPENDENTLOADFLAG (marcas de carga dependiente de conjunto de forma predeterminada)

Establece las marcas de carga predeterminado utiliza cuando `LoadLibrary` se usa para cargar los archivos DLL.

## <a name="syntax"></a>Sintaxis

> **/DEPENDENTLOADFLAG**[**:**_loadflags_]

### <a name="arguments"></a>Argumentos

*loadflags*<br/>
Un valor entero de 16 bits de "C"-style opcional en decimal, octal con un cero inicial o hexadecimal con uno de los principales `0x`, que especifica las marcas de carga dependiente que se aplicará a todos los [LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa) llamadas. El valor predeterminado es 0.

## <a name="remarks"></a>Comentarios

Esta opción es nueva en Visual Studio 2017 y solo se aplica a aplicaciones que se ejecutan en Windows 10 RS1 y versiones posteriores. Esta opción se omite para otros sistemas operativos que ejecutan la aplicación.

En sistemas operativos compatibles, esta opción tiene el efecto de cambiar las llamadas a `LoadLibrary("dependent.dll")` al equivalente de `LoadLibraryEx("dependent.dll", 0, loadflags)`. Las llamadas a [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa) no se ven afectadas. Esta opción no aplica de forma recursiva a archivos DLL cargados por la aplicación.

Esta marca se puede usar para evitar que la DLL plantar ataques. Por ejemplo, si una aplicación usa `LoadLibrary` para cargar un archivo DLL dependiente, un atacante podría implantar un archivo DLL con el mismo nombre en la ruta de acceso de búsqueda usando `LoadLibrary`, como el directorio actual, que se pueden comprobar antes de los directorios del sistema si es el modo seguro de búsqueda DLL deshabilitada. Modo seguro de búsqueda DLL coloca el directorio del usuario actual más adelante en el orden de búsqueda y está habilitado de forma predeterminada en Windows XP SP2 y versiones posteriores. Para obtener más información, consulte [orden de búsqueda de biblioteca de vínculos dinámicos](/windows/desktop/Dlls/dynamic-link-library-search-order).

Si especifica la opción de vínculo `/DEPENDENTLOADFLAG:0xA00` (el valor de las marcas combinados `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`), a continuación, incluso si se deshabilita el modo seguro de búsqueda DLL en el equipo del usuario, la ruta de acceso de búsqueda DLL se limita a los directorios protegidos que están más difíciles que un atacante cambio. Para obtener información acerca de los indicadores disponibles y sus valores numéricos y simbólicos, consulte el *dwFlags* descripción del parámetro en [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa).

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Para establecer la opción del vinculador DEPENDENTLOADFLAG en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Especifique la opción de **opciones adicionales**.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

- [Referencia MSVC del vinculador](linking.md)
- [Opciones del vinculador MSVC](linker-options.md)
- [Vincular un ejecutable a un archivo DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Vincular un ejecutable a un archivo DLL](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa)
- [Orden de búsqueda de la biblioteca de vínculos dinámicos](/windows/desktop/Dlls/dynamic-link-library-search-order)
