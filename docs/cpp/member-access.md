---
title: Acceso a miembros
ms.date: 11/04/2016
helpviewer_keywords:
- member-selection operators [C++]
- pointers, smart
- member access, overloaded operators
- operator overloading [C++], member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
ms.openlocfilehash: 34527f818b135fd5af629ebb69feaffd03b715fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301635"
---
# <a name="member-access"></a>Acceso a miembros

Acceso a miembros de clase puede controlarse mediante la sobrecarga del operador de acceso de miembro (**->**). Este operador se considera un operador unario en este uso, y la función de operador sobrecargado debe ser una función miembro de clase. Por lo tanto, la declaración de una función de ese tipo es:

## <a name="syntax"></a>Sintaxis

```
class-type *operator->()
```

## <a name="remarks"></a>Comentarios

donde *tipo de clase* es el nombre de la clase a la que pertenece este operador. La función de operador de acceso a miembros debe ser una función miembro no estática.

Este operador se usa (a menudo junto con el operador de desreferenciación de puntero) para implementar "punteros inteligentes" que validan punteros antes del uso de desreferenciación o de recuento.

El elemento de lenguaje **.** no se pueden sobrecargar el operador de acceso de miembro.

## <a name="see-also"></a>Vea también

[Sobrecarga de operadores](../cpp/operator-overloading.md)