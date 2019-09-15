---
title: _realloc_dbg
ms.date: 11/04/2016
api_name:
- _realloc_dbg
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
- _realloc_dbg
- realloc_dbg
helpviewer_keywords:
- reallocating memory blocks
- realloc_dbg function
- memory blocks, reallocating
- memory, reallocating
- _realloc_dbg function
ms.assetid: 7c3cb780-51ed-4d9c-9929-cdde606d846a
ms.openlocfilehash: 58d12ed6f4b013996f3f59cba1b146b823adbee6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949517"
---
# <a name="_realloc_dbg"></a>_realloc_dbg

Znovu přidělí zadaný blok paměti v haldě přesunutím a/nebo změnou velikosti bloku (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void *_realloc_dbg(
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
Požadovaná velikost pro znovu přidělený blok (bajty)

*blockType*<br/>
Požadovaný typ pro znovu přidělený blok: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

*Bitmap*<br/>
Ukazatel na název zdrojového souboru, který požadoval operaci **realokace** nebo **null**.

*číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, kde byla požadována operace **realokace** nebo **hodnota null**.

Parametry *filename* a *číslo řádku* jsou k dispozici pouze v případě, že byla explicitně volána metoda **_realloc_dbg** nebo byla definována konstanta preprocesoru [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) .

## <a name="return-value"></a>Návratová hodnota

Po úspěšném dokončení Tato funkce buď vrátí ukazatel na uživatelskou část bloku přerozdělené paměti, zavolá novou funkci obslužné rutiny nebo vrátí **hodnotu null**. Úplný popis vráceného chování naleznete v následující části poznámky. Další informace o použití nové funkce obslužné rutiny naleznete v tématu funkce [realokace](realloc.md) .

## <a name="remarks"></a>Poznámky

**_realloc_dbg** je ladicí verze funkce [realokace](realloc.md) . Pokud není definován [_DEBUG](../../c-runtime-library/debug.md) , každé volání **_realloc_dbg** je sníženo na volání pro **repřidělení**. **Realokace** a **_realloc_dbg** znovu přidělí blok paměti v základní haldě, ale **_realloc_dbg** se přizpůsobí několika funkcím pro ladění: vyrovnávací paměti na obou stranách bloku pro testování nevracení, parametr typu bloku pro Sledujte konkrétní typy přidělení a*číslo řádku* informace o *názvu souboru*/, abyste zjistili původ požadavků na přidělení.

**_realloc_dbg** znovu přidělí zadaný blok paměti o více místa, než je požadovaný *NewSize*. *NewSize* může být větší nebo menší než velikost původně přiděleného bloku paměti. Dodatečné místo se používá správcem haldy ladění k propojení bloků paměti ladění a k poskytnutí aplikace s informacemi hlavičky ladění a přepsat vyrovnávací paměti. Přerozdělení může mít za následek přesunutí původního bloku paměti na jiné místo v haldě a změnu velikosti bloku paměti. Pokud se blok paměti přesune, obsah původního bloku se přepíše.

**_realloc_dbg** nastaví **errno** na **ENOMEM** , pokud se přidělení paměti nepovede, nebo pokud velikost potřebné paměti (včetně výše zmíněné režie) překračuje **_HEAP_MAXREQ**. Další informace o tomto a dalších chybových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloků přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi voláním standardní funkce haldy a její ladicí verzí v sestavení ladění aplikace najdete v tématu [ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_realloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Příklad

Podívejte se na příklad v tématu [_msize_dbg](msize-dbg.md) .

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
