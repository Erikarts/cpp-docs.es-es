---
title: Ensamblados de confianza (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- friend assemblies, Visual C++
ms.assetid: 8d55fee0-b7c2-4fbe-a23b-dfe424dc71cd
ms.openlocfilehash: e469556a773ffcdbf50e53d94022c0b6b7abf869
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781047"
---
# <a name="friend-assemblies-c"></a>Ensamblados de confianza (C++)

Para los tiempos de ejecución es aplicable, el *ensamblados de confianza* característica del lenguaje hace que los tipos que están en el ámbito de espacio de nombres o ámbito global en un componente de ensamblado puede tener acceso a uno o más ensamblados de cliente o .netmodule.

## <a name="all-runtimes"></a>Todos los runtimes

**Comentarios**

(Esta característica del lenguaje no se admite en todos los runtimes.)

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

**Comentarios**

(Esta característica del lenguaje no se admite en el tiempo de ejecución de Windows).

### <a name="requirements"></a>Requisitos

Opción del compilador: **/ZW**

## <a name="common-language-runtime"></a>Common Language Runtime

**Comentarios**

#### <a name="to-make-types-at-namespace-scope-or-global-scope-in-an-assembly-component-accessible-to-a-client-assembly-or-netmodule"></a>Hacer que los tipos en el ámbito de espacio de nombres o ámbito global en un componente de ensamblado puede tener acceso a un ensamblado de cliente o .netmodule

1. En el componente, especificar un atributo de ensamblado <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>y pase el nombre del ensamblado de cliente o .netmodule que tendrá acceso a tipos en el ámbito de espacio de nombres o ámbito global en el componente.  Puede especificar varios ensamblados de cliente o .netmodule mediante atributos adicionales.

1. En el ensamblado de cliente o .netmodule cuando se hace referencia el ensamblado de componente mediante el uso de `#using`, pase el `as_friend` atributo.  Si especifica la `as_friend` atributo para un ensamblado que no especifica `InternalsVisibleToAttribute`, se producirá una excepción en tiempo de ejecución si intenta acceder a un tipo en el ámbito de espacio de nombres o ámbito global en el componente.

Se producirá un error de compilación si el ensamblado que contiene el <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo no tiene un nombre seguro, pero el ensamblado de cliente que usa el `as_friend` atributo hace.

Aunque los tipos en el ámbito de espacio de nombres y el ámbito global pueden conocerse a un ensamblado de cliente o .netmodule, accesibilidad de miembro está aún en vigor.  Por ejemplo, no puede tener acceso a un miembro privado.

Se debe conceder explícitamente acceso a todos los tipos en un ensamblado.  Por ejemplo, el ensamblado C no tiene acceso a todos los tipos en el ensamblado A Si el ensamblado C hace referencia al ensamblado B y el ensamblado B tiene acceso a todos los tipos del ensamblado A.

Para obtener información acerca de cómo iniciar sesión, es decir, cómo asignar un nombre seguro para, un ensamblado que se compila mediante el compilador de Visual C++, vea [ensamblados de nombre seguro (firma de ensamblados) (C++ / c++ / CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

Como alternativa al uso de la característica de los ensamblados de confianza, puede usar <xref:System.Security.Permissions.StrongNameIdentityPermission> para restringir el acceso a los distintos tipos.

### <a name="requirements"></a>Requisitos

Opción del compilador: **/clr**

### <a name="examples"></a>Ejemplos

El ejemplo de código siguiente define un componente que se especifica un ensamblado de cliente que tiene acceso a los tipos en el componente.

```cpp
// friend_assemblies.cpp
// compile by using: /clr /LD
using namespace System::Runtime::CompilerServices;
using namespace System;
// an assembly attribute, not bound to a type
[assembly:InternalsVisibleTo("friend_assemblies_2")];

ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

En el ejemplo de código siguiente se obtiene acceso a un tipo privado en el componente.

```cpp
// friend_assemblies_2.cpp
// compile by using: /clr
#using "friend_assemblies.dll" as_friend

int main() {
   Class1 ^ a = gcnew Class1;
   a->Test_Public();
}
```

```Output
Class1::Test_Public
```

El ejemplo de código siguiente define un componente, pero no especifica un ensamblado de cliente que tendrá acceso a los tipos en el componente.

Tenga en cuenta que el componente está vinculado mediante el uso de **/ opt: noref**. Esto garantiza que los tipos privados se emiten en los metadatos del componente, que no es necesaria cuando la `InternalsVisibleTo` atributo está presente. Para obtener más información, consulte [/OPT (optimizaciones)](../build/reference/opt-optimizations.md).

```cpp
// friend_assemblies_3.cpp
// compile by using: /clr /LD /link /opt:noref
using namespace System;

ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

El ejemplo de código siguiente define a un cliente que intenta obtener acceso a un tipo privado en un componente que no otorga acceso a sus tipos privados. Si desea capturar la excepción, debido al comportamiento del tiempo de ejecución, debe intentar tener acceso a un tipo privado en una función auxiliar.

```cpp
// friend_assemblies_4.cpp
// compile by using: /clr
#using "friend_assemblies_3.dll" as_friend
using namespace System;

void Test() {
   Class1 ^ a = gcnew Class1;
}

int main() {
   // to catch this kind of exception, use a helper function
   try {
      Test();
   }
   catch(MethodAccessException ^ e) {
      Console::WriteLine("caught an exception");
   }
}
```

```Output
caught an exception
```

El ejemplo de código siguiente muestra cómo crear un componente de nombre seguro que especifica un ensamblado de cliente que tendrá acceso a los tipos en el componente.

```cpp
// friend_assemblies_5.cpp
// compile by using: /clr /LD /link /keyfile:friend_assemblies.snk
using namespace System::Runtime::CompilerServices;
using namespace System;
// an assembly attribute, not bound to a type

[assembly:InternalsVisibleTo("friend_assemblies_6, PublicKey=00240000048000009400000006020000002400005253413100040000010001000bf45d77fd991f3bff0ef51af48a12d35699e04616f27ba561195a69ebd3449c345389dc9603d65be8cd1987bc7ea48bdda35ac7d57d3d82c666b7fc1a5b79836d139ef0ac8c4e715434211660f481612771a9f7059b9b742c3d8af00e01716ed4b872e6f1be0e94863eb5745224f0deaba5b137624d7049b6f2d87fba639fc5")];

private ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

Tenga en cuenta que el componente debe especificar su clave pública. Se recomienda que ejecute los siguientes comandos de forma secuencial en un símbolo del sistema para crear un par de claves y obtener la clave pública:

**sn -d friend_assemblies.snk**

**sn -k friend_assemblies.snk**

**sn -i friend_assemblies.snk friend_assemblies.snk**

**sn -pc friend_assemblies.snk key.publickey**

**sn -tp key.publickey**

En el ejemplo de código siguiente se obtiene acceso a un tipo privado en el componente de nombre seguro.

```cpp
// friend_assemblies_6.cpp
// compile by using: /clr /link /keyfile:friend_assemblies.snk
#using "friend_assemblies_5.dll" as_friend

int main() {
   Class1 ^ a = gcnew Class1;
   a->Test_Public();
}
```

```Output
Class1::Test_Public
```

## <a name="see-also"></a>Vea también

[Extensiones de componentes para plataformas de tiempo de ejecución](../extensions/component-extensions-for-runtime-platforms.md)
