---
title: Funciones de miembro de flujo de entrada
ms.date: 11/04/2016
helpviewer_keywords:
- input stream objects
- input streams, member functions
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
ms.openlocfilehash: b046ea1995d5a8eaa39dced9feb7a5e4c422c253
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159293"
---
# <a name="input-stream-member-functions"></a>Funciones de miembro de flujo de entrada

Las funciones miembro de flujo de entrada se usan para la entrada de disco. Entre las funciones miembro se incluyen las siguientes:

- [La función open para flujos de entrada](#vclrftheopenfunctionforinputstreamsanchor11)

- [La operación get](#vclrfthegetfunctionanchor12)

- [La getline](#vclrfthegetlinefunctionanchor13)

- [La operación de lectura](#vclrfthereadfunctionanchor14)

- [Las funciones seekg y tellg](#vclrftheseekgandtellgfunctionsanchor7)

- [La función close para flujos de entrada](#vclrftheclosefunctionforinputstreamsanchor15)

## <a name="vclrftheopenfunctionforinputstreamsanchor11"></a> La función open para flujos de entrada

Si usa un flujo de archivos de entrada (ifstream), debe asociar ese flujo con un archivo de disco específico. Puede hacerlo en el constructor, o puede usar el `open` función. En cualquier caso, los argumentos son los mismos.

Normalmente se especifica un [ios_base:: OpenMode](../standard-library/ios-base-class.md#openmode) marca al abrir el archivo asociado a un flujo de entrada (el modo predeterminado es `ios::in`). Para obtener una lista de los `open_mode` marcas, vea [abrir](#vclrftheopenfunctionforinputstreamsanchor11). Las marcas se pueden combinar con el operador OR bit a bit (&#124;).

Para leer un archivo, use primero el `fail` función miembro para determinar si existe:

```cpp
istream ifile("FILENAME");

if (ifile.fail())
// The file does not exist ...
```

## <a name="vclrfthegetfunctionanchor12"></a> La operación get

El formato `get` función miembro funciona como el `>>` operador con dos excepciones. En primer lugar, el `get` función incluye caracteres de espacio en blanco, mientras que el extractor excluye el espacio en blanco cuando el `skipws` marca se establece (valor predeterminado). Segundo, el `get` función es menos probable que causen un flujo de salida vinculado (`cout`, por ejemplo) que se debe vaciar.

Una variación de la `get` función especifica una dirección de búfer y el número máximo de caracteres que se va a leer. Esto es útil para limitar el número de caracteres que se envían a una variable específica, como se muestra en este ejemplo:

```cpp
// ioo_get_function.cpp
// compile with: /EHsc
// Type up to 24 characters and a terminating character.
// Any remaining characters can be extracted later.
#include <iostream>
using namespace std;

int main()
{
   char line[25];
   cout << " Type a line terminated by carriage return\n>";
   cin.get( line, 25 );
   cout << line << endl;
}
```

### <a name="input"></a>Entrada

```Input
1234
```

### <a name="sample-output"></a>Resultados del ejemplo

```Output
1234
```

## <a name="vclrfthegetlinefunctionanchor13"></a> La getline

El `getline` es similar a la función miembro el `get` función. Ambas funciones permiten un tercer argumento que especifica el carácter de terminación de la entrada. El valor predeterminado es el carácter de nueva línea. Ambas funciones reservan un carácter para el carácter de terminación necesario, Sin embargo, `get` deja el carácter de terminación en el flujo y `getline` quita el carácter de terminación.

En el ejemplo siguiente se especifica un carácter de terminación para el flujo de entrada:

```cpp
// getline_func.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char line[100];
   cout << " Type a line terminated by 't'" << endl;
   cin.getline( line, 100, 't' );
   cout << line;
}
```

### <a name="input"></a>Entrada

```Input
test
```

## <a name="vclrfthereadfunctionanchor14"></a> La operación de lectura

El `read` función miembro lee los bytes de un archivo a un área de memoria especificada. El argumento de longitud determina el número de bytes leídos. Si no se incluye ese argumento, la lectura se detiene cuando se llega al final del archivo o, en el caso de un archivo en modo de texto, cuando se lee un carácter `EOF` incrustado.

En este ejemplo se lee un registro binario de un archivo de nóminas en una estructura:

```cpp
#include <fstream>
#include <iostream>
using namespace std;

int main()
{
   struct
   {
      double salary;
      char name[23];
   } employee;

   ifstream is( "payroll" );
   if( is ) {  // ios::operator void*()
      is.read( (char *) &employee, sizeof( employee ) );
      cout << employee.name << ' ' << employee.salary << endl;
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

El programa da por supuesto que los registros de datos tienen exactamente el mismo formato especificado por la estructura, sin caracteres de terminación de retorno de carro o avance de línea.

## <a name="vclrftheseekgandtellgfunctionsanchor7"></a> Las funciones seekg y tellg

Los flujos de archivos de entrada conservan un puntero interno a la posición del archivo en la que se van a leer los datos a continuación. Este puntero se establece con la función `seekg`, como se muestra aquí:

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main( )
{
   char ch;

   ifstream tfile( "payroll" );
   if( tfile ) {
      tfile.seekg( 8 );        // Seek 8 bytes in (past salary)
      while ( tfile.good() ) { // EOF or failure stops the reading
         tfile.get( ch );
         if( !ch ) break;      // quit on null
         cout << ch;
      }
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

Para usar `seekg` para implementar sistemas de administración de datos orientado a registro, multiplique el tamaño del registro de longitud fija por el número de registro para obtener la posición de byte en relación con el final del archivo y, a continuación, usar el `get` objeto para leer el registro.

La función miembro `tellg` devuelve la posición del archivo actual para la lectura. Este valor es de tipo `streampos`, un `typedef` definido en \<iostream>. En el ejemplo siguiente se lee un archivo y se muestran los mensajes que indican las posiciones de los espacios.

```cpp
#include <fstream>
#include <iostream>
using namespace std;

int main( )
{
   char ch;
   ifstream tfile( "payroll" );
   if( tfile ) {
       while ( tfile.good( ) ) {
          streampos here = tfile.tellg();
          tfile.get( ch );
          if ( ch == ' ' )
             cout << "\nPosition " << here << " is a space";
       }
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

## <a name="vclrftheclosefunctionforinputstreamsanchor15"></a> La función close para flujos de entrada

El `close` función miembro se cierra el archivo de disco asociado con un flujo de archivo de entrada y libera el identificador de archivo del sistema operativo. El [ifstream](../standard-library/basic-ifstream-class.md) destructor cierra el archivo, pero puede usar el `close` funcionando si necesita abrir otro archivo para el mismo objeto de secuencia.

## <a name="see-also"></a>Vea también

[Flujos de entrada](../standard-library/input-streams.md)<br/>
