---
title: /STD (especificar la versión estándar del lenguaje)
ms.date: 11/26/2018
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: 32c63240f578b6170ae351cdf0cd1628167464b6
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58779747"
---
# <a name="std-specify-language-standard-version"></a>/STD (especificar la versión estándar del lenguaje)

Habilitar admite características del lenguaje C++ de la versión especificada del lenguaje C++ estándar.

## <a name="syntax"></a>Sintaxis

> /std:\[c++14\|c++17\|c++latest]

## <a name="remarks"></a>Comentarios

El **/std** opción está disponible en Visual Studio 2017 y versiones posteriores. Sirve para controlar las características estándar de lenguaje habilitadas durante la compilación del código de programación específicos de la versión ISO C++. Esta opción le permite deshabilitar la compatibilidad con ciertas características de lenguaje y biblioteca nueva que se puede interrumpir el código existente que se ajusta a una versión determinada del lenguaje estándar. De forma predeterminada, **/std: c ++ 14** se especifica, lo que deshabilita el idioma y las características de la biblioteca estándar se encuentra en las versiones posteriores del lenguaje C++ estándares. Use **/std: c ++ 17** para habilitar características C ++ 17 estándar específicos y el comportamiento. Para habilitar explícitamente el compilador está implementado actualmente y las características de la biblioteca estándar propuestas para el siguiente borrador de estándar, use **/std: c ++ más reciente**.

El valor predeterminado **/std: c ++ 14** opción habilita el conjunto de características C ++ 14 implementada por el compilador de MSVC. Esta opción deshabilita la compatibilidad del compilador y la biblioteca estándar de las características que se cambian o nuevas en las versiones más recientes del lenguaje estándar, a excepción de algunas características C ++ 17 ya implementados en versiones anteriores del compilador MSVC. Para evitar que los cambios para los usuarios que ya se han tenido dependencias de las características disponibles a partir de Visual Studio 2015 Update 2, estas características permanecerán habilitadas cuando la **/std: c ++ 14** se especifica la opción:

- [Reglas para auto con listas de inicialización entre llaves](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

- [TypeName en parámetros de plantilla](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

- [Eliminación de trígrafos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)

- [Atributos de espacios de nombres y enumeradores](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

- [literales de caracteres de U8](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)

Para obtener más información sobre qué características C ++ 14 y C ++ 17 están habilitados cuando **/std: c ++ 14** está especificado, vea las notas de [conformidad del lenguaje Visual C++](../../overview/visual-cpp-language-conformance.md).

El **/std: c ++ 17** opción permite que el conjunto completo de características C ++ 17 implementada por el compilador de MSVC. Esta opción deshabilita la compatibilidad del compilador y la biblioteca estándar con las características nuevas o que se han modificado en las versiones del borrador de trabajo y las actualizaciones de defectos de C++ Standard posteriores a C++17.

El **/std: c ++ más reciente** opción habilita la publicación-C ++ 17 características del lenguaje y biblioteca implementadas actualmente en el compilador y bibliotecas. Estos pueden incluir características de la C ++ 20 Working Draft y dar de baja las actualizaciones del estándar de C++ que no están incluidas en C ++ 17, así como experimentales propuestas del estándar de borrador. Para obtener una lista de características de la biblioteca y los idiomas admitidos, consulte [What ' s New for Visual C++](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md). El **/std: c ++ más reciente** opción no habilita las características protegidas por el **/ experimental** cambiar, pero es posible que deba habilitarlas.

> [!IMPORTANT]
> Las características del compilador y la biblioteca habilitadas por **/std: c ++ más reciente** se proporcionan como-es y sin soporte técnico. Están sujetos a cambios drásticos eliminación sin previo aviso. Se han diseñado como una vista previa de las características del lenguaje que pueden aparecer en la próxima versión del estándar pero el estándar es un trabajo en curso. Usar **/std: c ++ 17** para usar las características en el estándar ISO C++ más reciente.

El **/std** opción vigente durante una compilación en C++ se puede detectar mediante el uso de la [ \_MSVC\_LANG](../../preprocessor/predefined-macros.md) macro de preprocesador. Para obtener más información, consulte [Macros de preprocesador](../../preprocessor/predefined-macros.md).

El **/std: c ++ 14** y **/std: c ++ más reciente** opciones están disponibles a partir de Visual C++ 2015 Update 3. El **/std: c ++ 17** opción está disponible a partir de Visual C++ 2017 versión 15.3. Como se mencionó anteriormente, algunos estándar C ++ 17 comportamiento está habilitado de forma el **/std: c ++ 14** opción, pero todas las demás características C ++ 17 están habilitadas de forma **/std: c ++ 17**.

> [!NOTE]
> Según el nivel de versión o actualización de compilador MSVC, ciertas características C ++ 14 y C ++ 17 pueden no ser completamente implementadas o totalmente conforme al especificar el **/std: c ++ 14** o **/std: c ++ 17** opciones. Por ejemplo, el compilador de Visual C++ 2017 RTM no admite totalmente C ++ 14 ajustan `constexpr`, expresión SFINAE, o la búsqueda de nombres de 2 fases. Para obtener información general de conformidad del lenguaje C++ en Visual C++ por número de versión, consulte [conformidad del lenguaje Visual C++](../../overview/visual-cpp-language-conformance.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione **propiedades de configuración**, **C o C++**, **lenguaje**.

1. En **estándar de lenguaje C++**, elija el estándar del lenguaje para admitir en el control desplegable y luego elija **Aceptar** o **aplicar** para guardar los cambios.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
