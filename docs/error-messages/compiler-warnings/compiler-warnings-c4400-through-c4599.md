---
title: Compilador advertencias C4400 a C4599
ms.date: 05/30/2018
f1_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4451
- C4452
- C4453
- C4454
- C4455
- C4456
- C4457
- C4459
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
helpviewer_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4451
- C4452
- C4453
- C4454
- C4455
- C4456
- C4457
- C4459
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
ms.assetid: b07850a5-ae89-48ea-bf9a-f0e30939f9b9
ms.openlocfilehash: 990560e2c05f66a010382f736735c19c17d4dc28
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816625"
---
# <a name="compiler-warnings-c4400-through-c4599"></a>Compilador advertencias C4400 a C4599

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de advertencia generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Mensajes de advertencia

|Advertencia|Mensaje|
|-------------|-------------|
|[Advertencia del compilador (nivel 1) C4600](compiler-warning-level-1-c4600.md)|#pragma '*nombredemacro*': se esperaba una cadena vacía no válida|
|[Advertencia del compilador (nivel 4) C4400](../../error-messages/compiler-warnings/compiler-warning-level-4-c4400.md)|'*tipo*': no se admiten los calificadores const/volatile en este tipo|
|[Advertencia del compilador (nivel 1) C4401](../../error-messages/compiler-warnings/compiler-warning-level-1-c4401.md)|'*campo de bits*': miembro es el campo de bits|
|[Advertencia del compilador (nivel 1) C4402](../../error-messages/compiler-warnings/compiler-warning-level-1-c4402.md)|debe utilizar un operador PTR|
|[Advertencia del compilador (nivel 1) C4403](../../error-messages/compiler-warnings/compiler-warning-level-1-c4403.md)|operador PTR no válido|
|[Advertencia del compilador (nivel 3) C4404](../../error-messages/compiler-warnings/compiler-warning-level-3-c4404.md)|período de tiempo de la directiva pasa por alto|
|[Advertencia del compilador (nivel 1) C4405](../../error-messages/compiler-warnings/compiler-warning-level-1-c4405.md)|'*identificador*': identificador es una palabra reservada|
|[Advertencia del compilador (nivel 1) C4406](../../error-messages/compiler-warnings/compiler-warning-level-1-c4406.md)|operando de la directiva pasa por alto|
|[Advertencia del compilador (nivel 1) C4407](../../error-messages/compiler-warnings/compiler-warning-level-1-c4407.md)|conversión entre diferentes representaciones de puntero a miembro, el compilador puede generar código incorrecto|
|[Advertencia del compilador (nivel 4) C4408](../../error-messages/compiler-warnings/compiler-warning-level-4-c4408.md)|anónimo ' struct&#124;unión ' no se ha declarado ningún miembro de datos|
|[Advertencia del compilador (nivel 1) C4409](../../error-messages/compiler-warnings/compiler-warning-level-1-c4409.md)|tamaño de la instrucción no válida|
|[Advertencia del compilador (nivel 1) C4410](../../error-messages/compiler-warnings/compiler-warning-level-1-c4410.md)|tamaño no válido para el operando|
|[Advertencia del compilador (nivel 1) C4411](../../error-messages/compiler-warnings/compiler-warning-level-1-c4411.md)|'*identificador*': símbolo se resuelve como un registro de desplazamiento|
|[Advertencia del compilador (nivel 2) C4412](../../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)|'*función*': función firma contiene el tipo '*tipo*'; Los objetos de C++ son no es seguro pasar entre código puro y mixto o nativo.|
|Advertencia C4413 del compilador|'classname::member': miembro de referencia se inicializa en un archivo temporal que no se conserva cuando termina el constructor|
|[Advertencia del compilador (nivel 3) C4414](../../error-messages/compiler-warnings/compiler-warning-level-3-c4414.md)|'*función*': salto short a la función ha convertido en near|
|Advertencia del compilador (nivel 1) C4415|duplicados __declspec (code_seg ('*nombre*'))|
|Advertencia del compilador (nivel 1) C4416|__declspec(code_seg(...)) contiene una cadena vacía: omite|
|Advertencia del compilador (nivel 1) C4417|una instancia de plantilla explícitos no code_seg: omite|
|Advertencia del compilador (nivel 1) C4418|__declspec(code_seg(...)) omitido en una enumeración|
|Advertencia del compilador (nivel 3) C4419|'*símbolo*'no tiene ningún efecto cuando se aplica a la clase ref privada'*clase*'.|
|[Advertencia del compilador (nivel 1) C4420](../../error-messages/compiler-warnings/compiler-warning-level-1-c4420.md)|'*checked_operator*': operador no está disponible, utilizando '*operador*' en su lugar; comprobación de tiempo de ejecución puede suponer un riesgo|
|Advertencia del compilador (nivel 3) C4421|'*parámetro*': un parámetro de referencia en una función reanudable es potencialmente inseguro|
|Advertencia del compilador (nivel 3) C4423|'std:: bad_alloc': clase detectará ('*tipo*') en línea *número*|
|Advertencia del compilador (nivel 3) C4424|catch para '*type1*'precedido por'*type2*' en línea *número*; impredecibles comportamiento puede producir si se produce 'std:: bad_alloc'|
|Advertencia del compilador (nivel 1) C4425|Una anotación SAL no se puede aplicar a '...'|
|Advertencia del compilador (nivel 1) C4426|las marcas de optimización cambiadas después de incluir el encabezado, es posible que se puede deber a #pragma optimize()|
|Advertencia del compilador (nivel 1) C4427|'*operador*': desbordamiento de división de constantes, comportamiento no definido|
|[Advertencia del compilador (nivel 4) C4429](../../error-messages/compiler-warnings/compiler-warning-level-4-c4429.md)|posible incompleto o incorrectamente formado universal: nombre de carácter|
|[Advertencia (Error) del compilador C4430](../../error-messages/compiler-warnings/compiler-warning-c4430.md)|falta el especificador de tipo; se presupone int. Nota: C++ no admite default-int|
|[Advertencia del compilador (nivel 4) C4431](../../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)|falta el especificador de tipo; se presupone int. Nota: C ya no admite default-int|
|[Advertencia del compilador (nivel 4) C4434](../../error-messages/compiler-warnings/compiler-warning-level-4-c4434.md)|un constructor estático debe tener accesibilidad privada; cambiará a acceso privado|
|[Advertencia del compilador (nivel 4) C4435](../../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)|'*derived_class*': Diseño de objeto vd2 cambiará debido a la base virtual '*$base_class*'|
|[Advertencia del compilador (nivel 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)|dinámica\_conversión de la base virtual '*$base_class*'para'*derived_class*' en el constructor o destructor podría fallar con objetos construidos parcialmente|
|[Advertencia del compilador (nivel 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)|dinámica\_conversión de la base virtual '*$base_class*'para'*derived_class*' podría producir un error en algunos contextos|
|Advertencia C4438 del compilador|'*función*': no se puede llamar de forma segura / await: clrcompat modo. Si '*función*' llama a CLR puede causar daños principal de CLR|
|[Advertencia (Error) del compilador C4439](../../error-messages/compiler-warnings/compiler-warning-c4439.md)|'*función*': definición de función con un tipo administrado en la firma debe tener una convención de llamada __clrcall|
|[Advertencia del compilador (nivel 1) C4440](../../error-messages/compiler-warnings/compiler-warning-level-1-c4440.md)|nueva definición de convención de llamada '*convención_de_llamada1*'para'*calling_convenction2*' omite|
|[Advertencia del compilador (nivel 1) C4441](../../error-messages/compiler-warnings/compiler-warning-level-1-c4441.md)|convención de llamada de '*convención_de_llamada1*' omitida; '*calling_convention2*' utilizado en su lugar|
|Advertencia del compilador (nivel 1) C4442|terminador nulo incrustado en el argumento __annotation.  Valor se truncará.|
|Advertencia del compilador (nivel 1) C4443|se esperaba parámetro pragma fuera '0', '1' o '2'|
|Advertencia del compilador (nivel 3) C4444|'*identificador*': el nivel superior '__unaligned' no está implementado en este contexto|
|[Advertencia del compilador (nivel 1) C4445](../../error-messages/compiler-warnings/compiler-warning-level-1-c4445.md)|'*función*': en un ' WinRT&#124;administrado ' tipo de un método virtual no puede ser privado|
|Advertencia del compilador (nivel 1) C4446|'*tipo*': no se puede asignar el miembro '*nombre1*' en este tipo, debido a un conflicto con el nombre de tipo. El método se ha cambiado a '*nombre2*'|
|Advertencia del compilador (nivel 1) C4447|signatura 'main' encontrada sin necesidad de modelo de subprocesos. Considere usar ' int main (Platform:: Array\<Platform:: String ^ > ^ args)'.|
|Advertencia C4448 del compilador|'*tipo*1' no tiene una interfaz predeterminada especificada en los metadatos. Realizar una selección: '*type2*', que puede producir un error en tiempo de ejecución.|
|Advertencia C4449 del compilador|'*tipo*' un tipo no sellado se debe marcar como '[WebHostHidden]'|
|Advertencia C4450 del compilador|'*type1*'se debe marcar como '[WebHostHidden]' porque deriva de'*type2*'|
|Advertencia del compilador (nivel 4) C4451|'classname1::member': Uso de la clase ref 'classname2::member' dentro de este contexto puede dar lugar a la serialización no válido del objeto en todos los contextos|
|Advertencia del compilador (nivel 1) C4452|'*identificador*': no puede ser un tipo público en el ámbito global. Debe estar en un espacio de nombres es un elemento secundario del nombre del archivo de salida .winmd.|
|Advertencia del compilador (nivel 1) C4453|'*tipo*': Un tipo '[WebHostHidden]' no debe usarse en la superficie publicada de un tipo público que no sea '[WebHostHidden]'|
|Advertencia del compilador (nivel 1) C4454|'*función*' está sobrecargado por algo más que el número de parámetros de entrada sin necesidad de especificado [DefaultOverload]. Seleccionar '*declaración*' como sobrecarga predeterminada|
|Advertencia del compilador (nivel 1) C4455|' operador *operador*': los identificadores de sufijo literales que no empiecen por un carácter de subrayado están reservados|
|[Advertencia del compilador (nivel 4) C4456](compiler-warning-level-4-c4456.md)|declaración de '*identificador*' oculta la declaración local anterior|
|[Advertencia del compilador (nivel 4) C4457](compiler-warning-level-4-c4457.md)|declaración de '*identificador*' oculta el parámetro de función|
|[Advertencia del compilador (nivel 4) C4458](compiler-warning-level-4-c4458.md)|declaración de '*identificador*' oculta el miembro de clase|
|[Advertencia del compilador (nivel 4) C4459](compiler-warning-level-4-c4459.md)|declaración de '*identificador*' oculta la declaración global|
|[Advertencia del compilador (nivel 4) C4460](../../error-messages/compiler-warnings/compiler-warning-level-4-c4460.md)|' WinRT&#124;administrado ' operador '*operador*', tiene un parámetro pasado por referencia. ' WinRT&#124;administrado ' operador '*operador*'tiene una semántica diferente del operador de C++'*cpp_operator*', ¿deseaba pasar por valor?|
|[Advertencia del compilador (nivel 1) C4461](../../error-messages/compiler-warnings/compiler-warning-level-1-c4461.md)|'*classname*': esta clase tiene un finalizador '! *finalizador*' pero no un destructor ' ~*dtor*'|
|[Del compilador (nivel 1, Error) de la advertencia C4462](../../error-messages/compiler-warnings/compiler-warning-level-1-c4462.md)|'*tipo*': no se puede determinar el GUID del tipo. El programa puede dar un error en tiempo de ejecución.|
|[Advertencia del compilador (nivel 4) C4463](compiler-warning-level-4-c4463.md)|desbordamiento; asignación '*valor*'para el campo de bits que solo puede contener valores de'*min_value*'para'*max_value*'|
|[Advertencia del compilador (nivel 4) C4464](../../error-messages/compiler-warnings/c4464.md)|ruta de acceso de inclusión relativa contiene '..'|
|[Advertencia del compilador (nivel 1) C4470](../../error-messages/compiler-warnings/compiler-warning-level-1-c4470.md)|pragmas de control de punto flotante omitidas en /clr|
|[Advertencia del compilador (nivel 4) C4471](compiler-warning-level-4-c4471.md)|'*enumeración*': una declaración adelantada de una enumeración sin ámbito debe tener un tipo subyacente (se presupone int)|
|Advertencia del compilador (nivel 1) C4472|'*identificador*' es una enumeración nativa: agregue un especificador de acceso (privado/público) para declarar un ' WinRT&#124;administrada ' enum|
|[Advertencia del compilador (nivel 1) C4473](c4473.md)|'*función*': no hay suficientes argumentos pasan para la cadena de formato|
|Advertencia del compilador (nivel 3) C4474|'*función*': pasado demasiados argumentos para la cadena de formato|
|Advertencia del compilador (nivel 3) C4475|'*función*': modificador de longitud '*modificador*'no puede utilizarse con el carácter de tipo'*carácter*' en el especificador de formato|
|Advertencia del compilador (nivel 3) C4476|'*función*': carácter de tipo desconocido '*carácter*' en el especificador de formato|
|[Advertencia del compilador (nivel 1) C4477](c4477.md)|'*función*': cadena de formato '*cadena*'requiere un argumento de tipo'*tipo*', pero el argumento variádico *número* tiene el tipo '*tipo*'|
|Advertencia del compilador (nivel 1) C4478|'*función*': no se puede combinar marcadores de posición posicionales y no posicionales en la misma cadena de formato|
|Advertencia C4480 (Error) de advertencia del compilador|extensión no estándar utilizada: especifica el tipo subyacente de enum '*enumeración*'|
|[Advertencia del compilador (nivel 4) C4481](../../error-messages/compiler-warnings/compiler-warning-level-4-c4481.md)|ha utilizado una extensión no estándar: especificador de invalidación '*palabra clave*'|
|Advertencia C4482 del compilador|ha utilizado una extensión no estándar: enumeración '*enumeración*' utilizado en el nombre completo|
|Advertencia del compilador (nivel 1, Error) C4483|error de sintaxis: se esperaba la palabra clave de C++|
|[Advertencia (Error) del compilador C4484](../../error-messages/compiler-warnings/compiler-warning-c4484.md)|'*función_de_reemplazo*': coincide con el método de clase ref de base '*función_de_clase_base*', pero no está marcado como 'virtual', 'new' u 'override'; se supone 'new' (y no 'virtual')|
|[Advertencia (Error) del compilador C4485](../../error-messages/compiler-warnings/compiler-warning-c4485.md)|'*función_de_reemplazo*': coincide con el método de clase ref de base '*función_de_clase_base*', pero no está marcada 'new' u 'override'; se supone 'new' (y 'virtual')|
|[Advertencia del compilador (nivel 1) C4486](../../error-messages/compiler-warnings/compiler-warning-level-1-c4486.md)|'*función*': un método virtual privado de una clase ref o clase value debe marcarse como 'sealed'|
|[Advertencia del compilador (nivel 4) C4487](../../error-messages/compiler-warnings/compiler-warning-level-4-c4487.md)|'*función_de_clase_derivada*': coincide con hereda el método no virtual '*función_de_clase_base*' pero no está explícitamente marcado como 'new'|
|[Advertencia del compilador (nivel 1) C4488](../../error-messages/compiler-warnings/compiler-warning-level-1-c4488.md)|'*función*': requiere '*palabra clave*'palabra clave para implementar el método de interfaz'*método_de_interfaz*'|
|[Advertencia del compilador (nivel 1) C4489](../../error-messages/compiler-warnings/compiler-warning-level-1-c4489.md)|'*especificador*': no se permite en el método de interfaz '*método*'; solo se permiten especificadores en métodos de clase de valor y de clase ref de invalidación|
|[Advertencia del compilador (nivel 1) C4490](../../error-messages/compiler-warnings/compiler-warning-level-1-c4490.md)|'override': uso incorrecto del especificador de invalidación; '*función*' no coincide con un método de clase ref base|
|Advertencia del compilador (nivel 1) C4491|'*nombre*': tiene un formato de versión IDL no válido|
|Advertencia del compilador (nivel 1, Error) C4492|'*función1*': coincide con el método de clase ref de base '*función2*', pero no está marcado como 'override'|
|Advertencia del compilador (nivel 3, Error) C4493|Expresión DELETE no tiene ningún efecto porque el destructor de '*tipo*' no tiene accesibilidad 'public'|
|Advertencia del compilador (nivel 1) C4494|'*función*': Se omite __declspec (Allocator) porque el tipo de valor devuelto de la función no es un puntero o referencia|
|Advertencia C4495 del compilador|ha utilizado una extensión '__super': reemplazar por el nombre de clase base explícito|
|Advertencia C4496 del compilador|usa una extensión no estándar 'for each': reemplazar por la instrucción ranged-for|
|Advertencia C4497 del compilador|ha utilizado una extensión 'sealed': reemplácela por 'final'|
|Advertencia C4498 del compilador|ha utilizado una extensión no estándar: '*extensión*'|
|Advertencia del compilador (nivel 4) C4499|"*función*': una especialización explícita no puede tener una clase de almacenamiento (omiten)"|
|[Advertencia del compilador (nivel 1) C4502](../../error-messages/compiler-warnings/compiler-warning-level-1-c4502.md)|'*especificación de vinculación*' requiere el uso de la palabra clave 'extern' y debe preceder al resto de los especificadores|
|[Advertencia del compilador (nivel 1) C4503](../../error-messages/compiler-warnings/compiler-warning-level-1-c4503.md)|'*identificador*': superada, la longitud del nombre representativo nombre aparece truncado|
|[Advertencia del compilador (nivel 4) C4505](../../error-messages/compiler-warnings/compiler-warning-level-4-c4505.md)|'*función*': se ha quitado la función local sin referencia|
|[Advertencia del compilador (nivel 1) C4506](../../error-messages/compiler-warnings/compiler-warning-level-1-c4506.md)|ninguna definición de función insertada '*función*'|
|[Advertencia del compilador (nivel 1) C4508](../../error-messages/compiler-warnings/compiler-warning-level-1-c4508.md)|'*función*': función debe devolver un valor; 'void' tipo de valor devuelto asumido|
|Advertencia C4509 del compilador|ha utilizado una extensión no estándar: '*función*' utiliza SEH y '*objeto*' tiene un destructor|
|[Advertencia del compilador (nivel 4) C4510](../../error-messages/compiler-warnings/compiler-warning-level-4-c4510.md)|'*clase*': constructor predeterminado se definió implícitamente como eliminado|
|[Advertencia del compilador (nivel 3) C4511](../../error-messages/compiler-warnings/compiler-warning-level-3-c4511.md)|'*clase*': constructor de copias se definió implícitamente como eliminado|
|[Advertencia del compilador (nivel 4) C4512](../../error-messages/compiler-warnings/compiler-warning-level-4-c4512.md)|'*clase*': operador de asignación se definió implícitamente como eliminado|
|[Advertencia del compilador (nivel 4) C4513](../../error-messages/compiler-warnings/compiler-warning-level-4-c4513.md)|'*clase*': destructor se definió implícitamente como eliminado|
|[Advertencia del compilador (nivel 4) C4514](../../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)|'*función*': se ha quitado la función insertada sin referencia|
|[Advertencia del compilador (nivel 4) C4515](../../error-messages/compiler-warnings/compiler-warning-level-4-c4515.md)|'*espacio de nombres*': espacio de nombres se utiliza a sí mismo|
|[Advertencia del compilador (nivel 4) C4516](../../error-messages/compiler-warnings/compiler-warning-level-4-c4516.md)|'clase:: símbolo': las declaraciones de acceso están desusadas; declaraciones using de miembros son una alternativa mejor|
|[Advertencia del compilador (nivel 4) C4517](../../error-messages/compiler-warnings/compiler-warning-level-4-c4517.md)|las declaraciones de acceso están desusadas; declaraciones using de miembros son una alternativa mejor|
|[Advertencia del compilador (nivel 1) C4518](../../error-messages/compiler-warnings/compiler-warning-level-1-c4518.md)|'*especificador*': clase de almacenamiento o tipo esperaban aquí; se omite|
|Advertencia C4519 (Error) del compilador|argumentos de plantilla predeterminados solo se permiten en una plantilla de clase|
|[Advertencia del compilador (nivel 3) C4521](../../error-messages/compiler-warnings/compiler-warning-level-3-c4521.md)|'*clase*': han especificado varios constructores de copia|
|[Advertencia del compilador (nivel 3) C4522](../../error-messages/compiler-warnings/compiler-warning-level-3-c4522.md)|'*clase*': varios operadores de asignación especificados|
|[Advertencia del compilador (nivel 3) C4523](../../error-messages/compiler-warnings/compiler-warning-level-3-c4523.md)|'*clase*': han especificado varios destructores|
|[Advertencia del compilador (nivel 1) C4526](../../error-messages/compiler-warnings/compiler-warning-level-1-c4526.md)|'*función*': función miembro estática no puede invalidar la función virtual '*función virtual*' se omite, el reemplazo se ocultará la función virtual|
|[Advertencia del compilador (nivel 1) C4530](../../error-messages/compiler-warnings/compiler-warning-level-1-c4530.md)|Controlador de excepciones de C++ que utiliza, pero la semántica de desenredo no están habilitadas. Especifique /EHsc|
|Advertencia del compilador (nivel 1) C4531|Control de excepciones de C++ no está disponible en Windows CE. Utilice el control de excepciones estructurado|
|[Advertencia del compilador (nivel 1) C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|'continue': salto fuera del bloque ' __finally/finally' tiene un comportamiento indefinido durante el control de finalización|
|[Advertencia del compilador (nivel 1) C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|inicialización de '*variable*'se omite en'*goto label*'|
|[Advertencia del compilador (nivel 3) C4534](../../error-messages/compiler-warnings/compiler-warning-level-3-c4534.md)|'*constructor*'no se puede tener un constructor predeterminado para 'class/struct' '*identificador*' debido al argumento predeterminado|
|[Advertencia del compilador (nivel 3) C4535](../../error-messages/compiler-warnings/compiler-warning-level-3-c4535.md)|calling _set_se_translator() requires /EHa|
|[Advertencia del compilador (nivel 4) C4536](../../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)|'*typename*': nombre de tipo supera el límite de metadatos de '*character_limit*' caracteres|
|[Advertencia del compilador (nivel 1) C4537](../../error-messages/compiler-warnings/compiler-warning-level-1-c4537.md)|'*objeto*': '.' aplicado al tipo no definido por el usuario|
|[Advertencia del compilador (nivel 3) C4538](../../error-messages/compiler-warnings/compiler-warning-level-3-c4538.md)|'*tipo*': no se admiten los calificadores const/volatile en este tipo|
|[Advertencia del compilador (nivel 1) C4540](../../error-messages/compiler-warnings/compiler-warning-level-1-c4540.md)|dynamic_cast se ha utilizado para convertir a base inaccesible o ambigua; se producirá un error de prueba de tiempo de ejecución ('*type1*'para'*type2*')|
|[Advertencia del compilador (nivel 1) C4541](../../error-messages/compiler-warnings/compiler-warning-level-1-c4541.md)|'*identificador*'utilizado en el tipo polimórfico'*tipo*' con/GR-; puede provocar un comportamiento impredecible|
|Advertencia del compilador (nivel 1) C4542|Omitiendo la generación del archivo de texto insertado combinado, no se puede escribir *filetype* archivo: '*problema*': *mensaje*|
|[Advertencia del compilador (nivel 3) C4543](../../error-messages/compiler-warnings/compiler-warning-level-3-c4543.md)|Inserta texto suprimido por el atributo ' ningún\_injected_text'|
|[Advertencia del compilador (nivel 1) C4544](../../error-messages/compiler-warnings/compiler-warning-level-1-c4544.md)|'*declaración*': argumento de plantilla que se omite en esta declaración de plantilla predeterminado|
|[Advertencia del compilador (nivel 1) C4545](../../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)|la expresión antes de la coma se evalúa como una función a la que le falta una lista de argumentos|
|[Advertencia del compilador (nivel 1) C4546](../../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)|falta la lista de argumentos de la llamada de función antes de la coma|
|[Advertencia del compilador (nivel 1) C4547](../../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)|'*operador*': operador antes de una coma no tiene ningún efecto; se esperaba un operador con efectos secundarios|
|[Advertencia del compilador (nivel 1) C4548](../../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)|la expresión antes de la coma no tiene ningún efecto; se esperaba una expresión con efectos secundarios|
|[Advertencia del compilador (nivel 1) C4549](../../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)|'*operador*': operador antes de la coma no tiene ningún efecto; ¿realmente pensaba en '*operador*'?|
|[Advertencia del compilador (nivel 1) C4550](../../error-messages/compiler-warnings/compiler-warning-level-1-c4550.md)|expresión se evalúa como una función que le falta una lista de argumentos|
|[Advertencia del compilador (nivel 1) C4551](../../error-messages/compiler-warnings/compiler-warning-level-1-c4551.md)|lista de argumentos de función llamada que faltan|
|[Advertencia del compilador (nivel 1) C4552](../../error-messages/compiler-warnings/compiler-warning-level-1-c4552.md)|'*operador*': operador no tiene ningún efecto; se esperaba un operador con efectos secundarios|
|[Advertencia del compilador (nivel 1) C4553](../../error-messages/compiler-warnings/compiler-warning-level-1-c4553.md)|'*operador*': operador no tiene ningún efecto; ¿realmente pensaba en ' operador?|
|[Compilador advertencia (nivel 3) C4554](../../error-messages/compiler-warnings/compiler-warning-level-3-c4554.md) C4554|'*operador*': Compruebe la prioridad de operador para posibles errores; utilice paréntesis para indicar la prioridad|
|[Advertencia del compilador (nivel 1) C4555](../../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)|la expresión no tiene efecto; se esperaba una expresión con efecto secundario|
|[Advertencia del compilador (nivel 1) C4556](../../error-messages/compiler-warnings/compiler-warning-level-1-c4556.md)|valor del argumento inmediato intrínseco '*valor*'está fuera del intervalo'*lower_bound* - *upper_bound*'|
|[Advertencia del compilador (nivel 3) C4557](../../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)|'__assume' contiene el efecto '*efecto*'|
|[Advertencia del compilador (nivel 1) C4558](../../error-messages/compiler-warnings/compiler-warning-level-1-c4558.md)|valor del operando '*valor*'está fuera del intervalo'*lower_bound* - *upper_bound*'|
|[Advertencia del compilador (nivel 4) C4559](../../error-messages/compiler-warnings/compiler-warning-level-4-c4559.md)|'*función*': redefinición; el aumento de función __declspec (modificador)|
|[Advertencia del compilador (nivel 1) C4561](../../error-messages/compiler-warnings/compiler-warning-level-1-c4561.md)|'__fastcall' es incompatible con el ' / clr' opción: convertir a '__stdcall'|
|Advertencia del compilador (nivel 4) C4562|se requieren funciones prototipos totalmente con el ' / clr' opción: convirtiendo '()' a '(void)'|
|[Advertencia del compilador (nivel 4) C4564](../../error-messages/compiler-warnings/compiler-warning-level-4-c4564.md)|método '*método*'de 'class' '*classname*'define un parámetro predeterminado no admitido'*parámetro*'|
|[Advertencia del compilador (nivel 4) C4565](../../error-messages/compiler-warnings/compiler-warning-level-4-c4565.md)|'*función*': redefinición; el símbolo se declaró previamente con __declspec (modificador)|
|[Advertencia del compilador (nivel 1) C4566](../../error-messages/compiler-warnings/compiler-warning-level-1-c4566.md)|carácter representado por el nombre de carácter universal '*char*' no se puede representar en la página de códigos actual (*número*)|
|Advertencia del compilador (nivel 1) C4568|'*función*': ningún miembro coincide con la firma de la invalidación explícita|
|Advertencia del compilador (nivel 3) C4569|'*función*': ningún miembro coincide con la firma de la invalidación explícita|
|[Advertencia del compilador (nivel 3) C4570](../../error-messages/compiler-warnings/compiler-warning-level-3-c4570.md)|'*tipo*': no se declara explícitamente como abstracto pero tiene funciones abstractas|
|[Advertencia del compilador (nivel 4) C4571](../../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)|Informativo: semántica de catch (...) cambiada desde Visual C++ 7.1; ya no se detectan excepciones estructuradas (SEH)|
|[Advertencia del compilador (nivel 1) C4572](../../error-messages/compiler-warnings/compiler-warning-level-1-c4572.md)|El atributo [ParamArray] está en desuso en/CLR, use '...' en lugar de|
|Advertencia del compilador (nivel 1) C4573|el uso de '*función lambda*' requiere que el compilador capture 'this' pero no permitir que el modo de captura predeterminado actual|
|Advertencia del compilador (nivel 4) C4574|'*Identificador*'se define como ' 0': ¿pretendía usar '#if identificador'?|
|Advertencia del compilador (nivel 1) C4575|'__vectorcall' es incompatible con el ' / clr' opción: convertir a '__stdcall'|
|Advertencia del compilador (nivel 1, Error) C4576|un tipo entre paréntesis seguido de una lista de inicializadores es una sintaxis de conversión de tipo explícita no estándar|
|Advertencia del compilador (nivel 1, Off) C4577|Puede usar con ningún modo especificado; de control de excepciones 'noexcept' no se garantiza la finalización de la excepción. Especifique /EHsc|
|Advertencia del compilador (nivel 1, Error) C4578|'abs': conversión de '*type1*'para'*type2*', posible pérdida de datos (¿pretendía llamar a '*función*' o a #include \<cmath >?)|
|[Advertencia del compilador (nivel 3) C4580](../../error-messages/compiler-warnings/compiler-warning-level-3-c4580.md)|[attribute] está desusado; especifique en su lugar System::Attribute o Platform::Metadata como clase base|
|[Advertencia del compilador (nivel 1) C4581](../../error-messages/compiler-warnings/compiler-warning-level-1-c4581.md)|comportamiento desusado: ' "*cadena*"' reemplazado por '*cadena*' para procesar el atributo|
|Advertencia del compilador (nivel 4) C4582|'*tipo*': no se llama implícitamente constructor|
|Advertencia del compilador (nivel 4) C4583|'*tipo*': no se llama al destructor implícitamente|
|[Advertencia del compilador (nivel 1) C4584](../../error-messages/compiler-warnings/compiler-warning-level-1-c4584.md)|'*class1*': clase base*class2*'ya es una clase base de'*class3*'|
|Advertencia del compilador (nivel 1, Error) C4585|'*clase*': WinRT 'public ref class' debe estar sellado o derivar una clase no sellada existente|
|Advertencia del compilador (nivel 1, Error) C4586|'*tipo*': No se puede declarar un tipo público en un espacio de nombres de nivel superior llamado 'Windows'|
|Advertencia del compilador (nivel 1) C4587|'*anonymous_structure*': cambio de comportamiento: ya no es implícitamente se llama al constructor|
|Advertencia del compilador (nivel 1) C4588|'*anonymous_structure*': cambio de comportamiento: ya no es implícitamente se llama al destructor|
|Advertencia del compilador (nivel 1) C4591|límite de profundidad de llamada de 'constexpr' *número* superado (/ constexpr: Depth\<número >)|
|Advertencia del compilador (nivel 3) C4592|'*función*': error de evaluación de la llamada de 'constexpr'; se llamará la función en tiempo de ejecución|
|Advertencia del compilador (nivel 1) C4593|'*función*': límite de paso de evaluación de llamada de 'constexpr' de '*límite*"superado; use/constexpr: Steps\<número > para aumentar el límite|
|Advertencia del compilador (nivel 3) C4594|'*tipo*': un destructor no se llamará implícitamente si se produce una excepción|
|Advertencia del compilador (nivel 1) C4595|'*tipo*': cambio de comportamiento: destructor ya no se llamará implícitamente si se produce una excepción|
|Advertencia del compilador (nivel 4) C4596|'*identificador*': nombre completo no válido en la declaración de miembro|
|Advertencia del compilador C4597 (error)|un comportamiento indefinido: offsetof aplicado a un miembro de una base virtual|
|Advertencia del compilador (nivel 1 y nivel 3) C4598|' #include "*encabezado*"': el número de encabezado *número* en el encabezado precompilado no coincide con la compilación actual en esa posición|
|Advertencia del compilador (nivel 3) C4599|'*marca* *ruta*': número de argumento de línea de comandos *número* no coincide con el encabezado precompilado|
