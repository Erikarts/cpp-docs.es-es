---
title: Interfaces (C++/CX)
ms.date: 01/22/2017
ms.assetid: 11034314-d54a-426d-923b-5ab7a6b9f8ce
ms.openlocfilehash: b904f041e34bcf5fda78fed11aaad4998ba5208a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366037"
---
# <a name="interfaces-ccx"></a>Interfaces (C++/CX)

Aunque una clase ref solo puede heredar de a lo sumo una clase base concreta, puede implementar cualquier número de clases de interfaz. Una clase de interfaz (o struct de interfaz) en sí misma puede heredar (o requerir) varias clases de interfaz, puede sobrecargar sus funciones miembro y puede tener parámetros de tipo.

## <a name="characteristics"></a>Características

Una interfaz tiene estas características:

- Una clase (o struct) de interfaz se debe declarar dentro de un espacio de nombres y puede tener accesibilidad pública o privada. Únicamente las interfaces públicas se emiten para metadatos.

- Los miembros de una interfaz pueden incluir propiedades, métodos y eventos.

- Todos los miembros de interfaz son implícitamente públicos y virtuales.

- No permiten campos ni miembros estáticos.

- Los tipos que se usan como propiedades, parámetros de método o valores devueltos solo pueden ser tipos de Windows Runtime; esto incluye los tipos fundamentales y los tipos de clase enum.

## <a name="declaration-and-usage"></a>Declaración y uso

En el ejemplo siguiente se muestra cómo declarar una interfaz: Observa que una interfaz se puede declarar como una clase o como un tipo struct.

[!code-cpp[cx_interfaces#01](../cppcx/codesnippet/CPP/interfacestest/class1.h#01)]

Para implementar una interfaz, una clase ref o un struct ref declara e implementa métodos y propiedades virtuales. La interfaz y la clase ref de implementación deben utilizar los mismos nombres de parámetro de método, como se muestra en este ejemplo:

[!code-cpp[cx_interfaces#02](../cppcx/codesnippet/CPP/interfacestest/class1.h#02)]

## <a name="interface-inheritance-hierarchies"></a>Jerarquías de herencia de interfaz

Una interfaz puede heredar de una o varias interfaces. Pero a diferencia de una clase o un struct ref, una interfaz no declara los miembros heredados de la interfaz. Si la interfaz B hereda de la interfaz A y la clase ref C hereda de B, C debe implementar tanto A como B. Esto se muestra en el siguiente ejemplo.

[!code-cpp[cx_interfaces#03](../cppcx/codesnippet/CPP/interfacestest/class1.h#03)]

## <a name="implementing-interface-properties-and-events"></a>Implementar propiedades y eventos de interfaz

Como se muestra en el ejemplo anterior, puedes usar propiedades virtuales triviales para implementar propiedades de interfaz. También puedes proporcionar captadores y establecedores personalizados en la clase de implementación.  Tanto el captador como el establecedor deben ser públicos en una propiedad de interfaz.

[!code-cpp[cx_interfaces#04](../cppcx/codesnippet/CPP/interfacestest/class1.h#04)]

Si una interfaz declara una propiedad solo para obtener o solo para establecer, la clase de implementación debe proporcionar explícitamente un captador o un establecedor.

[!code-cpp[cx_interfaces#05](../cppcx/codesnippet/CPP/interfacestest/class1.h#05)]

También puedes implementar métodos Add y Remove personalizado para eventos de la clase de implementación.

## <a name="explicit-interface-implementation"></a>Implementación de interfaz explícita

Cuando una clase ref implementa varias interfaces y esas interfaces tienen métodos cuyos nombres y firmas son idénticos para el compilador, puedes utilizar la sintaxis siguiente para indicar explícitamente el método de interfaz que un método de clase está implementando.

[!code-cpp[cx_interfaces#06](../cppcx/codesnippet/CPP/interfacestest/class1.h#06)]

## <a name="generic-interfaces"></a>Interfaces genéricas

En C++/CX, `generic` la palabra clave se utiliza para representar un tipo parametrizado de Windows En tiempo de ejecución. Un tipo parametrizado se emite en metadatos y puede ser utilizado por código escrito en cualquier lenguaje que admita parámetros de tipo. Windows Runtime define algunas interfaces genéricas (por ejemplo, [Windows::Foundation::Collections::IVector\<T>), ](/uwp/api/Windows.Foundation.Collections.IVector_T_)pero no admite la creación de interfaces genéricas públicas definidas por el usuario en C++/CX. Sin embargo, puedes crear interfaces genéricas privadas.

A continuación se muestra cómo se pueden usar los tipos de Windows Runtime para crear una interfaz genérica:

- Una `interface class` genérica definida por el usuario en un componente no se puede emitir en su archivo de metadatos de Windows; por consiguiente, no puede tener accesibilidad pública y el código de cliente de otros archivos .winmd no puede implementarla. Puede ser implementada por clases ref no públicas en el mismo componente. Una clase ref pública puede tener un tipo de interfaz genérica como miembro privado.

   En el fragmento de código siguiente se muestra cómo declarar una `interface class` genérica e implementarla después en una clase ref privada, y utilizar la clase ref como miembro privado en una clase ref pública.

   [!code-cpp[cx_interfaces#07](../cppcx/codesnippet/CPP/interfacestest/class1.h#07)]

- Una interfaz genérica debe seguir las reglas de interfaz estándar que rigen la accesibilidad, los miembros, las relaciones *necesarias* , las clases base, etc.

- Una interfaz genérica puede tomar uno o más parámetros de tipo genérico precedidos de `typename` o `class`. No se admiten parámetros que no sean de tipo.

- Un parámetro de tipo puede ser cualquier tipo de Windows Runtime. Es decir, el parámetro de tipo puede ser un tipo de referencia, un tipo de valor, una clase de interfaz, un delegado, un tipo fundamental o una clase de enumeración pública.

- Una *interfaz genérica cerrada* es una interfaz que hereda de una interfaz genérica y especifica argumentos de tipo concretos para todos los parámetros de tipo. Se puede usar en cualquier lugar donde se pueda usar una interfaz privada genérica.

- Una *interfaz genérica abierta* es una interfaz que tiene uno o más parámetros de tipo para los que no se ha proporcionado todavía ningún tipo concreto. Se puede usar en cualquier lugar donde se pueda usar un tipo e incluir como un argumento de tipo de otra interfaz genérica.

- Solo puedes parametrizar una interfaz completa, no métodos individuales.

- Los parámetros de tipo no se pueden restringir.

- Una interfaz genérica cerrada tiene un UUID generado implícitamente. Un usuario no puede especificar el UUID.

- En la interfaz, se supone que cualquier referencia a la actual interfaz (en un parámetro de método, un valor devuelto o una propiedad) hace referencia a la instancia actual. Por ejemplo, *IMyIntf* significa *IMyIntf\<T>*.

- Cuando el tipo de un parámetro de método es un parámetro de tipo, la declaración de ese parámetro o variable usa el nombre del parámetro de tipo sin ningún puntero, referencia nativa o declaradores de identificador. Es decir, nunca has de escribir “T^”.

- Las clases ref con plantillas deben ser privadas. Pueden implementar interfaces genéricas y pueden pasar el parámetro de plantilla *T* al argumento genérico *T*. Cada creación de instancias de una clase ref con plantilla es en sí misma una clase ref.

## <a name="see-also"></a>Consulte también

[Sistema de tipos](../cppcx/type-system-c-cx.md)<br/>
[Referencia del lenguaje C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)
