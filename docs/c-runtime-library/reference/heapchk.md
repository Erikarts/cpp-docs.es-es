---
title: _heapchk
ms.date: 4/2/2020
api_name:
- _heapchk
- _o__heapchk
api_location:
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _heapchk
- heapchk
helpviewer_keywords:
- debugging [CRT], heap-related problems
- consistency checking of heaps
- heapchk function
- heaps, checking consistency
- _heapchk function
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
ms.openlocfilehash: 2ddbdaec5861d48cc23a7cbcd28332e8c06ebbfe
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916213"
---
# <a name="_heapchk"></a>_heapchk

Ejecuta comprobaciones de coherencia en el montón.

## <a name="syntax"></a>Sintaxis

```C
int _heapchk( void );
```

## <a name="return-value"></a>Valor devuelto

**_heapchk** devuelve una de las siguientes constantes de manifiesto Integer definidas en malloc. h.

|Valor devuelto|Condición|
|-|-|
| **_HEAPBADBEGIN** | La información del encabezado inicial es incorrecta o no se ha encontrado. |
| **_HEAPBADNODE** | Se ha encontrado un nodo incorrecto o el montón está dañado. |
| **_HEAPBADPTR** | El puntero al montón no es válido. |
| **_HEAPEMPTY** | No se ha inicializado el montón. |
| **_HEAPOK** | El montón parece ser coherente. |

Además, si se produce un error, **_heapchk** establece **errno** en **ENOSYS**.

## <a name="remarks"></a>Observaciones

La función **_heapchk** ayuda a depurar los problemas relacionados con el montón comprobando la coherencia mínima del montón. Si el sistema operativo no admite **_heapchk**(por ejemplo, Windows 98), la función devuelve **_HEAPOK** y establece **errno** en **ENOSYS**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_heapchk**|\<malloc.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_heapchk.c
// This program checks the heap for
// consistency and prints an appropriate message.

#include <malloc.h>
#include <stdio.h>

int main( void )
{
   int  heapstatus;
   char *buffer;

   // Allocate and deallocate some memory
   if( (buffer = (char *)malloc( 100 )) != NULL )
      free( buffer );

   // Check heap status
   heapstatus = _heapchk();
   switch( heapstatus )
   {
   case _HEAPOK:
      printf(" OK - heap is fine\n" );
      break;
   case _HEAPEMPTY:
      printf(" OK - heap is empty\n" );
      break;
   case _HEAPBADBEGIN:
      printf( "ERROR - bad start of heap\n" );
      break;
   case _HEAPBADNODE:
      printf( "ERROR - bad node in heap\n" );
      break;
   }
}
```

```Output
OK - heap is fine
```

## <a name="see-also"></a>Consulte también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
[_heapwalk](heapwalk.md)<br/>
