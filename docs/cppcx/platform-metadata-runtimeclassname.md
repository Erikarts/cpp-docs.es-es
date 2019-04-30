---
title: Platform::Metadata::RuntimeClassName
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata::RuntimeClassName
helpviewer_keywords:
- RuntimeClassName
- Platform::Metadata::RuntimeClassName
ms.assetid: fdef8f85-ab94-4edd-ba50-ee0da9358ff6
ms.openlocfilehash: d3de753c3a8897058333e02ce4294a0780d5b818
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387583"
---
# <a name="platformmetadataruntimeclassname"></a>Platform::Metadata::RuntimeClassName

Cuando se aplica a una definición de clase, garantiza que una clase privada devuelva un nombre válido de la función GetRuntimeClassName.

## <a name="syntax"></a>Sintaxis

```cpp
[Platform::Metadata::RuntimeClassName] name
```

#### <a name="parameters"></a>Parámetros

*name*<br/>
El nombre de un tipo público existente visible en Windows en tiempo de ejecución.

### <a name="remarks"></a>Comentarios

Usa este atributo en clases ref privadas para especificar un nombre de tipo en tiempo de ejecución personalizado o cuando el nombre existente no cumpla los requisitos. Especifica como nombre una interfaz pública que la clase implementa.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar el atributo. En este ejemplo, el nombre del tipo en tiempo de ejecución de HellowWorldImpl es Test::Native::MyComponent::IHelloWorld

```cpp
namespace Test
{
    namespace Native
    {
        namespace MyComponent
        {
            public interface class IHelloWorld
            {
                Platform::String^ SayHello();
            };

            private ref class HelloWorldImpl sealed :[Platform::Metadata::RuntimeClassName] IHelloWorld
            {
            public:
                HelloWorldImpl();
                virtual Platform::String^ SayHello();
            };

            Platform::String^ HelloWorldImpl::SayHello()
            {
                return L"Hello World!";
            }
        }
    }
}
```

## <a name="see-also"></a>Vea también

[Platform::Metadata (Espacio de nombres)](../cppcx/platform-metadata-namespace.md)
