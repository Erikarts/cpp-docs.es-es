---
title: mbsrtowcs
ms.date: 11/04/2016
apiname:
- mbsrtowcs
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: 2bc0c8c9e2d871b6d1748c42dc02c627244dbf69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331147"
---
# <a name="mbsrtowcs"></a>mbsrtowcs

Convierte una cadena de caracteres multibyte en la configuración regional actual en una cadena de caracteres anchos correspondiente, con la capacidad de reinicio en medio de un carácter multibyte. Hay disponible una versión más segura de esta función; vea [mbsrtowcs_s](mbsrtowcs-s.md).

## <a name="syntax"></a>Sintaxis

```C
size_t mbsrtowcs(
   wchar_t *wcstr,
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t mbsrtowcs(
   wchar_t (&wcstr)[size],
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parámetros

*wcstr*<br/>
Dirección para almacenar la cadena de caracteres anchos convertida.

*mbstr*<br/>
Puntero indirecto a la ubicación de la cadena de caracteres multibyte a convertir.

*count*<br/>
El número máximo de caracteres (no bytes) para convertir y almacenar en *wcstr*.

*mbstate*<br/>
Un puntero a un **mbstate_t** objeto de estado de conversión. Si este valor es un puntero nulo, se utiliza un objeto de estado de la conversión interno estático. Dado que la interna **mbstate_t** objeto no es seguro para subprocesos, se recomienda pasar siempre su propio *mbstate* parámetro.

## <a name="return-value"></a>Valor devuelto

Devuelve el número de caracteres convertidos correctamente, sin incluir el carácter nulo de terminación, de haberlo. Devuelve (size_t)(-1) si se ha producido un error y establece **errno** a EILSEQ.

## <a name="remarks"></a>Comentarios

El **mbsrtowcs** función convierte una cadena de caracteres multibyte indirectamente señalada por *mbstr*, en caracteres anchos almacenados en el búfer señalado por *wcstr*, por con el estado de conversión contenido en *mbstate*. La conversión continúa para cada carácter hasta que se encuentra ya sea un carácter nulo de terminación multibyte, se encuentra una secuencia multibyte que no corresponde a un carácter válido en la configuración regional actual, o hasta que *recuento* caracteres se han convertido. Si **mbsrtowcs** encuentra el carácter multibyte nulo ('\0') antes o al *recuento* se produce, convierte en un carácter nulo final de 16 bits y se detiene.

Por lo tanto, la cadena de caracteres anchos en *wcstr* está terminada en null solo si **mbsrtowcs** encuentra un carácter multibyte nulo durante la conversión. Si las secuencias señaladas por *mbstr* y *wcstr* se superponen, el comportamiento de **mbsrtowcs** es indefinido. **mbsrtowcs** se ve afectado por la categoría LC_TYPE de la configuración regional actual.

El **mbsrtowcs** función difiere de [mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md) por su capacidad de reinicio. El estado de conversión se almacena en *mbstate* en las llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables.  Por ejemplo, una aplicación debe utilizar **mbsrlen** en lugar de **mbslen**, si una llamada subsiguiente a **mbsrtowcs** se utiliza en lugar de **mbstowcs**.

Si *wcstr* no es un puntero nulo, el objeto de puntero apunta a *mbstr* se asigna un puntero nulo si la conversión se detuvo porque se alcanzó un carácter nulo de terminación. De lo contrario, se le asigna la dirección inmediatamente posterior al último carácter multibyte convertido, de haberlo. Esto permite que una llamada de función subsiguiente reinicie la conversión en el punto en que se detuvo esta llamada.

Si el *wcstr* argumento es un puntero nulo, el *recuento* argumento se omite y **mbsrtowcs** devuelve el tamaño necesario en caracteres anchos de la cadena de destino. Si *mbstate* es un puntero nulo, la función usa estático interno que no es segura para subprocesos **mbstate_t** objeto de estado de conversión. Si la secuencia de caracteres *mbstr* no tiene un multibyte correspondiente representación de caracteres, se devuelve -1 y el **errno** está establecido en **EILSEQ**.

Si *mbstr* se invoca un puntero nulo, el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** a **EINVAL** y devuelve -1.

En C++, esta función tiene una sobrecarga de plantilla que invoca una contrapartida más nueva y segura de la función. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Excepciones

El **mbsrtowcs** función es segura para subprocesos siempre y cuando ninguna función en el subproceso actual llame a **setlocale** siempre y cuando se ejecuta esta función y el *mbstate* argumento no es un puntero nulo.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**mbsrtowcs**|\<wchar.h>|

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
