---
title: Procedimiento Definir y usar enumeraciones en C++ / c++ / CLI
ms.date: 11/04/2016
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
ms.openlocfilehash: 9787b7b96f83b2926c65209254c88eb56fe1a8ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387388"
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>Procedimiento Definir y usar enumeraciones en C++ / c++ / CLI

Este tema describen las enumeraciones en C++ / c++ / CLI.

## <a name="specifying-the-underlying-type-of-an-enum"></a>Especifica el tipo subyacente de una enumeración

De forma predeterminada, el tipo subyacente de una enumeración es `int`.  Sin embargo, puede especificar el tipo para que los formularios con o sin signo de `int`, `short`, `long`, `__int32`, o `__int64`.  También puede usar `char`.

```
// mcppv2_enum_3.cpp
// compile with: /clr
public enum class day_char : char {sun, mon, tue, wed, thu, fri, sat};

int main() {
   // fully qualified names, enumerator not injected into scope
   day_char d = day_char::sun, e = day_char::mon;
   System::Console::WriteLine(d);
   char f = (char)d;
   System::Console::WriteLine(f);
   f = (char)e;
   System::Console::WriteLine(f);
   e = day_char::tue;
   f = (char)e;
   System::Console::WriteLine(f);
}
```

**Salida**

```Output
sun
0
1
2
```

## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>Cómo convertir entre enumeraciones administradas y estándar

No hay ninguna conversión estándar entre una enumeración y un tipo entero; se requiere una conversión.

```
// mcppv2_enum_4.cpp
// compile with: /clr
enum class day {sun, mon, tue, wed, thu, fri, sat};
enum {sun, mon, tue, wed, thu, fri, sat} day2; // unnamed std enum

int main() {
   day a = day::sun;
   day2 = sun;
   if ((int)a == day2)
   // or...
   // if (a == (day)day2)
      System::Console::WriteLine("a and day2 are the same");
   else
      System::Console::WriteLine("a and day2 are not the same");
}
```

**Salida**

```Output
a and day2 are the same
```

## <a name="operators-and-enums"></a>Operadores y enumeraciones

Los siguientes operadores son válidos en enumeraciones en C++ / c++ / CLI:

|Operador|
|--------------|
|== != \< > \<= >=|
|+ -|
|&#124; ^ & ~|
|++ --|
|sizeof|

Operadores &#124; ^ & ~ ++--se definen sólo para las enumeraciones con integral de los tipos, sin incluir bool subyacentes.  Ambos operandos deben ser del tipo de enumeración.

El compilador no realiza ninguna comprobación estática o dinámica del resultado de una operación de enumeración; una operación puede producir un valor no está en el intervalo de enumeradores válido de la enumeración.

> [!NOTE]
>  C ++ 11 incluye tipos de clase de enumeración en código no administrado que son significativamente diferentes de las clases de enumeración administrada en C++ / c++ / CLI. En concreto, el tipo de clase C ++ 11 enum no admite los mismos operadores que el tipo de clase de enumeración administrada en C++ / c++ / CLI y C++ / c++ / CLI origen el código debe proporcionar un especificador de accesibilidad en la enumeración administrada declaraciones de clase para distinguirlos de los no administrados (C++ 11) declaraciones de clase enum de. Para obtener más información acerca de las clases de enumeración en C / c++ / CLI, C++ / c++ / CX y C ++ 11, vea [clase enum](../extensions/enum-class-cpp-component-extensions.md).

```
// mcppv2_enum_5.cpp
// compile with: /clr
private enum class E { a, b } e, mask;
int main() {
   if ( e & mask )   // C2451 no E->bool conversion
      ;

   if ( ( e & mask ) != 0 )   // C3063 no operator!= (E, int)
      ;

   if ( ( e & mask ) != E() )   // OK
      ;
}
```

```
// mcppv2_enum_6.cpp
// compile with: /clr
private enum class day : int {sun, mon};
enum : bool {sun = true, mon = false} day2;

int main() {
   day a = day::sun, b = day::mon;
   day2 = sun;

   System::Console::WriteLine(sizeof(a));
   System::Console::WriteLine(sizeof(day2));
   a++;
   System::Console::WriteLine(a == b);
}
```

**Salida**

```Output
4
1
True
```

## <a name="see-also"></a>Vea también

[enum class](../extensions/enum-class-cpp-component-extensions.md)
