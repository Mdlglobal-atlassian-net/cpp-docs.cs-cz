---
title: _heapset
ms.date: 11/04/2016
api_name:
- _heapset
api_location:
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _heapset
- heapset
helpviewer_keywords:
- checking heap
- heapset function
- heaps, checking
- debugging [CRT], heap-related problems
- _heapset function
ms.assetid: 9667eeb0-55bc-4c19-af5f-d1fd0a142b3c
ms.openlocfilehash: 2a0aea37237f04939579eb059a42dd33771339ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351276"
---
# <a name="_heapset"></a>_heapset

Zkontroluje hromady pro minimální konzistenci a nastaví volné položky na zadanou hodnotu.

> [!IMPORTANT]
> Tato funkce je zastaralá. Počínaje Visual Studio 2015, není k dispozici v CRT.

## <a name="syntax"></a>Syntaxe

```
int _heapset(
   unsigned int fill
);
```

#### <a name="parameters"></a>Parametry

*fill*<br/>
Vyplnit znak.

## <a name="return-value"></a>Návratová hodnota

`_heapset`vrátí jednu z následujících konstant manifestu celého čísla definované v souboru Malloc.h.

|||
|-|-|
| `_HEAPBADBEGIN`  | Počáteční informace záhlaví jsou neplatné nebo nebyly nalezeny.  |
| `_HEAPBADNODE`  | Byla nalezena halda poškozená nebo chybná uzla.  |
| `_HEAPEMPTY`  | Halda není inicializována.  |
| `_HEAPOK`  | Halda se zdá být konzistentní.  |

Kromě toho, pokud dojde `_heapset` k `errno` `ENOSYS`chybě, nastaví na .

## <a name="remarks"></a>Poznámky

Funkce `_heapset` zobrazuje umístění volné paměti nebo uzly, které byly neúmyslně přepsány.

`_heapset`zkontroluje minimální konzistenci na haldě a potom nastaví každý bajt volné položky haldy na hodnotu. `fill` Tato známá hodnota ukazuje, která umístění paměti haldy obsahují volné uzly a která obsahují data, která byla neúmyslně zapsána do uvolněné paměti. Pokud operační systém `_heapset`nepodporuje (například Windows 98), `_HEAPOK` funkce `errno` `ENOSYS`se vrátí a nastaví na .

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|`_heapset`|\<malloc.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../c-runtime-library/compatibility.md) v úvodu.

## <a name="example"></a>Příklad

```c
// crt_heapset.c
// This program checks the heap and
// fills in free entries with the character 'Z'.

#include <malloc.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int heapstatus;
   char *buffer;

   if( (buffer = malloc( 1 )) == NULL ) // Make sure heap is
      exit( 0 );                        //    initialized
   heapstatus = _heapset( 'Z' );        // Fill in free entries
   switch( heapstatus )
   {
   case _HEAPOK:
      printf( "OK - heap is fine\n" );
      break;
   case _HEAPEMPTY:
      printf( "OK - heap is empty\n" );
      break;
   case _HEAPBADBEGIN:
      printf( "ERROR - bad start of heap\n" );
      break;
   case _HEAPBADNODE:
      printf( "ERROR - bad node in heap\n" );
      break;
   }
   free( buffer );
}
```

```Output
OK - heap is fine
```

## <a name="see-also"></a>Viz také

[Přidělení paměti](../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../c-runtime-library/heapadd.md)<br/>
[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapmin](../c-runtime-library/reference/heapmin.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)
