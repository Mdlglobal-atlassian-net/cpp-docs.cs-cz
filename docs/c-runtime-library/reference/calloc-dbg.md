---
title: _calloc_dbg
ms.date: 11/04/2016
api_name:
- _calloc_dbg
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
- _calloc_dbg
- calloc_dbg
helpviewer_keywords:
- _calloc_dbg function
- calloc_dbg function
ms.assetid: 7f62c42b-eb9f-4de5-87d0-df57036c87de
ms.openlocfilehash: eab17348e473a4f642e784defe4569e0e799299e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939322"
---
# <a name="_calloc_dbg"></a>_calloc_dbg

Přiděluje počet bloků paměti v haldě s dodatečnou mezerou pro hlavičku ladění a přepíše vyrovnávací paměti (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void *_calloc_dbg(
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*Automatické*<br/>
Požadovaný počet bloků paměti.

*hodnota*<br/>
Požadovaná velikost každého bloku paměti (v bajtech).

*blockType*<br/>
Požadovaný typ bloku paměti: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

Informace o typech bloků přidělení a způsobu jejich použití naleznete v tématu[typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

*Bitmap*<br/>
Ukazatel na název zdrojového souboru, který požadoval operaci přidělení, nebo **hodnota null**.

*číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, kde byla požadována operace přidělení, nebo **hodnota null**.

Parametry *filename* a *číslo řádku* jsou k dispozici pouze v případě, že byla explicitně volána metoda **_calloc_dbg** nebo byla definována konstanta preprocesoru [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) .

## <a name="return-value"></a>Návratová hodnota

Po úspěšném dokončení Tato funkce vrátí ukazatel na uživatelskou část posledního přiděleného bloku paměti, zavolá novou funkci obslužné rutiny nebo vrátí **hodnotu null**. Úplný popis vráceného chování naleznete v části poznámky. Další informace o tom, jak se používá nová funkce obslužné rutiny, najdete v tématu funkce [calloc](calloc.md) .

## <a name="remarks"></a>Poznámky

**_calloc_dbg** je ladicí verze funkce [calloc](calloc.md) . Pokud není definován [_DEBUG](../../c-runtime-library/debug.md) , každé volání **_calloc_dbg** je sníženo na volání **calloc**. **Calloc** i **_calloc_dbg** přidělují *číselné* bloky paměti v základní haldě, ale **_calloc_dbg** nabízí několik funkcí ladění:

- Vyrovnávací paměti na kterékoli straně uživatelské části bloku k otestování nevracení.

- Parametr typu bloku ke sledování konkrétních typů přidělení.

- filename/*číslo řádku* informace k určení původu žádostí o přidělení.

**_calloc_dbg** přiděluje každý blok paměti o něco více místa, než je požadovaná *Velikost*. Dodatečné místo se používá správcem haldy ladění k propojení bloků paměti ladění a k poskytnutí aplikace s informacemi hlavičky ladění a přepsat vyrovnávací paměti. Po přidělení bloku je uživatelská část bloku vyplněna hodnotou 0xCD a každá z vyrovnávací paměti přepsání je vyplněna 0xFD.

**_calloc_dbg** nastaví **errno** na **ENOMEM** , pokud není přidělení paměti úspěšné; **EINVAL** se vrátí, pokud velikost potřebné paměti (včetně výše zmíněné režie) překračuje **_HEAP_MAXREQ**. Další informace o tomto a dalších chybových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi voláním standardní funkce haldy oproti verzi ladicího programu v sestavení ladění aplikace naleznete v tématu [ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_calloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_callocd.c
// This program uses _calloc_dbg to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>
#include <crtdbg.h>

int main( void )
{
    long *bufferN, *bufferC;

    // Call _calloc_dbg to include the filename and line number
    // of our allocation request in the header and also so we can
    // allocate CLIENT type blocks specifically
    bufferN = (long *)_calloc_dbg( 40, sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );
    bufferC = (long *)_calloc_dbg( 40, sizeof(long), _CLIENT_BLOCK, __FILE__, __LINE__ );
    if( bufferN != NULL && bufferC != NULL )
        printf( "Allocated memory successfully\n" );
    else
        printf( "Problem allocating memory\n" );

    / _free_dbg must be called to free CLIENT type blocks
    free( bufferN );
    _free_dbg( bufferC, _CLIENT_BLOCK );
}
```

```Output
Allocated memory successfully
```

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[calloc](calloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
