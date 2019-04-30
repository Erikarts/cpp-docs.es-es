---
title: Errores del compilador de C3200 a C3299
ms.date: 04/21/2019
f1_keywords:
- C3220
- C3221
- C3245
- C3249
- C3250
- C3256
- C3257
- C3258
- C3259
- C3260
- C3261
- C3263
- C3267
- C3281
- C3294
helpviewer_keywords:
- C3220
- C3221
- C3245
- C3249
- C3250
- C3256
- C3257
- C3258
- C3259
- C3260
- C3261
- C3263
- C3267
- C3281
- C3294
ms.assetid: 6b3104f6-63bc-4823-b6f3-b8a16be4b87f
ms.openlocfilehash: 6965fcde5f7cc93464593e83f787d0a5838398dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62281500"
---
# <a name="compiler-errors-c3200-through-c3299"></a>Errores del compilador de C3200 a C3299

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|[Error del compilador C3200](compiler-error-c3200.md)|'*tipo*': argumento de plantilla no válido para el parámetro de plantilla '*parámetro*', se esperaba una plantilla de clase|
|[Error del compilador C3201](compiler-error-c3201.md)|la lista de parámetros de plantilla de clase '*plantilla*'no coincide con la lista de parámetros de plantilla para el parámetro de plantilla'*parámetro*'|
|[Error del compilador C3202](compiler-error-c3202.md)|'*identificador*': valor predeterminado no válido de argumento, se esperaba una plantilla de clase|
|[Error del compilador C3203](compiler-error-c3203.md)|'*identificador*': genérica o plantilla de clase no especializada no puede usarse como un argumento de plantilla o genérico para el parámetro de plantilla o genérico '*parámetro*', se esperaba un tipo real|
|[Error del compilador C3204](compiler-error-c3204.md)|'*función*' no pueden llamarse desde dentro de un bloque catch|
|[Error del compilador C3205](compiler-error-c3205.md)|lista de argumentos para el parámetro de plantilla '*identificador*' le falta|
|[Error del compilador C3206](compiler-error-c3206.md)|'*función*': argumento de plantilla o genérico no válido para '*plantilla*', falta lista de argumentos de plantilla o genérico en la plantilla de clase/generic '*tipo*'|
|[Error del compilador C3207](compiler-error-c3207.md)|'*función*': argumento de plantilla no válido para '*parámetro*', se esperaba una plantilla clase|
|[Error del compilador C3208](compiler-error-c3208.md)|'*función*': lista de parámetros de plantilla de clase '*plantilla*'no coincide con lista de parámetros de plantilla para el parámetro de plantilla'*parámetro*'|
|[Error del compilador C3209](compiler-error-c3209.md)|'*tipo*': clase genérica debe ser una clase administrada o WinRT|
|[Error del compilador C3210](compiler-error-c3210.md)|'*identificador*': declaración de acceso solo se puede aplicar a un miembro de clase base|
|[Error del compilador C3211](compiler-error-c3211.md)|'*función*': una especialización explícita está usando sintaxis de especialización parcial, use la plantilla <> en su lugar|
|[Error del compilador C3212](compiler-error-c3212.md)|'*función*': una especialización explícita de un miembro de plantilla debe ser un miembro de una especialización explícita|
|[Error del compilador C3213](compiler-error-c3213.md)|clase base*clase*'es menos accesible que'*derived_class*'|
|[Error del compilador C3214](compiler-error-c3214.md)|'*argumento*': argumento de tipo no válido para el parámetro genérico '*parámetro*'de genérico'*tipo*', no cumple la restricción '*restricción*'|
|[Error del compilador C3215](compiler-error-c3215.md)|'*constraint1*': parámetro de tipo genérico ya estaba restringido por '*constraint2*'|
|[Error del compilador C3216](compiler-error-c3216.md)|restricción debe ser un parámetro genérico, no '*tipo*'|
|[Error del compilador C3217](compiler-error-c3217.md)|'*parámetro*': parámetro genérico no se puede restringir en esta declaración|
|[Error del compilador C3218](compiler-error-c3218.md)|'*tipo*': no se permite como restricción de tipo|
|[Error del compilador C3219](compiler-error-c3219.md)|'*parámetro*': parámetro genérico no puede ser restringido por varios elementos sin interfaz: '*tipo*'|
|Error del compilador C3220|'*interfaz*': interfaz no puede tener el Id.|
|Error del compilador C3221|'*miembro*': varios 'default' y 'casos' atributos no está permitidos en un miembro|
|[Error del compilador C3222](compiler-error-c3222.md)|'*función*': no se puede declarar argumentos predeterminados para miembros de un tipo WinRT o administrado o funciones genéricas|
|[Error del compilador C3223](compiler-error-c3223.md)|'*propiedad*': no se puede aplicar 'typeid' a una propiedad|
|[Error del compilador C3224](compiler-error-c3224.md)|'*tipo*': toma ninguna clase genérica sobrecargada*número*' argumentos de tipo genérico|
|[Error del compilador C3225](compiler-error-c3225.md)|argumento de tipo genérico para '*argumento*'no puede ser'*tipo*', debe ser un tipo de valor o un identificador a un tipo de referencia|
|[Error del compilador C3226](compiler-error-c3226.md)|No se permiten declaraciones de plantilla dentro de una declaración genérica|
|[Error del compilador C3227](compiler-error-c3227.md)|'*tipo*': no se puede usar '*operador*' para asignar un tipo genérico|
|[Error del compilador C3228](compiler-error-c3228.md)|'*función*': argumento de tipo genérico para '*argumento*'no puede ser'*tipo*', debe ser un tipo de valor o tipo de identificador|
|[Error del compilador C3229](compiler-error-c3229.md)|'*tipo*': no se permiten direccionamientos indirectos en un parámetro de tipo genérico|
|[Error del compilador C3230](compiler-error-c3230.md)|'*función*': argumento de tipo de plantilla para '*argumento*' no puede contener un parámetro de tipo genérico: '*tipo*'|
|[Error del compilador C3231](compiler-error-c3231.md)|'*tipo*': argumento de tipo de plantilla no puede usar un parámetro de tipo genérico|
|[Error del compilador C3232](compiler-error-c3232.md)|'*parámetro*': no se puede usar un parámetro de tipo genérico en un nombre completo|
|[Error del compilador C3233](compiler-error-c3233.md)|'*tipo*': parámetro de tipo genérico ya restringido|
|[Error del compilador C3234](compiler-error-c3234.md)|una clase genérica no puede derivar de un parámetro de tipo genérico|
|[Error del compilador C3235](compiler-error-c3235.md)|'*especialización*': no se permiten especializaciones explícitas o parciales de una clase genérica|
|[Error del compilador C3236](compiler-error-c3236.md)|no se permite la creación de instancias explícita de un elemento genérico|
|[Error del compilador C3237](compiler-error-c3237.md)|'*clase*': una clase genérica no puede ser un atributo personalizado|
|[Error del compilador C3238](compiler-error-c3238.md)|'*tipo*': un tipo con este nombre ya se ha reenviado al ensamblado '*ensamblado*'|
|[Error del compilador C3239](compiler-error-c3239.md)|'*tipo*': puntero al puntero interior o de anclaje está deshabilitado por common language runtime|
|[Error del compilador C3240](compiler-error-c3240.md)|'*identificador*': debe ser una función miembro abstracta no sobrecargada de '*tipo*'|
|[Error del compilador C3241](compiler-error-c3241.md)|'*miembro*': este método no lo incluyó '*interfaz*'|
|[Error del compilador C3242](compiler-error-c3242.md)|'*función*': solo explícitamente pueden invalidar funciones virtuales|
|[Error del compilador C3243](compiler-error-c3243.md)|ninguna de las funciones de sobrecarga se introdujeron por '*interfaz*'|
|[Error del compilador C3244](compiler-error-c3244.md)|'*miembro*': este método lo incluyó '*Interfaz1*'no por'*Interfaz2*'|
|Error del compilador C3245|'*función*': uso de una plantilla de variables requiere la lista de argumentos de plantilla|
|[Error del compilador C3246](compiler-error-c3246.md)|'*clase*': no puede heredar de '*$base_class*'tal y como se ha declarado como'*herencia*'|
|[Error del compilador C3247](compiler-error-c3247.md)|'*coclase*': una coclase no puede heredar de otra coclase *$base_class*'|
|[Error del compilador C3248](compiler-error-c3248.md)|Obsoleto. '*función*': función declarada como 'sealed' no se puede reemplazar por '*función*'|
|Error del compilador C3249|instrucción no válida o subexpresión para la función 'constexpr'|
|Error del compilador C3250|'*declaración*': no se permite la declaración en el cuerpo de la función 'constexpr'|
|[Error del compilador C3251](compiler-error-c3251.md)|no se puede invocar el método de clase base en una instancia de tipo de valor|
|[Error del compilador C3252](compiler-error-c3252.md)|'*función*': no se puede reducir la accesibilidad de un método virtual en un tipo administrado o WinRT|
|[Error del compilador C3253](compiler-error-c3253.md)|'*función*': error con invalidación explícita|
|[Error del compilador C3254](compiler-error-c3254.md)|'*función*': clase contiene la invalidación explícita '*función*' pero no se deriva de una interfaz que contiene la declaración de función|
|[Error del compilador C3255](compiler-error-c3255.md)|'*tipo*': no se puede asignar dinámicamente este objeto de tipo de valor en el montón nativo|
|Error del compilador C3256|'*función*': variable use no produce una expresión constante|
|Error del compilador C3257|Obsoleto.|
|Error del compilador C3258|Obsoleto.|
|Error del compilador C3259|las funciones 'constexpr' solo pueden tener una instrucción return|
|Error del compilador C3260|'*token*': se omitirá los tokens no esperados antes del cuerpo lambda|
|Error del compilador C3261|una función que devuelve una matriz administrada o WinRT debe tener corchetes de matriz al final de la declaración: '*identificador*(...) []'|
|[Error del compilador C3262](compiler-error-c3262.md)|indización de matriz no válido: *número* especificaron *número*-dimensional '*tipo*'|
|Error del compilador C3263|Obsoleto.|
|[Error del compilador C3264](compiler-error-c3264.md)|'*identificador*': un constructor de clase no puede tener un tipo de valor devuelto|
|[Error del compilador C3265](compiler-error-c3265.md)|no puede declarar un '*managed_construct*'in unmanaged"*unmanaged_construct*'|
|[Error del compilador C3266](compiler-error-c3266.md)|'*función*': un constructor de clase debe tener una lista de parámetros 'void'|
|Error del compilador C3267|Obsoleto.|
|[Error del compilador C3268](compiler-error-c3268.md)|'*función*': una función genérica o una función miembro de una clase genérica no puede tener una lista de parámetros variable|
|[Error del compilador C3269](compiler-error-c3269.md)|'*función*': una función miembro de un tipo administrado o WinRT no se puede declarar con '...'|
|[Error del compilador C3270](compiler-error-c3270.md)|'*campo*': el atributo FieldOffset solo se puede usar en el contexto de StructLayout(LayoutKind::Explicit)|
|[Error del compilador C3271](compiler-error-c3271.md)|'*campo*': valor no válido '*número*' para el atributo FieldOffset|
|[Error del compilador C3272](compiler-error-c3272.md)|'*símbolo*': símbolo requiere FieldOffset, ya que es un miembro de clase o struct *type_name* definidos con StructLayout(LayoutKind::Explicit)|
|[Error del compilador C3273](compiler-error-c3273.md)|'*palabra clave*': no se permite en el bloque try de C++|
|[Error del compilador C3274](compiler-error-c3274.md)|Por último /&#95;&#95;finally sin el correspondiente try|
|[Error del compilador C3275](compiler-error-c3275.md)|'*identificador*': no se puede usar este símbolo sin calificador|
|[Error del compilador C3276](compiler-error-c3276.md)|'*palabra clave*': saltar fuera de finalmente /&#95;&#95;finalmente bloque tiene un comportamiento indefinido durante el control de finalización|
|[Error del compilador C3277](compiler-error-c3277.md)|no se puede definir una enumeración '*enumeración*'interior administrado'*tipo*'|
|[Error del compilador C3278](compiler-error-c3278.md)|llamada de interfaz o método puro directa '*función*' se producirá un error en tiempo de ejecución|
|[Error del compilador C3279](compiler-error-c3279.md)|no se permiten especializaciones parciales o explícitas ni creaciones de instancias explícitas de plantillas de clase declaradas en el espacio de nombres cli|
|[Error del compilador C3280](compiler-error-c3280.md)|'*función*': una función miembro de un tipo administrado no puede compilarse como una función no administrada|
|Error del compilador C3281|'*función*': operador global no puede tener el tipo administrado o WinRT '*tipo*' en la firma|
|[Error del compilador C3282](compiler-error-c3282.md)|listas de parámetros genéricos solamente pueden aparecer en clases administradas o WinRT, structs o funciones|
|[Error del compilador C3283](compiler-error-c3283.md)|'*interfaz*': una interfaz no puede tener un constructor de instancia|
|[Error del compilador C3284](compiler-error-c3284.md)|las restricciones del parámetro genérico '*parámetro*'de la función'*declarador*'debe coincidir con las restricciones del parámetro genérico'*parámetro*'de la función'*declarador*'|
|[Error del compilador C3285](compiler-error-c3285.md)|para cada instrucción no puede funcionar en variables de tipo '*tipo*'|
|[Error del compilador C3286](compiler-error-c3286.md)|'*especificador*': una variable de iteración no puede tener especificadores de clase de almacenamiento|
|[Error del compilador C3287](compiler-error-c3287.md)|el tipo '*tipo*' (tipo de valor devuelto de GetEnumerator) debe tener una función de miembro MoveNext pública adecuada y la propiedad Current pública|
|[Error del compilador C3288](compiler-error-c3288.md)|'*tipo*': desreferenciación no válida de un tipo de identificador|
|[Error del compilador C3289](compiler-error-c3289.md)|'*identificador*': no se puede indizar una propiedad trivial|
|[Error del compilador C3290](compiler-error-c3290.md)|'*tipo*': una propiedad trivial no puede tener tipo de referencia|
|[Error del compilador C3291](compiler-error-c3291.md)|'default': no puede ser el nombre de una propiedad trivial|
|[Error del compilador C3292](compiler-error-c3292.md)|el espacio de nombres cli no se puede abrir de nuevo|
|[Error del compilador C3293](compiler-error-c3293.md)|'*identificador*': utilice 'default' para obtener acceso a la propiedad predeterminada (indizador) para la clase*clase*'|
|Error del compilador C3294|Obsoleto.|
|[Error del compilador C3295](compiler-error-c3295.md)|' #pragma *especificador*' solo puede usarse en global o ámbito de espacio de nombres|
|[Error del compilador C3296](compiler-error-c3296.md)|'*identificador*': ya existe una propiedad con este nombre|
|[Error del compilador C3297](compiler-error-c3297.md)|' *constraint2*': no se puede usar ' *constraint1*' como restricción porque ' *constraint1*' tiene la restricción de valor|
|[Error del compilador C3298](compiler-error-c3298.md)|' *constraint1*': no se puede usar ' *constraint2*' como restricción porque ' *constraint2*' tiene la restricción de referencia y ' *constraint1*' tiene la restricción de valor|
|[Error del compilador C3299](compiler-error-c3299.md)|' *función*': no se puede especificar restricciones, se heredan del método base|

## <a name="see-also"></a>Vea también

[C /C++ herramientas errores y advertencias de compilación y el compilador](../compiler-errors-1/c-cpp-build-errors.md) \
[Errores del compilador de C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
