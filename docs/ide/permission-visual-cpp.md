---
title: '&lt;permission&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C++ XML tag
- permission C++ XML tag
ms.assetid: 537ee2bc-95bd-48e4-9ce6-3420c3da87f4
ms.openlocfilehash: ecf027600b23a640d1dc0cd68b75ffa5eb1b3659
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744610"
---
# <a name="ltpermissiongt-visual-c"></a>&lt;permission&gt; (Visual C++)

La etiqueta \<permission> le permite documentar el acceso de un miembro. <xref:System.Security.PermissionSet> permite especificar el acceso a un miembro.

## <a name="syntax"></a>Sintaxis

```
<permission cref="member">description</permission>
```

#### <a name="parameters"></a>Parámetros

*member*<br/>
Referencia a un miembro o campo al cual se puede llamar desde el entorno de compilación actual. El compilador comprueba si el elemento de código dado existe y traduce `member` al nombre de elemento canónico en la salida XML.  Ponga el nombre entre comillas simples o dobles.

El compilador emite una advertencia si no encuentra `member`.

Para obtener información sobre cómo crear una referencia cref a un tipo genérico, vea [\<see>](../ide/see-visual-cpp.md).

*description*<br/>
Descripción del acceso al miembro.

## <a name="remarks"></a>Comentarios

Compile con [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.

El compilador de Visual C++ intentará resolver referencias cref en un paso por los comentarios de documentación.  Por tanto, si usa las reglas de búsqueda de C++, un símbolo que no encuentra el compilador se marcará como no resuelto. Vea [\<seealso>](../ide/seealso-visual-cpp.md) para obtener más información.

## <a name="example"></a>Ejemplo

```
// xml_permission_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_permission_tag.dll
using namespace System;
/// Text for class TestClass.
public ref class TestClass {
   /// <permission cref="System::Security::PermissionSet">Everyone can access this method.</permission>
   void Test() {}
};
```

## <a name="see-also"></a>Vea también

[Documentación de XML](../ide/xml-documentation-visual-cpp.md)
