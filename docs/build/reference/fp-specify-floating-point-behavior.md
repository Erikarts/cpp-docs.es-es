---
title: /fp (Especificar comportamiento de punto flotante)
ms.date: 11/09/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.floatingPointModel
- VC.Project.VCCLWCECompilerTool.FloatingPointExceptions
- /fp
- VC.Project.VCCLWCECompilerTool.floatingPointModel
- VC.Project.VCCLCompilerTool.FloatingPointExceptions
helpviewer_keywords:
- -fp compiler option [C++]
- /fp compiler option [C++]
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
ms.openlocfilehash: c571bf104fd7e8f6a287c3dd35c444d904b4b7e8
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894099"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (Especificar comportamiento de punto flotante)

Especifica cómo el compilador trata las excepciones, las optimizaciones y las expresiones de punto flotante. El **/FP** opciones especifican si el código generado permite cambios de entorno de punto flotante en el modo de redondeo, máscaras de excepción y comportamiento subnormal, y si las comprobaciones de estado de punto flotante devuelven actuales y precisas resultados. Controla si el compilador genera código que mantiene la operación de origen y el orden de la expresión y se ajusta al estándar para la propagación de NaN, o si genera un código más eficaz que puede cambiar el orden o combinar operaciones y usar lo que simplifica en su lugar transformaciones algebraicas no permitidos por el estándar.

## <a name="syntax"></a>Sintaxis

> **/ fp:**[**precisa** | **strict** | **rápido** | **excepto**[ **-**]]

### <a name="arguments"></a>Argumentos

#### <a name="precise"></a>Precisa

De forma predeterminada, el compilador usa **/fp: precisa** comportamiento.

En **/fp: precisa** el compilador preserva la expresión de origen, ordenación y las propiedades de código de punto flotante de redondeo cuando genera y optimiza el código de objeto para el equipo de destino. El compilador se redondea a la precisión del código de origen en cuatro puntos específicos durante la evaluación de expresiones: en las asignaciones, en conversiones de tipo, se devuelve cuando se pasa un argumento de punto flotante a una llamada de función y cuando el valor de punto flotante de una llamada de función. Los cálculos intermedios se pueden realizar en la precisión de la máquina. Conversiones de tipo puede ser usada para redondear explícitamente los cálculos intermedios.

El compilador no realizar transformaciones algebraicas en expresiones de punto flotante, como la reasociación o distribución, a menos que se garantiza que la transformación para generar un resultado idéntico bit a bit.
Las expresiones que implican valores especiales (NaN, + infinito, - infinito, -0.0), se procesan según las especificaciones IEEE-754. Por ejemplo, `x != x` se evalúa como **true** si x es NaN. Punto flotante *contracciones*, es decir, las instrucciones máquina que combinan las operaciones de punto flotante, pueden generarse en **/fp: precisa**.

