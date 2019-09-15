---
title: _aligned_malloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_malloc_dbg
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
- _aligned_malloc_dbg
- aligned_malloc_dbg
helpviewer_keywords:
- aligned_malloc_dbg function
- _aligned_malloc_dbg function
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
ms.openlocfilehash: 3db61d494ea94c9ccbf2844c9f47df66dad87ff7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939886"
---
# <a name="_aligned_malloc_dbg"></a>_aligned_malloc_dbg

Přidělí paměť v zadaném hranici zarovnání s dodatečným prostorem pro hlavičku ladění a přepíše vyrovnávací paměti (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_malloc_dbg(
    size_t size,
    size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
Velikost požadované alokace paměti

*bod*<br/>
Hodnota zarovnání, která musí být celočíselnou mocninou 2.

*Bitmap*<br/>
Ukazatel na název zdrojového souboru, který požadoval operaci přidělení, nebo hodnotu NULL.

*číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, kde byla požadována operace přidělení, nebo hodnota NULL.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na blok paměti, který byl přidělen nebo NULL v případě, že operace se nezdařila.

## <a name="remarks"></a>Poznámky

**_aligned_malloc_dbg** je ladicí verze funkce [_aligned_malloc](aligned-malloc.md) . Pokud není definován [_DEBUG](../../c-runtime-library/debug.md) , každé volání **_aligned_malloc_dbg** je sníženo na volání `_aligned_malloc`. Oba `_aligned_malloc` i **_aligned_malloc_dbg** přidělují blok paměti v základní haldě, ale **_aligned_malloc_dbg** nabízí několik funkcí ladění: vyrovnávací paměti na obou stranách bloku pro testování nevracení a *název souboru* číslo řádku informace k určení původu žádostí o přidělení. / Sledování specifických typů přidělení s parametrem typu bloku není podporovanou funkcí ladění pro zarovnávání přidělení. Zarovnaná přidělení se zobrazí jako typ bloku _NORMAL_BLOCK.

**_aligned_malloc_dbg** přiděluje blok paměti o něco více místa, než je požadovaná *Velikost*. Dodatečné místo se používá správcem haldy ladění k propojení bloků paměti ladění a k poskytnutí aplikace s informacemi hlavičky ladění a přepsat vyrovnávací paměti. Po přidělení bloku je uživatelská část bloku vyplněna hodnotou 0xCD a každá z vyrovnávací paměti přepsání je vyplněna 0xFD.

**_aligned_malloc_dbg** nastaví `errno` , `ENOMEM` jestli se nezdařila alokace paměti, nebo pokud velikost potřebné paměti (včetně výše zmíněné režie) `_HEAP_MAXREQ`překračuje. Další informace o tomto a dalších chybových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). **_Aligned_malloc_dbg** také ověří své parametry. Pokud *Zarovnání* není mocninou 2 nebo *Velikost* je nula, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce vrátí hodnotu null a nastaví `errno` na. `EINVAL`

Informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloků přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi voláním standardní funkce haldy a její ladicí verzí v sestavení ladění aplikace najdete v tématu [ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_malloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)