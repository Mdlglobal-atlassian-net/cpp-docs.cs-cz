---
title: _expand
ms.date: 4/2/2020
api_name:
- _expand
- _o__expand
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
- _bexpand
- fexpand
- expand
- nexpand
- _fexpand
- _nexpand
- bexpand
- _expand
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
ms.openlocfilehash: 7f2a789bc5f475411808bc00a4280b7573b67cf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347561"
---
# <a name="_expand"></a>_expand

Změní velikost bloku paměti.

## <a name="syntax"></a>Syntaxe

```C
void *_expand(
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

**_expand** vrátí ukazatel void do bloku přerozdělené paměti. **_expand**, na rozdíl od **přerozdělení ,** nelze přesunout blok změnit jeho velikost. Proto pokud je k dispozici dostatek paměti pro rozšíření bloku bez jeho přesunutí, *parametr memblock* **_expand** je stejný jako vrácená hodnota.

**_expand** vrátí **hodnotu NULL,** pokud je během operace zjištěna chyba. Například pokud **_expand** slouží ke zmenšení bloku paměti, může zjistit poškození v haldě malého bloku nebo neplatný ukazatel bloku a vrátit **hodnotu NULL**.

Pokud není k dispozici dostatek paměti pro rozšíření bloku na danou velikost bez jeho přesunutí, vrátí funkce **hodnotu NULL**. **_expand** nikdy nevrátí blok rozbalený na menší velikost, než je požadováno. Pokud dojde k selhání, **errno** označuje povahu selhání. Další informace o **errno**naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Vrácená hodnota odkazuje na úložný prostor, který je zaručeně vhodně zarovnán pro uložení libovolného typu objektu. Chcete-li zkontrolovat novou velikost položky, použijte **_msize**. Chcete-li získat ukazatel na jiný typ než **void**, použijte typ přetypované na vrácenou hodnotu.

## <a name="remarks"></a>Poznámky

Funkce **_expand** změní velikost dříve přiděleného bloku paměti tím, že se pokusí rozbalit nebo zmenšit blok bez přesunutí jeho umístění v haldě. Parametr *memblock* odkazuje na začátek bloku. Parametr *size* udává novou velikost bloku v bajtech. Obsah bloku se nemění až na kratší nové a staré velikosti. *memblock* by neměl být blok, který byl uvolněn.

> [!NOTE]
> Na 64bitových platformách **nemusí _expand** uzavřít smlouvu s blokem, pokud je nová velikost menší než aktuální velikost; zejména v případě, že blok byl menší než 16 K velikosti, a proto přiděleny v haldě nízké fragmentace, **_expand** opustí blok beze změny a vrátí *memblock*.

Pokud je aplikace propojena s ladicí verzí knihoven run-time C, **_expand** překládá na [_expand_dbg](expand-dbg.md). Další informace o tom, jak haldy je spravována během procesu ladění, naleznete [v tématu HALDA ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Tato funkce ověřuje její parametry. Pokud *je memblock* nulovým ukazatelem, tato funkce vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **je chybné číslo** nastaveno na **hodnotu EINVAL** a funkce vrátí **hodnotu NULL**. Pokud je *velikost* větší než **_HEAP_MAXREQ**, je **errno** nastaveno na **ENOMEM** a funkce vrátí **hodnotu NULL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_expand**|\<malloc.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_expand.c

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   char *bufchar;
   printf( "Allocate a 512 element buffer\n" );
   if( (bufchar = (char *)calloc( 512, sizeof( char ) )) == NULL )
      exit( 1 );
   printf( "Allocated %d bytes at %Fp\n",
         _msize( bufchar ), (void *)bufchar );
   if( (bufchar = (char *)_expand( bufchar, 1024 )) == NULL )
      printf( "Can't expand" );
   else
      printf( "Expanded block to %d bytes at %Fp\n",
            _msize( bufchar ), (void *)bufchar );
   // Free memory
   free( bufchar );
   exit( 0 );
}
```

```Output
Allocate a 512 element buffer
Allocated 512 bytes at 002C12BC
Expanded block to 1024 bytes at 002C12BC
```

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[Zdarma](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
