---
title: _malloc_dbg
ms.date: 11/04/2016
api_name:
- _malloc_dbg
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
- malloc_dbg
- _malloc_dbg
helpviewer_keywords:
- malloc_dbg function
- memory allocation
- _malloc_dbg function
ms.assetid: c97eca51-140b-4461-8bd2-28965b49ecdb
ms.openlocfilehash: cfaaaec17dc8546c937045f93027e9609981bd93
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952883"
---
# <a name="_malloc_dbg"></a>_malloc_dbg

Přidělí blok paměti v haldě s dodatečnou mezerou pro hlavičku ladění a přepíše vyrovnávací paměti (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void *_malloc_dbg(
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
Požadovaná velikost bloku paměti (v bajtech).

*blockType*<br/>
Požadovaný typ bloku paměti: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

*Bitmap*<br/>
Ukazatel na název zdrojového souboru, který požadoval operaci přidělení, nebo **hodnotu null**.

*číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, kde byla požadována operace přidělení, nebo **hodnota null**.

Parametry *filename* a *číslo řádku* jsou k dispozici pouze v případě, že byla explicitně volána metoda **_malloc_dbg** nebo byla definována konstanta preprocesoru [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) .

## <a name="return-value"></a>Návratová hodnota

Po úspěšném dokončení Tato funkce vrátí ukazatel na uživatelskou část přiděleného bloku paměti, zavolá novou funkci obslužné rutiny nebo vrátí **hodnotu null**. Úplný popis vráceného chování naleznete v následující části poznámky. Další informace o tom, jak se používá nová funkce obslužné rutiny, [najdete v tématu funkce.](malloc.md)

## <a name="remarks"></a>Poznámky

**_malloc_dbg** je ladicí [verze funkce.](malloc.md) Pokud není definován [_DEBUG](../../c-runtime-library/debug.md) , každé volání **_malloc_dbg** je sníženo **na volání metody.** Třídy **\** a **_malloc_dbg** přidělují blok paměti v základní haldě, ale **_malloc_dbg** nabízí několik funkcí ladění: vyrovnávací paměti na obou stranách bloku pro testování nevracení, parametr typu bloku ke sledování konkrétní typy přidělení a informace o *názvu souboru*/*číslo řádku* , abyste určili původ požadavků na přidělení.

**_malloc_dbg** přiděluje blok paměti o něco více místa, než je požadovaná *Velikost*. Dodatečné místo se používá správcem haldy ladění k propojení bloků paměti ladění a k poskytnutí aplikace s informacemi hlavičky ladění a přepsat vyrovnávací paměti. Po přidělení bloku je uživatelská část bloku vyplněna hodnotou 0xCD a každá z vyrovnávací paměti přepsání je vyplněna 0xFD.

**_malloc_dbg** nastaví **errno** na **ENOMEM** , pokud se přidělení paměti nepovede, nebo pokud velikost potřebné paměti (včetně výše zmíněné režie) překračuje **_HEAP_MAXREQ**. Další informace o tomto a dalších chybových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloků přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi voláním standardní funkce haldy a její ladicí verzí v sestavení ladění aplikace najdete v tématu [ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_malloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Příklad

Ukázku použití **_malloc_dbg**naleznete v tématu [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[malloc](malloc.md)<br/>
[_calloc_dbg](calloc-dbg.md)<br/>
