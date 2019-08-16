---
title: Advertencia del compilador (nivel 1) C4691
ms.date: 11/04/2016
f1_keywords:
- C4691
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
ms.openlocfilehash: c194e19c8766b67eb7deef32e7228564cda5f1e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406384"
---
# <a name="compiler-warning-level-1-c4691"></a>Advertencia del compilador (nivel 1) C4691

'type': se esperaba el tipo al que hace referencia en el ensamblado sin referencia 'archivo', tipo definido en la unidad de traducción actual utilizado en su lugar

No se hace referencia el archivo de metadatos que contiene la definición del tipo original y el compilador está utilizando una definición de tipo local.

En el caso donde está reconstruyendo *archivo*, C4691 puede se omitirán o se ha desactivado con pragma [advertencia](../../preprocessor/warning.md).  Es decir, si el archivo que se va a compilar es el mismo que el archivo donde el compilador espera encontrar la definición de tipo, puede omitir la advertencia C4691.

Sin embargo, puede producirse un comportamiento inesperado si el compilador utiliza una definición que no esté en el mismo ensamblado que se hace referencia en los metadatos; Tipos CLR se escriben no solo por el nombre del tipo, sino también el ensamblado.  Es decir, un tipo Z del ensamblado z.dll es diferente de un tipo Z del ensamblado y.dll.

## <a name="example"></a>Ejemplo

Este ejemplo contiene la definición de tipo original.

```
// C4691_a.cpp
// compile with: /clr /LD /W1
public ref class Original_Type {};
```

## <a name="example"></a>Ejemplo

Este ejemplo hace referencia a C4691_a.dll y declara un campo de tipo Original_Type.

```
// C4691_b.cpp
// compile with: /clr /LD
#using "C4691_a.dll"
public ref class Client {
public:
   Original_Type^ ot;
};
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4691.  Observe que este ejemplo contiene una definición para Original_Type y no hace referencia a C4691a.dll.

Para resolver, hacer referencia al archivo de metadatos que contiene la definición del tipo original y quite la declaración local y la definición.

```
// C4691_c.cpp
// compile with: /clr /LD /W1
// C4691 expected

// Uncomment the following line to resolve.
// #using "C4691_a.dll"
#using "C4691_b.dll"

// Delete the following line to resolve.
ref class Original_Type;

public ref class MyClass : Client {};
```