El compilador genera código diseñada para ejecutarse el [entorno de punto flotante predeterminada](#the-default-floating-point-environment) y se da por supuesto que el entorno de punto flotante no se ha accedido o modificado en tiempo de ejecución. Es decir, se supone que el código no quitar la máscara de excepciones de punto flotante, leer o escribir registros de estado de punto flotante o cambiar el modo de redondeo.

Si el código de punto flotante no depende del orden de las operaciones y expresiones en las instrucciones de punto flotante (por ejemplo, si no importa si `a * b + a * c` se calcula como `(b + c) * a` o `2 * a` como `a + a`), tenga en cuenta el [/fp: Fast](#fast) opción, que puede generar código más rápido y eficaz. Si el código tanto depende del orden de las operaciones y expresiones y tiene acceso o modifica el entorno de punto flotante (por ejemplo, para cambiar los modos de redondeo o para interceptar las excepciones de punto flotante), use [/fp: strict](#strict).

#### <a name="strict"></a>strict

**/ fp: strict** tiene un comportamiento similar a **/fp: precisa**, es decir, el compilador preserva el orden de los orígenes y propiedades redondeo de punto flotante código cuando se genera y se optimiza el código para el equipo de destino del objeto y observa el estándar al controlar valores especiales. Además, el programa de forma segura puede acceder a o modificar el entorno de punto flotante en tiempo de ejecución.

En **/fp: strict**, el compilador genera código que permite al programa de forma segura sin máscara a excepciones de punto flotante, leer o escribir los registros de estado de punto flotante o cambiar el modo de redondeo. Redondea a la precisión del código de origen en cuatro puntos específicos durante la evaluación de expresiones: en las asignaciones, en conversiones de tipo, se devuelve cuando se pasa un argumento de punto flotante a una llamada de función y cuando el valor de punto flotante de una llamada de función. Los cálculos intermedios se pueden realizar en la precisión de la máquina. Conversiones de tipo puede ser usada para redondear explícitamente los cálculos intermedios. El compilador no realizar transformaciones algebraicas en expresiones de punto flotante, como la reasociación o distribución, a menos que se garantiza que la transformación para generar un resultado idéntico bit a bit. Las expresiones que implican valores especiales (NaN, + infinito, - infinito, -0.0), se procesan según las especificaciones IEEE-754. Por ejemplo, `x != x` se evalúa como **true** si x es NaN. Contracciones de punto flotante no se generan en **/fp: strict**.

**/ fp: strict** es más costoso que **/fp: precisa** porque el compilador debe insertar instrucciones adicionales para interceptar las excepciones y permitir que los programas tener acceso o modificar el entorno de punto flotante en tiempo de ejecución. Si el código no usa esta funcionalidad, pero requiere la ordenación de código de origen y el redondeo o se basa en valores especiales, utilice **/fp: precisa**. De lo contrario, considere el uso de **/fp: Fast**, lo que puede generar código más rápido y más pequeño.

#### <a name="fast"></a>Rápida

El **/fp: Fast** opción permite que el compilador reordenar, combinar o simplificar las operaciones de punto flotante para optimizar el código para la velocidad y el espacio de punto flotante. El compilador puede omitir el redondeo en instrucciones de asignación, conversiones de tipo o llamadas de función. Puede reordenar las operaciones o realizar transformaciones algebraicas, por ejemplo, mediante el uso de las leyes asociativas y distributivas, incluso si dichas transformaciones provocan el comportamiento de redondeo de diferente manera visible. Debido a esta optimización mejorada, el resultado de algunos cálculos de punto flotante puede diferir de los generados por otros **/FP** opciones. Los valores especiales (NaN, + infinito, - infinito, -0.0) no se pueden propagar o se comportan estrictamente según el estándar IEEE 754. Contracciones de punto flotante pueden generarse en **/fp: Fast**. El compilador todavía está enlazado por la arquitectura subyacente en **/fp: Fast**, y las optimizaciones adicionales estén disponibles a través del uso de la [/arch](../../build/reference/arch-minimum-cpu-architecture.md) opción.

En **/fp: Fast**, el compilador genera código diseñada para ejecutarse en el entorno de punto flotante de forma predeterminada y se da por supuesto que el entorno de punto flotante no es accedido o modificado en tiempo de ejecución. Es decir, se supone que el código no quitar la máscara de excepciones de punto flotante, leer o escribir registros de estado de punto flotante o cambiar el modo de redondeo.

**/ fp: Fast** está destinado a los programas que no requieren el orden de código de origen estricta y el redondeo de expresiones de punto flotante y no confían en las reglas estándar para controlar los valores especiales como NaN. Si el código de punto flotante requiere la conservación del código fuente de ordenación y el redondeo, o se basa en el comportamiento estándar de valores especiales, use [/fp: precisa](#precise). Si el código obtiene acceso o modifica el entorno para cambiar los modos de redondeo de punto flotante, sin máscara a excepciones de punto flotante, o comprobar el estado de punto flotante, utilice [/fp: strict](#strict).

#### <a name="except"></a>except

El **/fp: excepto** opción genera código para garantizar que las excepciones de punto flotante sin máscara se generan en el punto exacto en el que se producen, y que no se genera ninguna excepción de punto flotante adicional. De forma predeterminada, el **/fp: strict** opción habilita **/fp: excepto**, y **/fp: precisa** no lo hace. El **/fp: excepto** no es compatible con la opción **/fp: Fast**. La opción se puede deshabilitar explícitamente por nosotros de **/fp: excepto-**.

Tenga en cuenta que **/fp: excepto** no permite las excepciones de punto flotante por sí mismo, pero es necesario para los programas habilitar excepciones de punto flotante. Consulte [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) para obtener información sobre cómo habilitar excepciones de punto flotante.

## <a name="remarks"></a>Comentarios

Varios **/FP** opciones se pueden especificar en la misma línea de comandos del compilador. Solo uno de **/fp: strict**, **/fp: Fast**, y **/fp: precisa** opciones pueden estar en vigor a la vez. Si no se especifica más de una de estas opciones en la línea de comandos, la opción posterior tiene prioridad y el compilador genera una advertencia. El **/fp: strict** y **/fp: excepto** opciones no son compatibles con **/CLR**.

El [/Za](../../build/reference/za-ze-disable-language-extensions.md) no es compatible con la opción (compatibilidad con ANSI) **/FP**.

### <a name="using-pragmas-to-control-floating-point-behavior"></a>Uso de directivas pragma para controlar el comportamiento de punto flotante

El compilador ofrece tres directivas pragma para invalidar el comportamiento de punto flotante especificado en la línea de comandos: [float_control](../../preprocessor/float-control.md), [fenv_access](../../preprocessor/fenv-access.md), y [fp_contract](../../preprocessor/fp-contract.md). Puede utilizar estos pragmas para controlar el comportamiento de punto flotante en el nivel de función, no dentro de una función. Tenga en cuenta que estas pragmas no corresponden directamente a la **/FP** opciones. Esta tabla se muestra cómo el **/FP** directivas pragma y opciones se asignan entre sí. Para obtener más información, consulte la documentación para las directivas pragma y opciones individuales.

||float_control(precise)|float_control(except)|fenv_access|fp_contract|
|-|-|-|-|-|
|**/fp:fast**|Desactivar|Desactivar|Desactivar|el|
|**/fp:precise**|el|Desactivar|Desactivar|el|
|**/fp:strict**|el|el|el|Desactivar|

### <a name="the-default-floating-point-environment"></a>El entorno de punto flotante predeterminada

Cuando se inicializa un proceso, el *predeterminado al entorno de punto de flotante* está establecido. Este entorno enmascara excepciones de punto flotante de todo, Establece el modo de redondeo para redondear al más cercano (`FE_TONEAREST`), conserva subnormal (desnormalizado) valores, la precisión predeterminada de mantisa (mantisa) se utiliza para **float**, **doble**, y **long double** valores y, si se admite, Establece el control de infinito en el modo predeterminado afines.

### <a name="floating-point-environment-access-and-modification"></a>Modificación y el acceso al entorno de punto flotante

El tiempo de ejecución de Microsoft Visual C++ proporciona varias funciones para obtener acceso y modificar el entorno de punto flotante. Estos incluyen [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md), [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md), y [_statusfp](../../c-runtime-library/reference/status87-statusfp-statusfp2.md) y sus variantes. Para garantizar el comportamiento correcto del programa cuando el código obtiene acceso o modifica el entorno de punto flotante, `fenv_access` debe estar habilitada, ya sea por la **/fp: strict** opción o mediante el uso de la `fenv_access` pragma para estas funciones con tiene ningún efecto. Cuando `fenv_access` no es activado, acceso o la modificación del entorno de punto flotante puede provocar un comportamiento inesperado del programa: código no puede respetar los cambios solicitados para el entorno de punto flotante; no pueden informar de los registros de estado de punto flotante resultados esperados o actuales; y pueden producirse excepciones de punto flotante inesperadas o no pueden producirse excepciones de punto flotante esperadas.

Cuando el código obtiene acceso o modifica el entorno de punto flotante, debe tener cuidado al combinar código donde `fenv_access` está habilitado con código que no tenga `fenv_access` habilitado. En el código donde `fenv_access` no está habilitado, el compilador supone que el entorno de punto flotante de plataforma predeterminada está en vigor, y que no se tiene acceso a o se modifica el estado de punto flotante. Se recomienda guardar y restaurar el entorno de punto flotante local a su estado predeterminado antes de que el control se transfiere a una función que no tiene `fenv_access` habilitado. Este ejemplo se muestra cómo el `float_control` pragma se puede establecer y restaurar:

```cpp
#pragma float_control(strict, on, push)
// Code that uses /fp:strict mode
#pragma float_control(pop)
```

### <a name="floating-point-rounding-modes"></a>Modos de redondeo de punto flotante

En ambos **/fp: precisa** y **/fp: Fast** el compilador genera código diseñada para ejecutarse en el entorno de punto flotante de forma predeterminada y se da por supuesto que el entorno no es accedido o modificado en tiempo de ejecución. Es decir, se supone que el código no quitar la máscara de excepciones de punto flotante, leer o escribir registros de estado de punto flotante o cambiar el modo de redondeo.  Sin embargo, algunos programas se necesitan modificar el entorno de punto flotante. Por ejemplo, este ejemplo calcula los límites de error de una multiplicación de punto flotante mediante la modificación de los modos de redondeo de punto flotante:

```cpp
// fp_error_bounds.cpp
#include <iostream>
#include <limits>
using namespace std;

int main(void)
{
    float a = std::<float>::max();
    float b = -1.1;
    float cLower = 0.0;
    float cUpper = 0.0;
    unsigned int control_word = 0;
    int err = 0;

    // compute lower error bound.
    // set rounding mode to -infinity.
    err = _controlfp_s(&control_word, _RC_DOWN, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_DOWN, _MCW_RC) failed with error:" << err << endl;
    }  
    cLower = a * b;

    // compute upper error bound.
    // set rounding mode to +infinity.
    err = _controlfp_s(&control_word, _RC_UP, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_UP, _MCW_RC) failed with error:" << err << endl;
    }
    cUpper = a * b;

    // restore default rounding mode.
    err = _controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC) failed with error:" << err << endl;
    }
    // display error bounds.
    cout << "cLower = " << cLower << endl;
    cout << "cUpper = " << cUpper << endl;
    return 0;
}
```

Puesto que el compilador supone que el valor predeterminado entorno de punto de flotante **/fp: Fast** y **/fp: precisa** es gratis pasar por alto las llamadas a `_controlfp_s`. Por ejemplo, cuando se compila con ambos métodos **/O2** y **/fp: precisa** para el x86 arquitectura, no se calculan los límites y genera el programa de ejemplo:

```Output
cLower = -inf
cUpper = -inf
```

Cuando se compila con ambos **/O2** y **/fp: strict** para el x86 salidas de arquitectura, el programa de ejemplo:

```Output
cLower = -inf
cUpper = -3.40282e+38
```

### <a name="floating-point-special-values"></a>Valores especiales de punto flotante

En **/fp: precisa** y **/fp: strict**, las expresiones que implican valores especiales (NaN, + infinito, - infinito, -0.0) se comportan según las especificaciones IEEE-754. En **/fp: Fast**, el comportamiento de estos valores especiales que puede ser incoherente con IEEE 754.

Este ejemplo muestra el comportamiento diferente de valores especiales en **/fp: precisa**, **/fp: strict** y **/fp: Fast**:

```cpp
// fp_special_values.cpp
#include <stdio.h>
#include <cmath>

float gf0 = -0.0;

int main()
{
    float f1 = INFINITY;
    float f2 = NAN;
    float f3 = -INFINITY;
    bool a, b;
    float c, d, e;
    a = (f1 == f1);
    b = (f2 == f2);
    c = (f1 - f1);
    d = (f2 - f2);
    printf("INFINITY == INFINITY : %d\n", a);
    printf("NAN == NAN           : %d\n", b);
    printf("INFINITY - INFINITY  : %f\n", c);
    printf("NAN - NAN            : %f\n", d);

    e = gf0 / abs(f3);
    printf("std::signbit(-0.0/-INFINITY): %d\n", std::signbit(c));
    return 0;
}
```

Cuando se compila con **/O2** **/fp: precisa** o **/O2** **/fp: strict** para x86 arquitectura, las salidas son coherentes con la IEEE-754 especificación de:

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 0
INFINITY - INFINITY  : -nan(ind)
NAN - NAN            : -nan(ind)
std::signbit(-0.0/-INFINITY): 1
```

Cuando se compila con **/O2** **/fp: Fast** para x86 arquitectura, las salidas no son coherentes con IEEE-754:

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 1
INFINITY - INFINITY  : 0.000000
NAN - NAN            : 0.000000
std::signbit(-0.0/-INFINITY): 0
```

### <a name="floating-point-algebraic-transformations"></a>Transformaciones algebraicas punto flotante

En **/fp: precisa** y **/fp: strict**, el compilador no realiza transformaciones matemáticas a menos que se garantiza que la transformación para generar un resultado idéntico bit a bit. El compilador puede realizar dichas transformaciones en **/fp: Fast**. Por ejemplo, la expresión `a * b + a * c` en función de ejemplo `algebraic_transformation` pueden compilarse en `a * (b + c)` en **/fp: Fast**. No se realizan estas transformaciones en **/fp: precisa** o **/fp: strict**, y el compilador genera `a * b + a * c`.

```cpp
float algebraic_transformation (float a, float b, float c)
{
    return a * b + a * c;
}
```

### <a name="floating-point-explicit-casting-points"></a>Puntos de punto flotante de conversión explícita

En **/fp: precisa** y **/fp: strict**, el compilador se redondea a la precisión del código de origen en cuatro puntos específicos durante la evaluación de expresiones: en las asignaciones, en conversiones de tipo cuando un argumento de punto flotante se pasa a una llamada de función y se devuelve un valor de punto flotante de una llamada de función. Conversiones de tipo puede ser usada para redondear explícitamente los cálculos intermedios. En **/fp: Fast**, el compilador no genera las conversiones explícitas en estos momentos para garantizar la precisión del código de origen. En este ejemplo se muestra el comportamiento en diferentes **/FP** opciones:

```cpp
float casting(float a, float b)
{
    return 5.0*((double)(a+b));
}
```

Al compilar con **/O2** **/fp: precisa** o **/O2** **/fp: strict**, puede ver que las conversiones de tipos explícitas se insertan en ambos el convertir el tipo y a la función devuelve el punto en el código generado para el x64 arquitectura:

```asm
        addss    xmm0, xmm1
        cvtss2sd xmm0, xmm0
        mulsd    xmm0, QWORD PTR __real@4014000000000000
        cvtsd2ss xmm0, xmm0
        ret      0
```

En **/O2** **/fp: Fast** se simplifica el código generado, porque todas las conversiones de tipo optimizadas:

```asm
        addss    xmm0, xmm1
        mulss    xmm0, DWORD PTR __real@40a00000
        ret      0
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **generación de código** página de propiedades.

1. Modificar el **modelo de punto flotante** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](compiler-options.md)<br/>
[Establecer las opciones del compilador](setting-compiler-options.md)<br/>
[Microsoft Visual C++, optimización de punto flotante](floating-point-optimization.md)<br/>
