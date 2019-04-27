---
title: _recalloc_dbg
ms.date: 11/04/2016
apiname:
- _recalloc_dbg
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
apitype: DLLExport
f1_keywords:
- recalloc_dbg
- _recalloc_dbg
helpviewer_keywords:
- _recalloc_dbg function
- recalloc_dbg function
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
ms.openlocfilehash: e2782492d3338b5b548db0153b6123fb82ff5e72
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357681"
---
# <a name="recallocdbg"></a>_recalloc_dbg

Znovu alokuje pole a inicializuje jeho prvky na hodnotu 0 (pouze ladicí verze).

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
Ukazatele na blok paměti dříve přidělené.

*Číslo*<br/>
Požadovaný počet bloky paměti.

*Velikost*<br/>
Požadovaná velikost každého bloku paměti (v bajtech).

*blockType*<br/>
Požadovaný typ bloku paměti: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

Informace o typech bloku přidělení a způsob jejich použití naleznete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo **NULL**.

*linenumber*<br/>
Číslo řádku ve zdrojovém souboru, kde byla požadovaná operace rozdělení nebo **NULL**.

*Filename* a *linenumber* parametry jsou k dispozici pouze při **_recalloc_dbg –** explicitně volána nebo [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) byla definována konstanta preprocesoru.

## <a name="return-value"></a>Návratová hodnota

Při úspěšném dokončení, tato funkce vrací ukazatel na část uživatele bloku paměti nevyčerpané, volá funkci novou obslužnou rutinu nebo vrátí **NULL**. Úplný popis návratový chování najdete v části poznámky. Další informace o tom, jak použít nové funkce obslužné rutiny najdete v tématu [_recalloc –](recalloc.md) funkce.

## <a name="remarks"></a>Poznámky

**_recalloc_dbg –** je ladicí verzi [_recalloc –](recalloc.md) funkce. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, každé volání **_recalloc_dbg –** je omezená na volání **_recalloc –**. Obě **_recalloc –** a **_recalloc_dbg –** přidělení bloku paměti v haldě základní, ale **_recalloc_dbg –** obsáhne některé funkce pro ladění: vyrovnávací paměť po obou stranách část bloku pro testování nevracení uživatelským blok zadejte parametr pro sledování konkrétní přidělení typů a *filename*/*linenumber* informací pro určení, původ požadavků na přidělení.

**_recalloc_dbg –** znovu alokuje blok paměti zadaná s trochu více místa, než požadovaná velikost (*číslo* * *velikost*) který může být větší nebo menší než velikost blok původně přidělené paměti. Další místo používá správce hald ladění k propojení paměť bloků ladicího a k poskytování aplikací s informace hlavičky ladění a přepsat vyrovnávací paměti. Přerozdělení může způsobit přechod původního paměťového bloku na jiné místo v haldě, jakož i změníte velikost bloku paměti. Část uživatele bloku je vyplněny hodnotou 0xCD a každý z vyrovnávací paměti přepsání jsou vyplněny 0xFD.

**_recalloc_dbg –** nastaví **errno** k **ENOMEM** Pokud selže přidělování paměti. **EINVAL** je vrácena, pokud přesahuje velikost potřebné paměti (včetně režie již bylo zmíněno dříve) **_heap_maxreq –**. Informace o tomto a dalších chybových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce haldy standardní a jeho ladicí verze v sestavení pro ladění aplikace najdete v tématu [ladění verze z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_recalloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
