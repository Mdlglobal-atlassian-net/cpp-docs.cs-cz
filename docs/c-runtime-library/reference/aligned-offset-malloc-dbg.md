---
title: _aligned_offset_malloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_offset_malloc_dbg
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
- _aligned_offset_malloc_dbg
- aligned_offset_malloc_dbg
helpviewer_keywords:
- _aligned_offset_malloc_dbg function
- aligned_offset_malloc_dbg function
ms.assetid: 6c242307-c59e-4d63-aae5-d8cbec8e021c
ms.openlocfilehash: 481109a5ed7d137aa2d10c77955a2f460cba43c0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507533"
---
# <a name="alignedoffsetmallocdbg"></a>_aligned_offset_malloc_dbg

Přidělí paměť v zadaných hranicích zarovnání (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_offset_malloc_dbg(
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Velikost požadované alokace paměti.

*Zarovnání*<br/>
Hodnota zarovnání, které musí být celočíselnou mocninou 2.

*Posun*<br/>
Posun na přidělení paměti pro vynucení zarovnání.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo **NULL**.

*Číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, ve kterém se požadovaná operace rozdělení nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

Ukazatele na blok paměti, která byla přidělena nebo **NULL** Pokud se operace nezdařila.

## <a name="remarks"></a>Poznámky

**_aligned_offset_malloc_dbg –** je ladicí verzi [_aligned_offset_malloc –](aligned-offset-malloc.md) funkce. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, každé volání **_aligned_offset_malloc_dbg –** je omezená na volání **_aligned_offset_malloc –**. Obě **_aligned_offset_malloc –** a **_aligned_offset_malloc_dbg –** přidělení bloku paměti v haldě základní, ale **_aligned_offset_malloc_dbg –** nabízí několik funkce ladění: vyrovnávací paměť po obou stranách část uživatele bloku pro testování nevracení, parametr typu blok pro sledování konkrétní přidělení typů a *filename*/*linenumber* informací pro určení původu požadavků na přidělení.

**_aligned_offset_malloc_dbg –** přiděluje blok paměti se trochu více místa požadovaného *velikost*. Další místo používá správce hald ladění k propojení paměť bloků ladicího a k poskytování aplikací s informace hlavičky ladění a přepsat vyrovnávací paměti. Při přidělení bloku část uživatele bloku je vyplněny hodnotou 0xCD a každý z vyrovnávací paměti přepsání jsou vyplněny 0xFD.

**_aligned_offset_malloc_dbg –** je užitečné v situacích, kde je potřeba zarovnání na prvek vnořené; například, pokud zarovnání bylo potřeba ve vnořené třídě.

**_aligned_offset_malloc_dbg –** vychází **malloc**; Další informace najdete v tématu [malloc](malloc.md).

Tato funkce nastaví **errno** k **ENOMEM** Pokud přidělení paměti se nezdařilo nebo pokud byla větší než požadovaná velikost **_heap_maxreq –**. Další informace o **errno**, naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Navíc **_aligned_offset_malloc –** ověří jeho parametry. Pokud *zarovnání* není mocninou čísla 2 nebo, pokud *posun* je větší než nebo rovna hodnotě *velikost* a nenulovou hodnotu, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce vrací **NULL** a nastaví **errno** k **EINVAL**.

Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Informace o typech bloku přidělení a způsob jejich použití naleznete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_offset_malloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
