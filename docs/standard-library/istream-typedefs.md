---
title: Definiciones de tipo &lt;istream&gt;
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: f647fba2036f6c69cb02393e30553c66df34b9dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413299"
---
# <a name="ltistreamgt-typedefs"></a>Definiciones de tipo &lt;istream&gt;

||||
|-|-|-|
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a>  iostream

Un tipo `basic_iostream` especializado en **char**.

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_iostream](../standard-library/basic-iostream-class.md), especializada en elementos del tipo **char** con rasgos de caracteres predeterminados.

## <a name="istream"></a>  istream

Un tipo `basic_istream` especializado en **char**.

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_istream](../standard-library/basic-istream-class.md), especializada en elementos del tipo **char** con rasgos de caracteres predeterminados.

## <a name="wiostream"></a>  wiostream

Un tipo `basic_iostream` especializado en **wchar_t**.

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_iostream](../standard-library/basic-iostream-class.md), especializada en elementos del tipo **wchar_t** con rasgos de caracteres predeterminados.

## <a name="wistream"></a>  wistream

Un tipo `basic_istream` especializado en **wchar_t**.

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_istream](../standard-library/basic-istream-class.md), especializada en elementos del tipo **wchar_t** con rasgos de caracteres predeterminados.

## <a name="see-also"></a>Vea también

[\<istream>](../standard-library/istream.md)<br/>
