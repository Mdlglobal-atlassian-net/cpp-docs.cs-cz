---
title: realloc
ms.date: 4/2/2020
api_name:
- realloc
- _o_realloc
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 964c465a95d44de9d8a4d399f23ec43f8a3a6692
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332936"
---
# <a name="realloc"></a>realloc

Přerozdělit bloky paměti.

## <a name="syntax"></a>Syntaxe

```C
void *realloc(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*memblok*<br/>
Ukazatel na dříve přidělený blok paměti.

*Velikost*<br/>
Nová velikost v bajtů.

## <a name="return-value"></a>Návratová hodnota

**funkce přerozdělovací položky** vrátí ukazatel **void** na přerozdělený (a případně přesunutý) blok paměti.

Pokud není k dispozici dostatek paměti pro rozšíření bloku na danou velikost, původní blok zůstane beze změny **a** null je vrácena.

Pokud je *velikost* nulová, je blok, na který ukazuje *memblock,* uvolněn; vrácená hodnota je **NULL**a *memblock* je ponechán a směřující na uvolněný blok.

Vrácená hodnota odkazuje na úložný prostor, který je zaručeně vhodně zarovnán pro uložení libovolného typu objektu. Chcete-li získat ukazatel na jiný typ než **void**, použijte typ přetypované na vrácenou hodnotu.

## <a name="remarks"></a>Poznámky

Funkce **reloc** změní velikost přiděleného bloku paměti. Argument *memblock* odkazuje na začátek bloku paměti. Pokud *memblock* je **NULL**, **realloc** chová stejným způsobem jako **malloc** a přiděluje nový blok *velikosti* bajtů. Pokud *memblock* není **NULL**, by měl být ukazatel vrácena předchozí volání **calloc**, **malloc**, nebo **reloc**.

Argument *velikost* i dává novou velikost bloku v bajtů. Obsah bloku se nemění až na kratší nové a staré velikosti, i když nový blok může být v jiném umístění. Vzhledem k tomu, že nový blok může být v novém umístění paměti, ukazatel vrácený **realloc** není zaručeno, že ukazatel prošel *memblock* argument. **přerozdělované** není nula nově přidělené paměti v případě růstu vyrovnávací paměti.

**přecenění** nastaví **errno** na **ENOMEM,** pokud se nezdaří přidělení paměti nebo pokud požadované množství paměti překročí **_HEAP_MAXREQ**. Informace o tomto a dalších kódech chyb naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**funkce realloc** volá **malloc,** aby bylo možné použít funkci [c++ _set_new_mode](set-new-mode.md) k nastavení nového režimu obslužné rutiny. Nový režim obslužné rutiny označuje, zda při selhání **malloc** volá novou rutinu obslužné rutiny nastavenou [_set_new_handler](set-new-handler.md). Ve výchozím nastavení **malloc** nevolá novou rutinu obslužné rutiny při selhání přidělení paměti. Můžete přepsat toto výchozí chování tak, že při **realloc** se nezdaří přidělit paměť, **malloc** volá rutiny nové obslužné rutiny stejným způsobem, že **nový** operátor dělá, když se nezdaří ze stejného důvodu. Chcete-li přepsat výchozí,

```C
_set_new_mode(1);
```

brzy v nich programu, nebo odkaz s NEWMODE. OBJ (viz [Možnosti odkazu](../../c-runtime-library/link-options.md)).

Pokud je aplikace propojena s ladicí verzí knihoven c run-time, **překládá funkce realloc** na [_realloc_dbg](realloc-dbg.md). Další informace o tom, jak haldy je spravována během procesu ladění, naleznete [v tématu HALDA ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

**přerozdělování** `__declspec(noalias)` je `__declspec(restrict)`označeno a , což znamená, že je zaručeno, že funkce nebude měnit globální proměnné a že vrácený ukazatel není aliasován. Další informace naleznete v [tématu noalias](../../cpp/noalias.md) a [restrict](../../cpp/restrict.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**realloc**|\<stdlib.h> \<a malloc.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[Zdarma](free.md)<br/>
[malloc](malloc.md)<br/>
