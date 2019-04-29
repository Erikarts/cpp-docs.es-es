---
title: selectany
ms.date: 11/04/2016
f1_keywords:
- selectany_cpp
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
ms.openlocfilehash: a6bf4076dfecbd29035716285f52c0a9faf81067
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267302"
---
# <a name="selectany"></a>selectany

**Específicos de Microsoft**

Indica al compilador que el elemento de datos globales declarado (variable u objeto) es un COMDAT de selección (una función empaquetada).

## <a name="syntax"></a>Sintaxis

```
__declspec( selectany ) declarator
```

## <a name="remarks"></a>Comentarios

En tiempo de vinculación, si se ven varias definiciones de un COMDAT, el vinculador selecciona una y descarta el resto. Si la opción del vinculador [/OPT: ref](../build/reference/opt-optimizations.md) (optimizaciones) está seleccionada, se producirá la eliminación de COMDAT quitar todos los elementos de datos sin referencia en la salida del vinculador.

Los constructores y la asignación mediante una función global o métodos estáticos en la declaración no crean una referencia y no impedirán la eliminación de /OPT:REF. No se debe depender de los efectos secundarios de ese código si no existen otras referencias a los datos.

De forma dinámica los objetos globales inicializados, **selectany** código de inicialización de un objeto sin referencia, así, se descartarán.

Un elemento de datos globales se puede inicializar normalmente solo una vez en un proyecto EXE o DLL. **selectany** puede usarse en la inicialización de datos globales definidos por los encabezados cuando el mismo encabezado aparece en más de un archivo de código fuente. **selectany** está disponible en los compiladores de C y C++.

> [!NOTE]
>  **selectany** sólo puede aplicarse a la inicialización real de elementos de datos globales externamente visibles.

## <a name="example"></a>Ejemplo

Este código muestra cómo usar el **selectany** atributo:

```cpp
//Correct - x1 is initialized and externally visible
__declspec(selectany) int x1=1;

//Incorrect - const is by default static in C++, so
//x2 is not visible externally (This is OK in C, since
//const is not by default static in C)
const __declspec(selectany) int x2 =2;

//Correct - x3 is extern const, so externally visible
extern const __declspec(selectany) int x3=3;

//Correct - x4 is extern const, so it is externally visible
extern const int x4;
const __declspec(selectany) int x4=4;

//Incorrect - __declspec(selectany) is applied to the uninitialized
//declaration of x5
extern __declspec(selectany) int x5;

// OK: dynamic initialization of global object
class X {
public:
X(int i){i++;};
int i;
};

__declspec(selectany) X x(1);
```

## <a name="example"></a>Ejemplo

Este código muestra cómo usar el **selectany** atributo para garantizar el plegamiento de COMDAT de datos cuando también se utiliza el [/OPT: ICF](../build/reference/opt-optimizations.md) opción del vinculador. Tenga en cuenta que los datos deben estar marcados con **selectany** y se coloca en un **const** sección (solo lectura). Debe especificar explícitamente la sección de solo lectura.

```cpp
// selectany2.cpp
// in the following lines, const marks the variables as read only
__declspec(selectany) extern const int ix = 5;
__declspec(selectany) extern const int jx = 5;
int main() {
   int ij;
   ij = ix + jx;
}
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)