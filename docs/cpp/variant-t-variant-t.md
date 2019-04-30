---
title: _variant_t::_variant_t
ms.date: 11/04/2016
f1_keywords:
- _variant_t::_variant_t
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
ms.openlocfilehash: b3575226199c15c4a9796fb439f65efb5a539225
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403287"
---
# <a name="varianttvariantt"></a>_variant_t::_variant_t

**Específicos de Microsoft**

Construye un objeto `_variant_t`.

## <a name="syntax"></a>Sintaxis

```
_variant_t( ) throw( );

_variant_t(
   const VARIANT& varSrc
);

_variant_t(
   const VARIANT* pVarSrc
);

_variant_t(
   const _variant_t& var_t_Src
);

_variant_t(
   VARIANT& varSrc,
   bool fCopy
);

_variant_t(
   short sSrc,
   VARTYPE vtSrc = VT_I2
);

_variant_t(
   long lSrc,
   VARTYPE vtSrc = VT_I4
);

_variant_t(
   float fltSrc
) throw( );

_variant_t(
   double dblSrc,
   VARTYPE vtSrc = VT_R8
);

_variant_t(
   const CY& cySrc
) throw( );

_variant_t(
   const _bstr_t& bstrSrc
);

_variant_t(
   const wchar_t *wstrSrc
);

_variant_t(
   const char* strSrc
);

_variant_t(
   IDispatch* pDispSrc,
   bool fAddRef = true
) throw( );

_variant_t(
   bool bSrc
) throw( );

_variant_t(
   IUnknown* pIUknownSrc,
   bool fAddRef = true
) throw( );

_variant_t(
   const DECIMAL& decSrc
) throw( );

_variant_t(
   BYTE bSrc
) throw( );

variant_t(
   char cSrc
) throw();

_variant_t(
   unsigned short usSrc
) throw();

_variant_t(
   unsigned long ulSrc
) throw();

_variant_t(
   int iSrc
) throw();

_variant_t(
   unsigned int uiSrc
) throw();

_variant_t(
   __int64 i8Src
) throw();

_variant_t(
   unsigned __int64 ui8Src
) throw();
```

#### <a name="parameters"></a>Parámetros

*varSrc*<br/>
Un objeto `VARIANT` que se va a copiar en el nuevo objeto `_variant_t`.

*pVarSrc*<br/>
Puntero a un `VARIANT` objeto que se copiará en el nuevo `_variant_t` objeto.

*var_t_Src*<br/>
Un objeto `_variant_t` que se va a copiar en el nuevo objeto `_variant_t`.

*fCopy*<br/>
Si **false**, proporcionado `VARIANT` objeto está asociado a la nueva `_variant_t` objeto sin crear una nueva copia por `VariantCopy`.

*ISrc, sSrc*<br/>
Un valor entero que se va a copiar en el nuevo objeto `_variant_t`.

*vtSrc*<br/>
El `VARTYPE` para el nuevo `_variant_t` objeto.

*fltSrc, dblSrc*<br/>
Un valor numérico que se va a copiar en el nuevo objeto `_variant_t`.

*cySrc*<br/>
Un objeto `CY` que se va a copiar en el nuevo objeto `_variant_t`.

*bstrSrc*<br/>
Un objeto `_bstr_t` que se va a copiar en el nuevo objeto `_variant_t`.

*strSrc, wstrSrc*<br/>
Una cadena que se va a copiar en el nuevo objeto `_variant_t`.

*bSrc*<br/>
Un **bool** valor que se copiará en el nuevo `_variant_t` objeto.

*pIUknownSrc*<br/>
Puntero de interfaz COM a un objeto VT_UNKNOWN que va a encapsular en el nuevo `_variant_t` objeto.

*pDispSrc*<br/>
Puntero de interfaz COM a un objeto VT_DISPATCH que va a encapsular en el nuevo `_variant_t` objeto.

*decSrc*<br/>
Un valor `DECIMAL` que se va a copiar en el nuevo objeto `_variant_t`.

*bSrc*<br/>
Un valor `BYTE` que se va a copiar en el nuevo objeto `_variant_t`.

*cSrc*<br/>
Un **char** valor que se copiará en el nuevo `_variant_t` objeto.

*usSrc*<br/>
Un **entero corto sin signo** valor que se copiará en el nuevo `_variant_t` objeto.

*ulSrc*<br/>
Un **unsigned long** valor que se copiará en el nuevo `_variant_t` objeto.

*iSrc*<br/>
Un **int** valor que se copiará en el nuevo `_variant_t` objeto.

*uiSrc*<br/>
Un **int sin signo** valor que se copiará en el nuevo `_variant_t` objeto.

*i8Src*<br/>
Un **__int64** valor que se copiará en el nuevo `_variant_t` objeto.

