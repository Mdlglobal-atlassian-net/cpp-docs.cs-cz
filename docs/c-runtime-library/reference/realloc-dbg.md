---
title: _realloc_dbg
ms.date: 11/04/2016
apiname:
- _realloc_dbg
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
- _realloc_dbg
- realloc_dbg
helpviewer_keywords:
- reallocating memory blocks
- realloc_dbg function
- memory blocks, reallocating
- memory, reallocating
- _realloc_dbg function
ms.assetid: 7c3cb780-51ed-4d9c-9929-cdde606d846a
ms.openlocfilehash: 9b30dfd6fbae9a4831ff53e7896aeb995657da03
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640281"
---
# <a name="reallocdbg"></a>_realloc_dbg

Znovu zadaný blok paměti v haldě alokuje přesunutí nebo změně velikosti bloku (pouze ladicí verze).

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
Ukazatele na blok paměti dříve přidělené.

*newSize*<br/>
Požadovaná velikost pro reallocated bloku (v bajtech).

*blockType*<br/>
Požadovaný typ pro reallocated blok: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který vyžadují **realloc** operace nebo **NULL**.

*Číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru kde **realloc** operace byla požadována nebo **NULL**.

*Filename* a *linenumber* parametry jsou k dispozici pouze při **_realloc_dbg –** explicitně volána nebo [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) byla definována konstanta preprocesoru.

## <a name="return-value"></a>Návratová hodnota

Při úspěšném dokončení, tato funkce vrací ukazatel na část uživatele bloku paměti nevyčerpané, volá funkci novou obslužnou rutinu nebo vrátí **NULL**. Úplný popis návratový chování najdete v části poznámky. Další informace o tom, jak použít nové funkce obslužné rutiny najdete v tématu [realloc](realloc.md) funkce.

## <a name="remarks"></a>Poznámky

**_realloc_dbg –** je ladicí verzi [realloc](realloc.md) funkce. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, každé volání **_realloc_dbg –** je omezená na volání **realloc**. Obě **realloc** a **_realloc_dbg –** přidělení bloku paměti v haldě základní, ale **_realloc_dbg –** obsáhne některé funkce pro ladění: vyrovnávací paměť po obou stranách část uživatele bloku pro testování nevracení, parametr typu blok pro sledování konkrétní přidělení typů a *filename*/*linenumber* informací pro určení původu požadavky na přidělení.

**_realloc_dbg –** znovu alokuje blok zadaná paměťová s mírně více místa požadovaného *newSize*. *newSize* může být větší nebo menší než velikost bloku původně přidělené paměti. Další místo používá správce hald ladění k propojení paměť bloků ladicího a k poskytování aplikací s informace hlavičky ladění a přepsat vyrovnávací paměti. Přerozdělení může způsobit přechod původního paměťového bloku na jiné místo v haldě, jakož i změníte velikost bloku paměti. Pokud se přesune blok paměti obsah původního bloku jsou přepsány.

**_realloc_dbg –** nastaví **errno** k **ENOMEM** Pokud selhání přidělení paměti nebo pokud přesahuje velikost potřebné paměti (včetně režie již bylo zmíněno dříve) **_HEAP_ MAXREQ**. Informace o tomto a dalších chybových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsob jejich použití naleznete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce haldy standardní a jeho ladicí verze v sestavení pro ladění aplikace najdete v tématu [ladění verze z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_realloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

Podívejte se na příklad v [_msize_dbg –](msize-dbg.md) tématu.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
