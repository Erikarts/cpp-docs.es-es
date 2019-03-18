---
title: Directivas de preprocesamiento de archivos MAKE
ms.date: 06/14/2018
f1_keywords:
- '!UNDEF'
- '!INCLUDE'
- '!IFNDEF'
- '!MESSAGE'
helpviewer_keywords:
- ERROR directive
- '!MESSAGE directive'
- IF directive
- '!UNDEF directive'
- IFDEF directive
- '!ELSEIF directive'
- '!IFDEF directive'
- '!IF directive'
- UNDEF directive
- '!CMDSWITCHES directive'
- ENDIF directive
- directives, makefile preprocessing
- INCLUDE directive
- IFNDEF directive
- preprocessing directives, makefiles
- '!IFNDEF directive'
- ELSEIFNDEF directive
- NMAKE program, expressions
- ELSEIF directive
- '!ERROR directive'
- '!ENDIF directive'
- MESSAGE directive
- '!INCLUDE directive'
- '!ELSEIFNDEF directive'
- CMDSWITCHES directive
- '!ELSEIFDEF directive'
- '!ELSE directive'
- NMAKE program, preprocessor directives
- makefiles, preprocessing directives
- ELSE directive
- ELSEIFDEF directive
ms.assetid: bcedeccb-d981-469d-b9e8-ab5d097fd8c2
ms.openlocfilehash: 0945d0e1c149b7e1ab31b0dbbd5003f8b15a1e4d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826784"
---
# <a name="makefile-preprocessing-directives"></a>Directivas de preprocesamiento de archivos MAKE

Las directivas de preprocesamiento no distinguen mayúsculas de minúsculas. El punto inicial de signo de exclamación (!) debe aparecer al principio de la línea. Pueden aparecer cero o más espacios o tabulaciones después del punto de exclamación, aplicación de sangría.

- **!CMDSWITCHES** {**+** &#124; **-**}*option* ...

   Convierte cada *opción* aparece activado o desactivado. Espacios o tabulaciones deben aparecer antes del + o - operador. no pueden estar entre el operador y el [opción letras](nmake-options.md). Letras no distinguen mayúsculas de minúsculas y se especifican sin una barra diagonal (/). Para activar algunas opciones y desactivar otras, utilizar especificaciones independientes de **! CMDSWITCHES**.

   Sólo/d, / I, /N y /S se pueden usar en un archivo MAKE. En Tools.ini, se permiten todas las opciones excepto/f, / Help, / nologo, / X, y /?. Especificado en un bloque de descripción de los cambios no surtirán efecto hasta el siguiente bloque de descripción. Esta directiva actualiza **MAKEFLAGS**; los cambios se heredan durante la recursividad si **MAKEFLAGS** se especifica.

- **!ERROR**  *text*

   Muestra *texto* en error U1050 después interrumpe NMAKE, aunque/k, / I, **. OMITIR**, **! CMDSWITCHES**, o se usa el modificador de comandos de guión (-). Los espacios o tabulaciones antes *texto* se omiten.

- **!MESSAGE**  *text*

   Muestra *texto* a la salida estándar. Los espacios o tabulaciones antes *texto* se omiten.

- **! INCLUIR** [ **\<** ] *filename* [ **>** ]

   Lee *filename* como un archivo MAKE, a continuación, continúa con el archivo MAKE actual. Busca NMAKE *filename* primero en el directorio actual o especificado, a continuación, de forma recursiva a través de los directorios de cualquier principal archivos MAKE, a continuación, si *filename* está incluido entre corchetes angulares (\<>), en los directorios especificados por el **INCLUDE** macro, que inicialmente se establece en la variable de entorno INCLUDE. Es útil para pasar **. SUFIJOS** configuración, **. PRECIOSAS**y las reglas de inferencia para archivos MAKE recursivos.

- **!IF** *constant_expression*

   Procesa las instrucciones entre **! IF** y la siguiente **! ELSE** o **! ENDIF** si *constant_expression* se evalúa como un valor distinto de cero.

- **!IFDEF**  *macroname*

   Procesa las instrucciones entre **! IFDEF** y la siguiente **! ELSE** o **! ENDIF** si *Nombredelamacro* está definido. Una macro null se considera que está definida.

- **!IFNDEF**  *macroname*

   Procesa las instrucciones entre **! IFNDEF** y la siguiente **! ELSE** o **! ENDIF** si *Nombredelamacro* no está definido.

- **!ELSE** [**IF** *constant_expression* &#124; **IFDEF** *macroname* &#124; **IFNDEF** *macroname*]

   Procesa las instrucciones entre **! ELSE** y la siguiente **! ENDIF** si previo **! IF**, **! IFDEF**, o **! IFNDEF** instrucción que se evalúa como cero. Las palabras clave opcionales ofrecen un control de preprocesamiento.

- **!ELSEIF**

   Sinónimo de **! ELSE IF**.

- **!ELSEIFDEF**

   Sinónimo de **! ELSE IFDEF**.

- **!ELSEIFNDEF**

   Sinónimo de **! IFNDEF ELSE**.

- **!ENDIF**

   Marca el final de un **! IF**, **! IFDEF**, o **! IFNDEF** bloque. Cualquier texto situado tras **! ENDIF** se omite en la misma línea.

- **!UNDEF**  *macroname*

   Anulación del *Nombredelamacro*.

## <a name="see-also"></a>Vea también

- [Preprocesamiento de archivos MAKE](makefile-preprocessing.md)