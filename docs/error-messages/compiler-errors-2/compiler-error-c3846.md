---
title: Error del compilador C3846
ms.date: 11/04/2016
f1_keywords:
- C3846
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
ms.openlocfilehash: 788f03e4364404ad5c30b7edcba8b743c7f201ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152428"
---
# <a name="compiler-error-c3846"></a>Error del compilador C3846

'símbolo': no se puede importar un símbolo desde 'assembly2': como "symbol" ya se ha importado desde otro ensamblado 'assembly1'

No se pudo importar un símbolo desde un ensamblado de referencia porque ya se había importado desde un ensamblado de referencia.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3846:

```
// C3846a.cpp
// compile with: /LD /clr
public ref struct G
{
};
```

Y, a continuación, compile esto:

```
// C3846b.cpp
// compile with: /clr
#using "c3846a.dll"
#using "c3846a.obj"   // C3846

int main()
{
}
```
