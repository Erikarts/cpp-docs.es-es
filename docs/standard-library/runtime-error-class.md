---
title: runtime_error (Clase)
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::runtime_error
helpviewer_keywords:
- runtime_error class
ms.assetid: 4d0227bf-847b-45a2-a320-2351ebf98368
ms.openlocfilehash: c4c4436c32f5f23c6bea119e95b165631384f583
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451120"
---
# <a name="runtimeerror-class"></a>runtime_error (Clase)

Clase que actúa como la clase base para todas las excepciones iniciadas para informar de errores supuestamente detectables únicamente cuando se ejecute el programa.

## <a name="syntax"></a>Sintaxis

```cpp
class runtime_error : public exception {
public:
    explicit runtime_error(const string& message);

    explicit runtime_error(const char *message);

};
```

## <a name="remarks"></a>Comentarios

El valor devuelto por [exception (Clase)](../standard-library/exception-class.md)es una copia de **message**`.`[data](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Ejemplo

```cpp
// runtime_error.cpp
// compile with: /EHsc /GR
#include <iostream>

using namespace std;

int main( )
{
// runtime_error
   try
   {
      locale loc( "test" );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught bad locale name
Type class std::runtime_error
*/
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<stdexcept>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Exception (clase)](../standard-library/exception-class.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
