---
title: 'Administración de memoria: Asignación de marcos'
ms.date: 11/04/2016
helpviewer_keywords:
- memory leaks [MFC], frame allocation
- memory [MFC], detecting leaks
- memory [MFC], reclaiming
- memory allocation [MFC], frames
- frame variables [MFC], automatic deletion of
- scope [MFC], frame variables
- heap allocation [MFC], vs. frame allocation
- variables [MFC], frame variables
- memory leaks [MFC], detecting
- memory, releasing [MFC]
- stack frames [MFC]
- memory leaks [MFC], allocating objects on the frame
- detecting memory leaks [MFC]
- frame allocation [MFC]
- frame variables [MFC]
ms.assetid: 945a211a-6f4f-4679-bb6a-b0f2a0d4a6c1
ms.openlocfilehash: 1acf2ce89e18dd64c166103b59b5eb7007214efd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352133"
---
# <a name="memory-management-frame-allocation"></a>Administración de memoria: Asignación de marcos

Asignación en el marco toma su nombre de la "marco de pila" que se establece cada vez que se llama a una función. El marco de pila es un área de memoria que contiene de forma temporal los argumentos a la función, así como las variables que se definen local a la función. Las variables de marco a menudo se denominan variables "automáticas" porque el compilador asigna automáticamente el espacio para ellos.

Hay dos características clave de asignación en el marco. En primer lugar, al definir una variable local, se asigna espacio suficiente en el marco de pila para contener la variable completa, incluso si es una matriz de gran tamaño o la estructura de datos. En segundo lugar, las variables de marco se eliminan automáticamente cuando salen del ámbito:

[!code-cpp[NVC_MFC_Utilities#10](../mfc/codesnippet/cpp/memory-management-frame-allocation_1.cpp)]

Variables de función local, esta transición de ámbito se produce cuando la función finaliza, pero el ámbito de una variable de marco puede ser menor que una función de si se usan llaves anidadas. Esta eliminación automática de las variables de marco es muy importante. En el caso de tipos primitivos simples (como **int** o **bytes**), matrices o estructuras de datos, la eliminación automática simplemente reclama la memoria utilizada por la variable. Puesto que la variable se ha salido del ámbito, no se puede acceder a él de todos modos. Sin embargo, en el caso de los objetos de C++, el proceso de eliminación automática es un poco más complicado.

Cuando un objeto se define como una variable de marco, se invoca automáticamente su constructor en el punto donde se encuentra la definición. Cuando el objeto queda fuera del ámbito, su destructor se invoca automáticamente antes de la memoria para el objeto sea reclamada. Esta construcción y destrucción automáticas pueden ser muy útiles, pero debe ser consciente de las llamadas automáticas, especialmente al destructor.

La ventaja clave de asignación de objetos en el marco es que se eliminen automáticamente. Cuando se asignan los objetos en el marco, no tiene que preocuparse por las pérdidas de memoria por objetos olvidados. (Para obtener más información sobre las pérdidas de memoria, vea el artículo [detectar pérdidas de memoria en MFC](/previous-versions/visualstudio/visual-studio-2010/c99kz476(v=vs.100)).) Una desventaja de asignación en el marco es que las variables de marco no se puede usar fuera de su ámbito. Otro factor para elegir la asignación de marcos en comparación con la asignación del montón es que para las estructuras de gran tamaño y objetos, a menudo es mejor utilizar el montón en lugar de la pila para el almacenamiento, puesto que el espacio de pila se limita a menudo.

## <a name="see-also"></a>Vea también

[Administración de memoria](../mfc/memory-management.md)
