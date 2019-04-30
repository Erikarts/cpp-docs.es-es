---
title: /CLRUNMANAGEDCODECHECK (quite SuppressUnmanagedCodeSecurityAttribute)
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.openlocfilehash: cb23106648e3325755a857d0b962112e9bdcfac4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294426"
---
# <a name="clrunmanagedcodecheck-remove-suppressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK (quite SuppressUnmanagedCodeSecurityAttribute)

**/CLRUNMANAGEDCODECHECK** especifica que no se aplica el vinculador <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> a generadas por vinculador `PInvoke` llamadas desde código administrado en archivos DLL nativos.

## <a name="syntax"></a>Sintaxis

> **/CLRUNMANAGEDCODECHECK**[**:NO**]

## <a name="remarks"></a>Comentarios

De forma predeterminada, el vinculador se aplica el **SuppressUnmanagedCodeSecurityAttribute** a generadas por vinculador `PInvoke` llamadas. Cuando **/CLRUNMANAGEDCODECHECK** está en vigor, **SuppressUnmanagedCodeSecurityAttribute** se quita. Para aplicar explícitamente la **SuppressUnmanagedCodeSecurityAttribute** a generadas por vinculador `PInvoke` llamadas, puede usar **/CLRUNMANAGEDCODECHECK:NO**.

El vinculador solo agrega el atributo a objetos que están compilados con **/CLR** o **/CLR: pure**. Sin embargo, el **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

Un `PInvoke` llamada genera el vinculador cuando el enlazador no encuentra un símbolo administrado que satisfaga una referencia desde un llamador administrado, pero puede encontrar un símbolo nativo para satisfacer esa referencia. Para obtener más información acerca de `PInvoke`, consulte [llamar a funciones nativas desde código administrado](../../dotnet/calling-native-functions-from-managed-code.md).

Tenga en cuenta que si usa <xref:System.Security.AllowPartiallyTrustedCallersAttribute> en el código, debe establecer explícitamente **/CLRUNMANAGEDCODECHECK** para quitar el **SuppressUnmanagedCodeSecurity** atributo. Es una posible vulnerabilidad de seguridad si una imagen contiene tanto el **SuppressUnmanagedCodeSecurity** y **AllowPartiallyTrustedCallers** atributos.

Consulte [instrucciones de codificación segura para código no administrado](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code) para obtener más información acerca de las implicaciones del uso de **SuppressUnmanagedCodeSecurityAttribute**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Expanda el nodo **Propiedades de configuración**.

1. Expanda el **vinculador** nodo.

1. Seleccione el **avanzadas** página de propiedades.

1. Modificar el **código no administrado CLR comprobar** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>.

## <a name="see-also"></a>Vea también

- [Referencia del enlazador MSVC](linking.md)
- [Opciones del enlazador MSVC](linker-options.md)
