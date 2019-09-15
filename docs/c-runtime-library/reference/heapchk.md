---
title: _heapchk
ms.date: 11/04/2016
api_name:
- _heapchk
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
ms.openlocfilehash: 857feb66d89d5dc406042478156483ecb86a2474
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954813"
---
# <a name="_heapchk"></a>_heapchk

Spustí kontroly konzistence na haldě.

## <a name="syntax"></a>Syntaxe

```C
int _heapchk( void );
```

## <a name="return-value"></a>Návratová hodnota

**_heapchk** vrátí jednu z následujících celočíselných konstant manifestu definovaných ve typu. h.

|Návratová hodnota|Podmínka|
|-|-|
| **_HEAPBADBEGIN** | Počáteční informace hlavičky jsou chybné nebo se nenašly. |
| **_HEAPBADNODE** | Byl nalezen špatný uzel nebo je poškozena halda. |
| **_HEAPBADPTR** | Ukazatel na haldu není platný. |
| **_HEAPEMPTY** | Halda nebyla inicializována. |
| **_HEAPOK** | Halda se jeví jako konzistentní. |

Kromě toho, pokud dojde k chybě, **_heapchk** nastaví **errno** na **ENOSYS**.

## <a name="remarks"></a>Poznámky

Funkce **_heapchk** pomáhá ladit problémy související s haldou, a to kontrolou minimální konzistence haldy. Pokud operační systém nepodporuje **_heapchk**(například Windows 98), funkce vrátí **_HEAPOK** a nastaví **errno** na **ENOSYS**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_heapchk**|\<. h >|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

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

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
[_heapwalk](heapwalk.md)<br/>
