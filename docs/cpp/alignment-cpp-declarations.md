---
title: Alineación (declaraciones de C++)
ms.date: 11/04/2016
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
ms.openlocfilehash: 0709ad414af3f167a64d9c89c342690015190287
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155399"
---
# <a name="alignment-c-declarations"></a>Alineación (declaraciones de C++)

Una de las características de bajo nivel de C++ es la capacidad para especificar la alineación precisa de los objetos en la memoria para sacar el máximo partido de una arquitectura de hardware específica. De forma predeterminada, el compilador alinea los miembros de clase y estructura en su valor de tamaño: bool y char se alinea en límites de un byte, short en dos bytes, int en cuatro bytes y long long, double y long dos en ocho bytes. En la mayoría de los escenarios no tendrá que preocuparse jamás por la alineación, puesto que la alineación predeterminada ya es óptima. No obstante, en algunos casos se pueden conseguir importantes mejoras de rendimiento o ahorros de memoria al especificar una alineación personalizada para sus estructuras de datos. Antes de Visual Studio 2015 podía usar las palabras clave __alignof y declspec(alignas) específicas de Microsoft para especificar una alineación mayor que el valor predeterminado. A partir de Visual Studio 2015, debe utilizar el C ++ 11 palabras clave estándar [alignof y alignas](../cpp/alignof-and-alignas-cpp.md) para la portabilidad de código al máximo. A efectos prácticos, las nuevas palabras clave se comportan de la misma manera que las extensiones específicas de Microsoft. Además, la documentación de esas extensiones también se aplica a las nuevas palabras clave. Consulte [operador __alignof](../cpp/alignof-operator.md) y [alinear](../cpp/align-cpp.md) para obtener más información. El estándar de C++ no especifica el comportamiento de empaquetado para alinear en límites menores que el valor predeterminado del compilador para la plataforma de destino, por lo que deberá usar Microsoft #pragma [pack](../preprocessor/pack.md) en ese caso.

El C++ biblioteca estándar proporciona el [aligned_storage (clase)](../standard-library/aligned-storage-class.md) para asignar memoria para las estructuras de datos con alineaciones personalizadas y la [clase aligned_union](../standard-library/aligned-union-class.md) para especificar la alineación de uniones con constructores no triviales o destructores.

## <a name="about-alignment"></a>Acerca de la alineación

La alineación es una propiedad de una dirección de memoria, expresada como el módulo de la dirección numérica a una potencia de 2. Por ejemplo, la dirección 0x0001103F módulo 4 es 3; se dice que esa dirección está alineada con 4n+3, donde 4 indica la potencia de 2 elegida. La alineación de una dirección depende de la potencia de dos elegida. El mismo módulo de dirección 8 es 7. Se dice que una dirección está alineada con X si su alineación es Xn+0.

Las CPU ejecutan instrucciones que operan en los datos almacenados en la memoria y los datos se identifican por sus direcciones en la memoria. Además de su dirección, un dato individual también tiene un tamaño. Se dice que un dato está alineado naturalmente si su dirección está alineada a su tamaño y desalineado si no lo está. Por ejemplo, un dato de punto flotante de 8 bytes se encuentra alineado naturalmente si la dirección que se utiliza para identificarlo está alineada a 8.

Control del compilador de datos alignmentDevice compiladores intentan asignar datos de forma que impide que un error de alineación de datos.

Para los tipos de datos simples, el compilador asigna direcciones que son múltiplos del tamaño en bytes del tipo de datos. De este modo, el compilador asigna direcciones a variables de tipo long que son múltiplos de cuatro, estableciendo los dos bits de la parte inferior de la dirección en cero.

Además, el compilador rellena las estructuras de tal manera que alinea naturalmente cada elemento de la estructura. Considere la estructura struct x_ en el siguiente ejemplo de código:

```cpp
struct x_
{
   char a;     // 1 byte
   int b;      // 4 bytes
   short c;    // 2 bytes
   char d;     // 1 byte
} MyStruct;
```

El compilador rellena esta estructura para aplicar la alineación de forma natural.

En el siguiente ejemplo de código se muestra cómo el compilador coloca la estructura rellenada en memoria:

```cpp
// Shows the actual memory layout
struct x_
{
   char a;            // 1 byte
   char _pad0[3];     // padding to put 'b' on 4-byte boundary
   int b;            // 4 bytes
   short c;          // 2 bytes
   char d;           // 1 byte
   char _pad1[1];    // padding to make sizeof(x_) multiple of 4
}
```

1. Ambas declaraciones devuelven sizeof(struct x_) como 12 bytes.

1. La segunda declaración incluye dos elementos de relleno:

1. char _pad0[3] para alinear el miembro int b en un límite de cuatro bytes y

1. char _pad1[1] para alinear los elementos de la matriz de la estructura _x struct bar[3].

1. El relleno alinea los elementos de bar[3] de tal forma que permite el acceso natural.

En el código de ejemplo siguiente se muestra el diseño de matriz bar[3]:

```
adr offset   element
------   -------
0x0000   char a;         // bar[0]
0x0001   char pad0[3];
0x0004   int b;
0x0008   short c;
0x000a   char d;
0x000b   char _pad1[1];

0x000c   char a;         // bar[1]
0x000d   char _pad0[3];
0x0010   int b;
0x0014   short c;
0x0016   char d;
0x0017   char _pad1[1];

0x0018   char a;         // bar[2]
0x0019   char _pad0[3];
0x001c   int b;
0x0020   short c;
0x0022   char d;
0x0023   char _pad1[1];
```

## <a name="see-also"></a>Vea también

[Alineación de estructuras de datos](http://en.wikipedia.org/wiki/Data_structure_alignment)