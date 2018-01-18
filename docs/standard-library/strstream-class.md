---
title: strstream (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- strstream/std::strstream::freeze
- strstream/std::strstream::pcount
- strstream/std::strstream::rdbuf
- strstream/std::strstream::str
dev_langs: C++
helpviewer_keywords:
- std::strstream [C++], freeze
- std::strstream [C++], pcount
- std::strstream [C++], rdbuf
- std::strstream [C++], str
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2e11fade0bf5bf6f816f273250217be24c8bc87c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="strstream-class"></a>strstream (Clase)
Describe un objeto que controla la inserción y la extracción de objetos codificados y elementos usando un búfer de secuencia de la clase [strstreambuf](../standard-library/strstreambuf-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```
class strstream : public iostream
```  
  
## <a name="remarks"></a>Comentarios  
 El objeto almacena un objeto de clase `strstreambuf`.  
  
> [!NOTE]
>  Esta clase está en desuso. Considere el uso de [stringstream](../standard-library/sstream-typedefs.md#stringstream) o [wstringstream](../standard-library/sstream-typedefs.md#wstringstream) en su lugar.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[strstream](#strstream)|Construye un objeto de tipo `strstream`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[freeze](#freeze)|Hace que un búfer de secuencia no esté disponible a través de las operaciones de búfer de secuencia.|  
|[pcount](#pcount)|Devuelve un recuento del número de elementos que se escriben en la secuencia controlada.|  
|[rdbuf](#rdbuf)|Devuelve un puntero al objeto `strstreambuf` asociado de la secuencia.|  
|[str](#str)|Llama a [freeze](../standard-library/strstreambuf-class.md#freeze) y, después, devuelve un puntero al principio de la secuencia controlada.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<strstream>  
  
 **Espacio de nombres:** std  
  
##  <a name="freeze"></a>  strstream::freeze  
 Hace que un búfer de secuencia no esté disponible a través de las operaciones de búfer de secuencia.  
  
```
void freeze(bool _Freezeit = true);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Freezeit`  
 Un `bool` que indica si quiere que la secuencia se detenga.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro llama a [rdbuf](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).  
  
### <a name="example"></a>Ejemplo  
  Vea [strstreambuf::freeze](../standard-library/strstreambuf-class.md#freeze) para obtener un ejemplo que usa **freeze**.  
  
##  <a name="pcount"></a>  strstream::pcount  
 Devuelve un recuento del número de elementos que se escriben en la secuencia controlada.  
  
```
streamsize pcount() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos que se escriben en la secuencia controlada.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).  
  
### <a name="example"></a>Ejemplo  
  Vea [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) para obtener un ejemplo del uso de pcount.  
  
##  <a name="rdbuf"></a>  strstream::rdbuf  
 Devuelve un puntero al objeto strstreambuf asociado de la secuencia.  
  
```
strstreambuf *rdbuf() const
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto strstreambuf asociado del flujo.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve la dirección del búfer de secuencia almacenado de tipo **pointer** a [strstreambuf](../standard-library/strstreambuf-class.md).  
  
### <a name="example"></a>Ejemplo  
  Vea [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) para obtener un ejemplo que usa `rdbuf`.  
  
##  <a name="str"></a>  strstream::str  
 Llama a [freeze](../standard-library/strstreambuf-class.md#freeze) y, después, devuelve un puntero al principio de la secuencia controlada.  
  
```
char *str();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al principio de la secuencia controlada.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).  
  
### <a name="example"></a>Ejemplo  
  Vea [strstreambuf::str](../standard-library/strstreambuf-class.md#str) para obtener un ejemplo que usa **str**.  
  
##  <a name="strstream"></a>  strstream::strstream  
 Construye un objeto de tipo `strstream`.  
  
```
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>Parámetros  
 `count`  
 Tamaño del búfer.  
  
 `_Mode`  
 El modo de entrada y salida del búfer. Vea [ios_base::openmode](../standard-library/ios-base-class.md#openmode) para más información.  
  
 `ptr`  
 El búfer.  
  
### <a name="remarks"></a>Comentarios  
 Los dos constructores inicializan la clase base mediante una llamada a [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( **sb**), donde **sb** es el objeto almacenado de la clase [strstreambuf](../standard-library/strstreambuf-class.md). El primer constructor inicializa también **sb** mediante una llamada a [strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf). El segundo constructor inicializa la clase base de una de estas formas:  
  
-   Si `_Mode` & **ios_base::app**== 0, entonces `ptr` debe designar el primer elemento de una matriz de elementos `count` y el constructor llama a `strstreambuf`( `ptr`, `count`, `ptr`).  
  
-   De lo contrario, `ptr` debe designar el primer elemento de una matriz de elementos count que contiene una cadena de C cuyo primer elemento está designado por `ptr`, y el constructor llama a `strstreambuf`( `ptr`, `count`, `ptr` + `strlen`( `ptr`) ).  
  
## <a name="see-also"></a>Vea también  
 [iostream](../standard-library/istream-typedefs.md#iostream)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)


