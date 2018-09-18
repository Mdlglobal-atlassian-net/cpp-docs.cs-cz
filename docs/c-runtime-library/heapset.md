---
title: _heapset – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _heapset
apilocation:
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _heapset
- heapset
dev_langs:
- C++
helpviewer_keywords:
- checking heap
- heapset function
- heaps, checking
- debugging [CRT], heap-related problems
- _heapset function
ms.assetid: 9667eeb0-55bc-4c19-af5f-d1fd0a142b3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b9700ce3f003488ba394302ac011937ea116a90
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085209"
---
# <a name="heapset"></a>_heapset

Kontroluje haldy pro minimální konzistence a nastaví volné položky na zadanou hodnotu.

> [!IMPORTANT]
>  Tato funkce je zastaralá. Od v sadě Visual Studio 2015, není k dispozici v CRT.

## <a name="syntax"></a>Syntaxe

```
int _heapset(
   unsigned int fill
);
```

#### <a name="parameters"></a>Parametry

*Výplň*<br/>
Zadejte znak.

## <a name="return-value"></a>Návratová hodnota

`_heapset` Vrátí jeden z následující celých čísel konstant manifestu definovaných v Malloc.h.

|||
|-|-|
| `_HEAPBADBEGIN`  | Počáteční informace hlavičky jsou neplatné nebo nebyly nalezeny.  |
| `_HEAPBADNODE`  | Haldy poškozený nebo nalezený špatný uzel.  |
| `_HEAPEMPTY`  | Halda neinicializována.  |
| `_HEAPOK`  | Haldy se zdá být konzistentní vzhledem k aplikacím.  |

Kromě toho, pokud dojde k chybě `_heapset` nastaví `errno` k `ENOSYS`.

## <a name="remarks"></a>Poznámky

`_heapset` Funkce zobrazuje umístění volné paměti nebo uzly, které byly neúmyslně přepsána.

`_heapset` kontroluje minimální konzistence na haldě a pak nastaví všech bajtů haldy bezplatné položky `fill` hodnotu. Tato známá hodnota zobrazí umístění paměti haldy obsahovat uzly úrovně free a které obsahují data, která se neúmyslně zapsána do uvolněné paměti. Pokud operační systém nepodporuje `_heapset`(například Windows 98), funkce vrátí `_HEAPOK` a nastaví `errno` k `ENOSYS`.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|`_heapset`|\<malloc.h >|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../c-runtime-library/compatibility.md) v úvodu.

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

## <a name="see-also"></a>Viz také

[Přidělení paměti](../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../c-runtime-library/heapadd.md)<br/>
[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapmin](../c-runtime-library/reference/heapmin.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)