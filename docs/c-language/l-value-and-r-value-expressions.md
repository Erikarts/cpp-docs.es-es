---
title: Expresiones de valor L y valor R
ms.date: 11/04/2016
helpviewer_keywords:
- L-values
- member-selection expressions
- R-value expressions
- subscript expressions
ms.assetid: b790303e-ec6f-4d0d-bc55-df42da267172
ms.openlocfilehash: bd5f702588a11b7841f77de539d113206833cde9
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150225"
---
# <a name="l-value-and-r-value-expressions"></a>Expresiones de valor L y valor R

Las expresiones que hacen referencia a ubicaciones de memoria se denominan expresiones de “valor L”. Un valor L representa un valor de "localizador" de la región de almacenamiento o un valor "izquierdo", lo que implica que puede aparecer a la izquierda del signo igual (**=**). Los valores L suelen ser identificadores.

Las expresiones que hacen referencia a ubicaciones modificables se denominan “valores L modificables”. Un valor L modificable no puede tener un tipo de matriz, un tipo incompleto ni o un tipo con el atributo **const**. Para que las estructuras y las uniones sean valores L modificables, no deben tener ningún miembro con el atributo **const**. El nombre del identificador indica una ubicación de almacenamiento, mientras que el valor de la variable es el valor almacenado en esa ubicación.

Un identificador es un valor L modificable si hace referencia a una ubicación de memoria y si su tipo es aritmético, de estructura, de unión o de puntero. Por ejemplo, si `ptr` es un puntero a una región de almacenamiento, entonces `*ptr` es un valor L modificable que designa la región de almacenamiento a la que señala `ptr`.

Cualquiera de las siguientes expresiones de C pueden ser expresiones de valor L:

- Un identificador de tipo entero, flotante, puntero, estructura o unión

- Una expresión de subíndice (**[ ]**) que no se evalúe como una matriz

- Una expresión de selección de miembro (**->** o **.**)

- Una expresión de direccionamiento indirecto unario (<strong>\*</strong>) que no hace referencia a una matriz

- Una expresión de valor L entre paréntesis

- Un objeto **const** (un valor L no modificable)

El término “valor R” se utiliza a veces para describir el valor de una expresión y distinguirlo de un valor L. Todos los valores L son valores R, pero no todos los valores R son valores L.

**Específicos de Microsoft**

Microsoft C incluye una extensión del estándar ANSI C que permite que las conversiones de valores L se usen valores L, siempre que el tamaño del objeto no se alargue debido a la conversión. (Vea [Conversiones de tipos](../c-language/type-cast-conversions.md) para obtener más información). En el ejemplo siguiente se ilustra esta característica.

```
char *p ;
short  i;
long l;

(long *) p = &l ;       /* Legal cast   */
(long) i = l ;          /* Illegal cast */
```

El valor predeterminado para Microsoft C es que las extensiones de Microsoft estén habilitadas. Utilice la opción de compilador /Za para deshabilitar estas extensiones.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Operandos y expresiones](../c-language/operands-and-expressions.md)
