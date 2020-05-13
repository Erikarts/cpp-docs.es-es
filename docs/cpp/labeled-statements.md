---
title: Instrucciones con etiqueta
ms.date: 11/04/2016
helpviewer_keywords:
- labeled statement
- statements, labeled
ms.assetid: 456a26d5-0fcc-4d1a-b71f-fa9ff3d73b91
ms.openlocfilehash: d971a0e9864aeada1db5f004ef70577512e78c76
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179697"
---
# <a name="labeled-statements"></a>Instrucciones con etiqueta

Las etiquetas se usan para transferir el control de programas directamente a la instrucción especificada.

```
identifier :  statement
case constant-expression :  statement
default :  statement
```

El ámbito de una etiqueta es toda la función donde se declara.

## <a name="remarks"></a>Observaciones

Hay tres tipos de instrucciones con etiquetas. En todas ellas se utiliza el carácter de dos puntos para distinguir el tipo de etiqueta de la instrucción. La etiqueta case y las etiquetas predeterminadas son específicas para las instrucciones case.

```cpp
#include <iostream>
using namespace std;

void test_label(int x) {

    if (x == 1){
        goto label1;
    }
    goto label2;

label1:
    cout << "in label1" << endl;
    return;

label2:
    cout << "in label2" << endl;
    return;
}

int main() {
    test_label(1);  // in label1
    test_label(2);  // in label2
}
```

**La instrucción Goto**

La apariencia de una etiqueta de *identificador* en el programa de origen declara una etiqueta. Solo una instrucción [goto](../cpp/goto-statement-cpp.md) puede transferir el control a una etiqueta de *identificador* . En el fragmento de código siguiente se muestra el uso de la instrucción **goto** y una etiqueta *Identifier* :

Una etiqueta no puede aparecer por sí misma; debe estar asociada siempre a una instrucción. Si se necesita la propia etiqueta, coloque una instrucción null detrás de la etiqueta.

La etiqueta tiene ámbito de función y no se puede volver a declarar dentro de la función. Sin embargo, se puede utilizar el mismo nombre como una etiqueta en diferentes funciones.

```cpp
// labels_with_goto.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   using namespace std;
   goto Test2;

   cout << "testing" << endl;

   Test2:
      cerr << "At Test2 label." << endl;
}

//Output: At Test2 label.
```

**La instrucción Case**

Las etiquetas que aparecen después de la palabra clave **Case** también no pueden aparecer fuera de una instrucción **Switch** . (Esta restricción también se aplica a la palabra clave **default** ). En el fragmento de código siguiente se muestra el uso correcto de las etiquetas **Case** :

```cpp
// Sample Microsoft Windows message processing loop.
switch( msg )
{
   case WM_TIMER:    // Process timer event.
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );
      ShowWindow( hWnd, SW_SHOWNA );
      nIcon %= 14;
      Yield();
      break;

   case WM_PAINT:
      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );
      hDC = BeginPaint( hWnd, &ps );
      EndPaint( hWnd, &ps );
      break;

   default:
      // This choice is taken for all messages not specifically
      //  covered by a case statement.

      return DefWindowProc( hWnd, Message, wParam, lParam );
      break;
}
```

## <a name="labels-in-the-case-statement"></a>Etiquetas en la instrucción case

Las etiquetas que aparecen después de la palabra clave **Case** también no pueden aparecer fuera de una instrucción **Switch** . (Esta restricción también se aplica a la palabra clave **default** ). En el fragmento de código siguiente se muestra el uso correcto de las etiquetas **Case** :

```cpp
// Sample Microsoft Windows message processing loop.
switch( msg )
{
   case WM_TIMER:    // Process timer event.
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );
      ShowWindow( hWnd, SW_SHOWNA );
      nIcon %= 14;
      Yield();
      break;

   case WM_PAINT:
      // Obtain a handle to the device context.
      // BeginPaint will send WM_ERASEBKGND if appropriate.

      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );
      hDC = BeginPaint( hWnd, &ps );

      // Inform Windows that painting is complete.

      EndPaint( hWnd, &ps );
      break;

   case WM_CLOSE:
      // Close this window and all child windows.

      KillTimer( hWnd, TIMER1 );
      DestroyWindow( hWnd );
      if ( hWnd == hWndMain )
         PostQuitMessage( 0 );  // Quit the application.
      break;

   default:
      // This choice is taken for all messages not specifically
      //  covered by a case statement.

      return DefWindowProc( hWnd, Message, wParam, lParam );
      break;
}
```

## <a name="labels-in-the-goto-statement"></a>Etiquetas en la instrucción goto

La apariencia de una etiqueta de *identificador* en el programa de origen declara una etiqueta. Solo una instrucción [goto](../cpp/goto-statement-cpp.md) puede transferir el control a una etiqueta de *identificador* . En el fragmento de código siguiente se muestra el uso de la instrucción **goto** y una etiqueta *Identifier* :

Una etiqueta no puede aparecer por sí misma; debe estar asociada siempre a una instrucción. Si se necesita la propia etiqueta, coloque una instrucción null detrás de la etiqueta.

La etiqueta tiene ámbito de función y no se puede volver a declarar dentro de la función. Sin embargo, se puede utilizar el mismo nombre como una etiqueta en diferentes funciones.

```cpp
// labels_with_goto.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   using namespace std;
   goto Test2;

   cout << "testing" << endl;

   Test2:
      cerr << "At Test2 label." << endl;
// At Test2 label.
}
```

## <a name="see-also"></a>Consulte también

[Información general sobre las instrucciones de C++](../cpp/overview-of-cpp-statements.md)<br/>
[switch (Instrucción) (C++)](../cpp/switch-statement-cpp.md)
