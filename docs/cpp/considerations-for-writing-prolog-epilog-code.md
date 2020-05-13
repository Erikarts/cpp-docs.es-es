---
title: Consideraciones para escribir código de prólogo/epílogo
ms.date: 11/04/2016
helpviewer_keywords:
- stack frame layout
- prolog code
- epilog code
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
ms.openlocfilehash: cda6a6c82efcf30a916aced121024095d7ce8138
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337108"
---
# <a name="considerations-for-writing-prologepilog-code"></a>Consideraciones para escribir código de prólogo/epílogo

**Microsoft Specific**

Antes de escribir sus propias secuencias de código de prólogo y epílogo, es importante comprender cómo se establece el marco de pila. También es útil saber cómo `__LOCAL_SIZE` utilizar el símbolo.

## <a name="stack-frame-layout"></a><a name="_pluslang_c.2b2b_.stack_frame_layout"></a>Diseño de marco de pila

En este ejemplo se muestra el código de prólogo estándar que puede aparecer en una función de 32 bits:

```
push        ebp                ; Save ebp
mov         ebp, esp           ; Set stack frame pointer
sub         esp, localbytes    ; Allocate space for locals
push        <registers>        ; Save registers
```

La variable `localbytes` representa el número de bytes necesarios en la pila para las variables locales y la variable `<registers>` es un marcador de posición que representa la lista de registros que se guarden en la pila. Después de insertar los registros, puede colocar cualquier otro dato adecuado en la pila. A continuación, se muestra el código de epílogo correspondiente:

```
pop         <registers>   ; Restore registers
mov         esp, ebp      ; Restore stack pointer
pop         ebp           ; Restore ebp
ret                       ; Return from function
```

La pila siempre va de mayor a menor (de las direcciones de memoria superiores a las inferiores). El puntero base (`ebp`) señala al valor insertado de `ebp`. El área de valores locales comienza en `ebp-4`. Para tener acceso a las variables locales, calcule un desplazamiento de `ebp` restando el valor apropiado a `ebp`.

## <a name="__local_size"></a><a name="_pluslang___local_size"></a>__LOCAL_SIZE

El compilador proporciona `__LOCAL_SIZE`un símbolo, , para su uso en el bloque ensamblador en línea del código de prólogo de función. Este símbolo se utiliza para asignar espacio para variables locales del marco de pila en código de prólogo personalizado.

El compilador determina el `__LOCAL_SIZE`valor de . Su valor es el número total de bytes de todas las variables locales definidas por el usuario y las variables temporales generadas por el compilador. `__LOCAL_SIZE`sólo se puede utilizar como operando inmediato; no se puede utilizar en una expresión. No debe cambiar o volver a definir el valor de este símbolo. Por ejemplo:

```
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov        eax, [ebp - __LOCAL_SIZE]   ;Error
```

El siguiente ejemplo de una función desnuda que contiene `__LOCAL_SIZE` secuencias de prólogo y epílogo personalizadas utiliza el símbolo en la secuencia de prólogo:

```cpp
// the__local_size_symbol.cpp
// processor: x86
__declspec ( naked ) int main() {
   int i;
   int j;

   __asm {      /* prolog */
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */
   __asm {   /* epilog */
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**END Microsoft Specific**

## <a name="see-also"></a>Consulte también

[Llamadas de función naked](../cpp/naked-function-calls.md)
