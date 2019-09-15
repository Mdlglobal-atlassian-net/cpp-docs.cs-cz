---
title: realloc
ms.date: 11/04/2016
api_name:
- realloc
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
- _brealloc
- _nrealloc
- realloc
- _frealloc
helpviewer_keywords:
- _brealloc function
- realloc function
- nrealloc function
- frealloc function
- _nrealloc function
- memory blocks, reallocating
- memory, reallocating
- _frealloc function
- reallocate memory blocks
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
ms.openlocfilehash: 6197b7bca3ec9f416696e1ded8ea5ca813392616
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949502"
---
# <a name="realloc"></a>realloc

Znovu přidělit bloky paměti.

## <a name="syntax"></a>Syntaxe

```C
void *realloc(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Ukazatel na dříve přidělený blok paměti.

*hodnota*<br/>
Nová velikost v bajtech

## <a name="return-value"></a>Návratová hodnota

**realokace** vrátí ukazatel **void** na blok paměti realokace (a případně přesunuto).

Pokud není dostatek dostupné paměti pro rozšíření bloku na danou velikost, původní blok zůstane beze změny a vrátí **hodnotu null** .

Pokud je *Velikost* nulová, pak je uvolněn blok, na který odkazuje *memblock* ; Vrácená hodnota je **null**a *memblock* vlevo odkazuje na uvolněný blok.

Vrácená hodnota odkazuje na prostor úložiště, který je zaručen vhodným způsobem pro uložení libovolného typu objektu. Chcete-li získat ukazatel na jiný typ než **void**, použijte přetypování typu u vrácené hodnoty.

## <a name="remarks"></a>Poznámky

Funkce **realokace** změní velikost přiděleného bloku paměti. Argument *memblock* odkazuje na začátek bloku paměti. Pokud má Memblock **hodnotu null**, **realokace** se chová stejným **způsobem jako \** a přidělí nový blok *velikosti* bajtů. Pokud *memblock* není **null**, mělo by se jednat o ukazatel vrácený předchozím voláním metody **calloc** **, pro**nebo **realokace**.

Argument *Size* poskytuje novou velikost bloku v bajtech. Obsah bloku se nezměnil do kratšího z nových a starých velikostí, i když nový blok může být v jiném umístění. Vzhledem k tomu, že nový blok může být v novém umístění v paměti, ukazatel vrácený funkcí **realokace** není zaručen jako ukazatel předaný pomocí argumentu *memblock* . **realokace** nemá v případě růstu vyrovnávací paměti nula nově přidělené paměti.

**realokace** nastaví **errno** na **ENOMEM** , pokud se přidělení paměti nepovede nebo pokud je velikost požadované paměti větší než **_HEAP_MAXREQ**. Informace o tomto a dalších chybových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**realokace** volá **hodnotu** _set_new_mode, aby bylo možné C++ použít funkci [](set-new-mode.md) k nastavení nového režimu obslužné rutiny. Nový režim obslužné rutiny **označuje, zda je při** selhání zavolána nová rutina obslužné rutiny nastavenou na [_set_new_handler](set-new-handler.md). Ve výchozím nastavení nevolá hodnota \ nevolá novou rutinu obslužné rutiny při selhání přidělení paměti. Toto výchozí chování můžete přepsat tak, **aby při opětovném přidělení paměti** nebylo volání nové obslužné rutiny nové rutiny obslužné rutiny stejným způsobem jako operátor **New** **, když** dojde k chybě ze stejného důvodu. Chcete-li přepsat výchozí hodnotu, zavolejte

```C
_set_new_mode(1);
```

nejdříve v programu nebo se připojte pomocí NEWMODE. OBJ (viz [možnosti propojení](../../c-runtime-library/link-options.md)).

Pokud je aplikace propojena s ladicí verzí knihoven jazyka C Runtime, **realokace** se přeloží na [_realloc_dbg](realloc-dbg.md). Další informace o tom, jak je halda spravována během procesu ladění, naleznete v [haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

**realokace** je označena `__declspec(restrict)`jako `__declspec(noalias)` , což znamená, že funkce zaručuje, že nemění globální proměnné a že ukazatel, který vrátil, nemá alias. Další informace najdete [v tématech a](../../cpp/noalias.md) [omezení](../../cpp/restrict.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**realloc**|\<Stdlib. h > a \<. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_realloc.c
// This program allocates a block of memory for
// buffer and then uses _msize to display the size of that
// block. Next, it uses realloc to expand the amount of
// memory used by buffer and then calls _msize again to
// display the new amount of memory allocated to buffer.

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   long *buffer, *oldbuffer;
   size_t size;

   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )
      exit( 1 );

   size = _msize( buffer );
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );

   // Reallocate and show new size:
   oldbuffer = buffer;     // save pointer in case realloc fails
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))
        ==  NULL )
   {
      free( oldbuffer );  // free original block
      exit( 1 );
   }
   size = _msize( buffer );
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",
            size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after malloc of 1000 longs: 4000
Size of block after realloc of 1000 more longs: 8000
```

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
