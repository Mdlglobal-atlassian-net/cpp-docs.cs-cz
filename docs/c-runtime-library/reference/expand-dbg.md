---
title: _expand_dbg
ms.date: 11/04/2016
api_name:
- _expand_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- expand_dbg
- _expand_dbg
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
ms.openlocfilehash: 836b9cffcf0367f248a14469b30c1a355e2bdec2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941582"
---
# <a name="_expand_dbg"></a>_expand_dbg

Změní velikost zadaného bloku paměti v haldě rozšířením nebo zavoláním bloku (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void *_expand_dbg(
   void *userData,
   size_t newSize,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*userData*<br/>
Ukazatel na dříve přidělený blok paměti.

*newSize*<br/>
Požadovaná nová velikost pro blok (v bajtech).

*blockType*<br/>
Požadovaný typ pro blok s předanou velikostí: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

*Bitmap*<br/>
Ukazatel na název zdrojového souboru, který požadoval operaci Expand nebo **null**.

*číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, kde byla operace rozšíření požadována nebo **má hodnotu null**.

Parametry *filename* a *číslo řádku* jsou k dispozici pouze v případě, že byla explicitně volána metoda **_expand_dbg** nebo byla definována konstanta preprocesoru [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) .

## <a name="return-value"></a>Návratová hodnota

Po úspěšném dokončení vrátí **_expand_dbg** ukazatel na blok paměti se změněnou velikostí. Vzhledem k tomu, že paměť není přesunuta, adresa je stejná jako u uživatelských userData. Pokud došlo k chybě nebo nešlo rozšířit blok na požadovanou velikost, vrátí **hodnotu null**. Pokud dojde k selhání, **errno** má informace z operačního systému o povaze selhání. Další informace o **errno**najdete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_expand_dbg** je ladicí verze funkce _[expand](expand.md) . Pokud není definován [_DEBUG](../../c-runtime-library/debug.md) , každé volání **_expand_dbg** je sníženo na volání **_expand**. **_Expand** i **_expand_dbg** mění velikost paměti bloku v základní haldě, ale **_expand_dbg** nabízí několik funkcí ladění: vyrovnávací paměti na obou stranách bloku pro testování nevracení, parametr typu bloku ke sledování konkrétní typy přidělení a informace o *názvu souboru*/*číslo řádku* , abyste určili původ požadavků na přidělení.

**_expand_dbg** změní velikost zadaného bloku paměti o více místa, než je požadovaný *NewSize*. *NewSize* může být větší nebo menší než velikost původně přiděleného bloku paměti. Dodatečné místo se používá správcem haldy ladění k propojení bloků paměti ladění a k poskytnutí aplikace s informacemi hlavičky ladění a přepsat vyrovnávací paměti. Změna velikosti se provádí buď rozšířením, nebo zadáním původního bloku paměti. **_expand_dbg** nepřesouvá blok paměti, podobně jako funkce [_realloc_dbg](realloc-dbg.md) .

Když je *NewSize* větší než původní velikost bloku, blok paměti je rozbalený. Pokud se během rozšiřování nedá blok paměti rozšířit tak, aby odpovídal požadované velikosti, vrátí se **hodnota null** . Pokud je *NewSize* menší než původní velikost bloku, je blok paměti zadaný až do získání nové velikosti.

Informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloků přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi voláním standardní funkce haldy a její ladicí verzí v sestavení ladění aplikace najdete v tématu [ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

Tato funkce ověří své parametry. Pokud je *memblock* ukazatel s hodnotou null, nebo pokud je velikost větší než **_HEAP_MAXREQ**, tato funkce vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **hodnotu null**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_expand_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Příklad

```C
// crt_expand_dbg.c
//
// This program allocates a block of memory using _malloc_dbg
// and then calls _msize_dbg to display the size of that block.
// Next, it uses _expand_dbg to expand the amount of
// memory used by the buffer and then calls _msize_dbg again to
// display the new amount of memory allocated to the buffer.
//

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>
#include <crtdbg.h>

int main( void )
{
   long *buffer;
   size_t size;

   // Call _malloc_dbg to include the filename and line number
   // of our allocation request in the header
   buffer = (long *)_malloc_dbg( 40 * sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );
   if( buffer == NULL )
      exit( 1 );

   // Get the size of the buffer by calling _msize_dbg
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );

   // Expand the buffer using _expand_dbg and show the new size
   buffer = (long *)_expand_dbg( buffer, size + sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );

   if( buffer == NULL )
      exit( 1 );
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _expand_dbg of 1 more long: %u\n",
           size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after _malloc_dbg of 40 longs: 160
Size of block after _expand_dbg of 1 more long: 164
```

## <a name="comment"></a>Komentář

Výstup tohoto programu závisí na schopnosti vašeho počítače rozbalit všechny oddíly. Pokud jsou všechny oddíly rozbaleny, výstup se projeví v části Output.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
