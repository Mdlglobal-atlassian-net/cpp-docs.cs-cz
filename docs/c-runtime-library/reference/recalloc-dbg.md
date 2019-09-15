---
title: _recalloc_dbg
ms.date: 11/04/2016
api_name:
- _recalloc_dbg
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
- recalloc_dbg
- _recalloc_dbg
helpviewer_keywords:
- _recalloc_dbg function
- recalloc_dbg function
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
ms.openlocfilehash: 6274e749b2c4e6f64c7c7f82f8764dcf5ba642fe
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949473"
---
# <a name="_recalloc_dbg"></a>_recalloc_dbg

Znovu přidělí pole a inicializuje jeho prvky na hodnotu 0 (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void *_recalloc_dbg(
   void *userData,
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*userData*<br/>
Ukazatel na dříve přidělený blok paměti.

*Automatické*<br/>
Požadovaný počet bloků paměti.

*hodnota*<br/>
Požadovaná velikost každého bloku paměti (v bajtech).

*blockType*<br/>
Požadovaný typ bloku paměti: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

Informace o typech bloků přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

*Bitmap*<br/>
Ukazatel na název zdrojového souboru, který požadoval operaci přidělení, nebo **hodnota null**.

*číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, kde byla požadována operace přidělení, nebo **hodnota null**.

Parametry *filename* a *číslo řádku* jsou k dispozici pouze v případě, že byla explicitně volána metoda **_recalloc_dbg** nebo byla definována konstanta preprocesoru [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) .

## <a name="return-value"></a>Návratová hodnota

Po úspěšném dokončení Tato funkce buď vrátí ukazatel na uživatelskou část bloku přerozdělené paměti, zavolá novou funkci obslužné rutiny nebo vrátí **hodnotu null**. Úplný popis vráceného chování naleznete v následující části poznámky. Další informace o tom, jak se používá nová funkce obslužné rutiny, najdete v tématu funkce [_recalloc](recalloc.md) .

## <a name="remarks"></a>Poznámky

**_recalloc_dbg** je ladicí verze funkce [_recalloc](recalloc.md) . Pokud není definován [_DEBUG](../../c-runtime-library/debug.md) , každé volání **_recalloc_dbg** je sníženo na volání **_recalloc**. **_Recalloc** i **_recalloc_dbg** znovu přidělí blok paměti v základní haldě, ale **_recalloc_dbg** nabízí několik funkcí ladění: vyrovnávací paměti na obou stranách bloku pro testování nevracení, parametr typu bloku Chcete-li sledovat konkrétní typy přidělení, a*číslo řádku* informace o *názvu souboru*/, abyste určili původ požadavků na přidělení.

**_recalloc_dbg** znovu přidělí zadaný blok paměti o více místa, než je požadovaná velikost (*Číselná* * *Velikost*), která může být větší nebo menší než velikost původně přiděleného bloku paměti. Dodatečné místo se používá správcem haldy ladění k propojení bloků paměti ladění a k poskytnutí aplikace s informacemi hlavičky ladění a přepsat vyrovnávací paměti. Přerozdělení může mít za následek přesunutí původního bloku paměti na jiné místo v haldě a změnu velikosti bloku paměti. Uživatelská část bloku je vyplněna hodnotou 0xCD a každá z vyrovnávací paměti přepsání je vyplněna 0xFD.

**_recalloc_dbg** nastaví **errno** na **ENOMEM** , pokud není přidělení paměti úspěšné; **EINVAL** se vrátí, pokud velikost potřebné paměti (včetně výše zmíněné režie) překračuje **_HEAP_MAXREQ**. Další informace o tomto a dalších chybových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi voláním standardní funkce haldy a její ladicí verzí v sestavení ladění aplikace najdete v tématu [ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_recalloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
