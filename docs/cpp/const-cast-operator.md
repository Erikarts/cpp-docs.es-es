---
title: const_cast (Operador)
ms.date: 11/04/2016
f1_keywords:
- const_cast_cpp
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
ms.openlocfilehash: 389ef84149031fd602ff9ded15d34869258ffd52
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399114"
---
# <a name="constcast-operator"></a>const_cast (Operador)

Quita el **const**, **volátil**, y **__unaligned** atributos de una clase.

## <a name="syntax"></a>Sintaxis

```
const_cast <type-id> (expression)
```

## <a name="remarks"></a>Comentarios

Un puntero a cualquier tipo de objeto o un puntero a un miembro de datos se puede convertir explícitamente a un tipo que es idéntico, salvo para la **const**, **volátil**, y **__unaligned** calificadores. Para los punteros y las referencias, el resultado hará referencia al objeto original. Para los punteros a miembros de datos, el resultado hará referencia al mismo miembro que el puntero original (sin convertir) al miembro de datos. Según el tipo del objeto al que se hace referencia, una operación de escritura a través del puntero, referencia o puntero a miembro de datos resultante podría generar un comportamiento indefinido.

No puede usar el **const_cast** operador para invalidar directamente el estado constante de una variable constante.

El **const_cast** operador convierte un valor de puntero nulo en el valor de puntero null del tipo de destino.

## <a name="example"></a>Ejemplo

```cpp
// expre_const_cast_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class CCTest {
public:
   void setNumber( int );
   void printNumber() const;
private:
   int number;
};

void CCTest::setNumber( int num ) { number = num; }

void CCTest::printNumber() const {
   cout << "\nBefore: " << number;
   const_cast< CCTest * >( this )->number--;
   cout << "\nAfter: " << number;
}

int main() {
   CCTest X;
   X.setNumber( 8 );
   X.printNumber();
}
```

En la línea que contiene el **const_cast**, tipo de datos de la **esto** puntero es `const CCTest *`. El **const_cast** operador cambia el tipo de datos de la **esto** puntero a `CCTest *`, lo que permite el miembro `number` va a modificar. La conversión se produce únicamente para el resto de la instrucción en la que aparece.

## <a name="see-also"></a>Vea también

[Operadores de conversión](../cpp/casting-operators.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)