*ui8Src*<br/>
Un **__int64 sin signo** valor que se copiará en el nuevo `_variant_t` objeto.

## <a name="remarks"></a>Comentarios

- **_variant_t ()** construye vacío `_variant_t` objeto, `VT_EMPTY`.

- **_variant_t (VARIANT &***varSrc***)** construye un `_variant_t` objeto desde una copia de la `VARIANT` objeto.     El tipo variant se conserva.

- **_variant_t (VARIANT**<strong>\*</strong>*pVarSrc***)** construye un `_variant_t` objeto desde una copia de la `VARIANT` objeto.     El tipo variant se conserva.

- **_variant_t (_variant_t &***var_t_Src***)** construye un `_variant_t` objeto desde otro `_variant_t` objeto.     El tipo variant se conserva.

- **_variant_t (VARIANT &***varSrc* **, bool**`fCopy`**)** construye un `_variant_t` objeto a partir de una máquina `VARIANT` objeto.       Si *fCopy* es **false**, **VARIANT** objeto se adjunta al nuevo objeto sin crear una copia.

- **_variant_t (short***sSrc* **, VARTYPE**`vtSrc`**= VT_I2)** construye un `_variant_t` objeto de tipo VT_I2 o VT_BOOL desde un **corto** valor entero.       Cualquier otro `VARTYPE` produce un error E_INVALIDARG.

- **_variant_t (long** `lSrc` **, VARTYPE**`vtSrc`**= VT_I4)** construye un `_variant_t` objeto de tipo VT_I4, VT_BOOL o VT_ERROR desde un **largo**  valor entero.       Cualquier otro `VARTYPE` produce un error E_INVALIDARG.

- **_variant_t (float**`fltSrc`**)** construye un `_variant_t` objeto de tipo VT_R4 desde un **float** valor numérico.    

- **_variant_t (double** `dblSrc` **, VARTYPE**`vtSrc`**= VT_R8)** construye un `_variant_t` objeto de tipo VT_R8 o VT_DATE de un **doble** valor numérico.       Cualquier otro `VARTYPE` produce un error E_INVALIDARG.

- **_variant_t (CY &**`cySrc`**)** construye un `_variant_t` objeto de tipo VT_CY desde un `CY` objeto.    

- **_variant_t (_bstr_t &**`bstrSrc`**)** construye un `_variant_t` objeto de tipo VT_BSTR desde un `_bstr_t` objeto.     Se asigna un nuevo `BSTR`.

- **_variant_t (wchar_t** <strong>\*</strong> *wstrSrc***)** construye un `_variant_t` objeto de tipo VT_BSTR desde una cadena Unicode.   Se asigna un nuevo `BSTR`.

- **_variant_t (char**<strong>\*</strong>`strSrc`**)** construye un `_variant_t` objeto de tipo VT_BSTR desde una cadena.     Se asigna un nuevo `BSTR`.

- **_variant_t (bool**`bSrc`**)** construye un `_variant_t` objeto de tipo VT_BOOL desde un **bool** valor.    

- **_variant_t (IUnknown** <strong>\*</strong> `pIUknownSrc` **, bool**`fAddRef`**= true)** construye un `_variant_t` objeto de tipo VT_UNKNOWN desde un puntero de interfaz COM.       Si `fAddRef` es **true**, a continuación, `AddRef` se llama en el puntero de interfaz proporcionado para que coincida con la llamada a `Release` que se producirá cuando el `_variant_t` se destruye el objeto. Es decisión suya llamar a `Release` en el puntero de interfaz proporcionado. Si `fAddRef` es **false**, este constructor toma la propiedad del puntero de interfaz proporcionado; no llame a `Release` en el puntero de interfaz proporcionado.

- **_variant_t (IDispatch** <strong>\*</strong> `pDispSrc` **, bool**`fAddRef`**= true)** construye un `_variant_t` objeto de VT_DISPATCH un tipo de puntero de interfaz COM.       Si `fAddRef` es **true**, a continuación, `AddRef` se llama en el puntero de interfaz proporcionado para que coincida con la llamada a `Release` que se producirá cuando el `_variant_t` se destruye el objeto. Es decisión suya llamar a `Release` en el puntero de interfaz proporcionado. Si `fAddRef` es **false**, este constructor toma la propiedad del puntero de interfaz proporcionado; no llame a `Release` en el puntero de interfaz proporcionado.

- **_variant_t (DECIMAL &**`decSrc`**)** construye un `_variant_t` objeto de tipo VT_DECIMAL desde un `DECIMAL` valor.    

- **_variant_t (BYTE**`bSrc`**)** construye un `_variant_t` objeto de tipo `VT_UI1` desde un `BYTE` valor.    

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_variant_t (Clase)](../cpp/variant-t-class.md)