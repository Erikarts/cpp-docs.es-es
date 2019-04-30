---
title: time_put_byname (Clase)
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put_byname
helpviewer_keywords:
- time_put_byname class
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
ms.openlocfilehash: ffe7aa276e9380b6544a78c1c1735ab57765507a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411973"
---
# <a name="timeputbyname-class"></a>time_put_byname (Clase)

Una clase de plantilla derivada que describe un objeto que puede actuar como una faceta de configuración regional de tipo `time_put`\< CharType, OutputIterator >.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType, class OutIt = ostreambuf_iterator<CharType, char_traits<CharType>>>
class time_put_byname : public time_put<CharType, OutputIterator>
{
public:
    explicit time_put_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_put_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_put_byname();

};
```

### <a name="parameters"></a>Parámetros

*_Locname*<br/>
Un nombre de configuración regional.

*_Refs*<br/>
Un recuento de referencias inicial.

## <a name="remarks"></a>Comentarios

Su comportamiento viene determinado por la [denominado](../standard-library/locale-class.md#name) configuración regional *_Locname*. Cada constructor inicializa su objeto base con [time_put](../standard-library/time-put-class.md#time_put)\<CharType, OutputIterator > (`_Refs`).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
