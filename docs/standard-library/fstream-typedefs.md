---
title: '&lt;fstream&gt; (Typedefs)'
ms.date: 11/04/2016
f1_keywords:
- fstream/std::filebuf
- fstream/std::fstream
- fstream/std::ifstream
- fstream/std::ofstream
- fstream/std::wfilebuf
- fstream/std::wfstream
- fstream/std::wifstream
- fstream/std::wofstream
ms.assetid: 8dddef2d-7f17-42a6-ba08-6f6f20597d23
ms.openlocfilehash: 6144826254c6acc509db2c0285b21811fe37bd4e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454050"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; (Typedefs)

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>  filebuf

Tipo `basic_filebuf` especializado en parámetros de plantilla **Char** .

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_filebuf](../standard-library/basic-filebuf-class.md), especializada en elementos de tipo **Char** con rasgos de caracteres predeterminados.

## <a name="fstream"></a>  fstream

Tipo `basic_fstream` especializado en parámetros de plantilla **Char** .

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_fstream](../standard-library/basic-fstream-class.md), especializada en elementos de tipo **Char** con rasgos de caracteres predeterminados.

## <a name="ifstream"></a>  ifstream

Define una secuencia que se utilizará para leer datos de caracteres de byte único en serie desde un archivo. `ifstream`es un typedef que especializa la clase `basic_ifstream` de plantilla para **Char**.

También `wifstream`hay una definición de tipo que se `basic_ifstream` especializa en leer caracteres de doble ancho de **wchar_t** . Para obtener más información, vea [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_ifstream](../standard-library/basic-ifstream-class.md), especializada en elementos de tipo char con rasgos de caracteres predeterminados. Un ejemplo es

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a>  ofstream

Tipo `basic_ofstream` especializado en parámetros de plantilla **Char** .

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_ofstream](../standard-library/basic-ofstream-class.md), especializada en elementos de tipo **Char** con rasgos de caracteres predeterminados.

## <a name="wfstream"></a>  wfstream

Tipo `basic_fstream` especializado en parámetros de plantilla **wchar_t** .

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_fstream](../standard-library/basic-fstream-class.md), especializada en elementos de tipo **wchar_t** con rasgos de caracteres predeterminados.

## <a name="wifstream"></a>  wifstream

Tipo `basic_ifstream` especializado en parámetros de plantilla **wchar_t** .

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_ifstream](../standard-library/basic-ifstream-class.md), especializada en elementos de tipo **wchar_t** con rasgos de caracteres predeterminados.

## <a name="wofstream"></a>  wofstream

Tipo `basic_ofstream` especializado en parámetros de plantilla **wchar_t** .

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_ofstream](../standard-library/basic-ofstream-class.md), especializada en elementos de tipo **wchar_t** con rasgos de caracteres predeterminados.

## <a name="wfilebuf"></a>  wfilebuf

Tipo `basic_filebuf` especializado en parámetros de plantilla **wchar_t** .

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_filebuf](../standard-library/basic-filebuf-class.md), especializada en elementos de tipo **wchar_t** con rasgos de caracteres predeterminados.

## <a name="see-also"></a>Vea también

[\<fstream>](../standard-library/fstream.md)
