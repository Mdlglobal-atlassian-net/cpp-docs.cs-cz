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
ms.openlocfilehash: 65b74798c4b3b513acea0b51ecc0cb7df98391c1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944310"
---
# <a name="_heapset"></a>_heapset

Kontroluje haldy pro minimální konzistenci a nastavuje bezplatné položky na zadanou hodnotu.

> [!IMPORTANT]
>  Tato funkce je zastaralá. Počínaje verzí Visual Studio 2015 není k dispozici v CRT.

## <a name="syntax"></a>Syntaxe

```
int _heapset(
   unsigned int fill
);
```

#### <a name="parameters"></a>Parametry

*vyplnění*<br/>
Znak Fill.

## <a name="return-value"></a>Návratová hodnota

`_heapset`Vrátí jednu z následujících celočíselných konstant manifestu definovaných ve typu. h.

|||
|-|-|
| `_HEAPBADBEGIN`  | Informace počáteční hlavičky jsou neplatné nebo se nenašly.  |
| `_HEAPBADNODE`  | Byl nalezen poškozený nebo chybný uzel haldy.  |
| `_HEAPEMPTY`  | Halda není inicializovaná.  |
| `_HEAPOK`  | Halda se jeví jako konzistentní.  |

Kromě toho, pokud dojde k chybě, `_heapset` nastaví `errno` na `ENOSYS`.

## <a name="remarks"></a>Poznámky

`_heapset` Funkce zobrazuje volná umístění paměti nebo uzly, které byly neúmyslně přepsány.

`_heapset`kontroluje minimální konzistenci haldy a pak nastaví každý bajt bezplatných záznamů haldy na `fill` hodnotu. Tato známá hodnota ukazuje, která paměťová umístění haldy obsahují volné uzly a která obsahují data, která nebyla záměrně zapsána do uvolněné paměti. Pokud operační systém `_heapset`nepodporuje (například Windows 98), vrátí `_HEAPOK` funkce a nastaví `errno` na `ENOSYS`.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|`_heapset`|\<. h >|\<errno.h>|

Další informace o kompatibilitě naleznete v úvodu v tématu [Kompatibilita](../c-runtime-library/compatibility.md) .

## <a name="example"></a>Příklad

```
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

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../c-runtime-library/heapadd.md)<br/>
[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapmin](../c-runtime-library/reference/heapmin.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)
