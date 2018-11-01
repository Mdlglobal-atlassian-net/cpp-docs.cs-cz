---
title: realloc
ms.date: 11/04/2016
apiname:
- realloc
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 0d61746365a8ded8d68072b1f398a18ba6ce7605
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544960"
---
# <a name="realloc"></a>realloc

Změnit přidělení bloků paměti.

## <a name="syntax"></a>Syntaxe

```C
void *realloc(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Ukazatele na blok paměti dříve přidělené.

*Velikost*<br/>
Nová velikost v bajtech.

## <a name="return-value"></a>Návratová hodnota

**realloc** vrátí **void** ukazatele na blok paměti a nevyčerpané prostředky se (může být přesunutý).

Pokud není k dispozici dostatek paměti a rozbalte na danou velikost bloku, původního bloku je vlevo beze změny, a **NULL** je vrácena.

Pokud *velikost* nula, je blok odkazovaný parametrem *memblock* je uvolněn; vrácená hodnota je **NULL**, a *memblock* zbývá odkazující na uvolnění bloku.

Návratová hodnota odkazuje na prostor úložiště, která je zaručeně jako vhodně zarovnaný pro úložiště libovolného typu objektu. Získání ukazatele na typ jiný než **void**, použijte přetypování typu na návratovou hodnotu.

## <a name="remarks"></a>Poznámky

**Realloc** funkce změní velikost přidělené paměti bloku. *Memblock* argument odkazuje na začátku bloku paměti. Pokud *memblock* je **NULL**, **realloc** se chová stejně jako **malloc** a přiděluje nový blok *velikost*bajtů. Pokud *memblock* není **NULL**, měla by být ukazatel vrácený z předchozího volání **calloc**, **malloc**, nebo **realloc** .

*Velikost* argument poskytuje novou velikost bloku, v bajtech. Obsah bloku jsou až po kratší velikostí novém i starém beze změny i nový blok může být v jiném umístění. Vzhledem k tomu, že nový blok může být nové umístění paměti, vrácený ukazatel **realloc** nemusí být předány prostřednictvím ukazatele *memblock* argument. **realloc** nemá nulovou nově přidělenou paměť v případě růstu vyrovnávací paměti.

**realloc** nastaví **errno** k **ENOMEM** Pokud selhání přidělení paměti, nebo pokud požadované množství paměti překročí **_heap_maxreq –**. Informace o tomto a dalších chybových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**realloc** volání **malloc** Chcete-li použít C++ [_set_new_mode](set-new-mode.md) funkce nastavíte nový režim obslužné rutiny. Nový režim obslužné rutiny Určuje, zda je při selhání, **malloc** je volat nové rutiny obsluhy úmluvu [_set_new_handler](set-new-handler.md). Ve výchozím nastavení **malloc** nevolá nové rutiny obsluhy při selhání přidělení paměti. Toto výchozí chování můžete přepsat tak, aby, když **realloc** selže přidělování paměti, **malloc** volá nové rutiny obsluhy ve stejném způsobu, jakým **nové** operátor Když selže ze stejného důvodu. Chcete-li přepsat výchozí hodnotu, zavolejte

```C
_set_new_mode(1);
```

zpočátku v těch, které jsou programu nebo propojení s knihovnou NEWMODE. OBJ (viz [možnosti propojení](../../c-runtime-library/link-options.md)).

Když je aplikace spojena s ladicí verzí knihovny run-time C **realloc** přeloží na [_realloc_dbg –](realloc-dbg.md). Další informace o tom, jak je spravována halda během procesu ladění, naleznete v tématu [haldy pro ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

**realloc** je označen `__declspec(noalias)` a `__declspec(restrict)`, což znamená, že funkce je zaručeno, že neupraví globální proměnné a Vrácený ukazatel není alias. Další informace najdete v tématu [noalias](../../cpp/noalias.md) a [omezit](../../cpp/restrict.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**realloc**|\<stdlib.h > a \<malloc.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
