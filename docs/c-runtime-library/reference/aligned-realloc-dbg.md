---
title: _aligned_realloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_realloc_dbg
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
- aligned_realloc_dbg
- _aligned_realloc_dbg
helpviewer_keywords:
- _aligned_realloc_dbg function
- aligned_realloc_dbg function
ms.assetid: 8aede920-991e-44cd-867f-83dc2165db47
ms.openlocfilehash: 2a261b3e578bef5464bbfda8528ffd8b491acb23
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545948"
---
# <a name="alignedreallocdbg"></a>_aligned_realloc_dbg

Změní velikost bloku paměti, která byla přidělena pomocí [_aligned_malloc](aligned-malloc.md) nebo [_aligned_offset_malloc –](aligned-offset-malloc.md) (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_realloc_dbg(
   void *memblock,
   size_t size,
   size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Aktuální ukazatel bloku paměti.

*Velikost*<br/>
Velikost požadované alokace paměti.

*Zarovnání*<br/>
Hodnota zarovnání, které musí být celočíselnou mocninou 2.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který vyžadují **realloc** operace nebo **NULL**.

*Číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru kde **realloc** operace byla požadována nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

**_aligned_realloc_dbg –** vrací neplatný ukazatel na blok paměti a nevyčerpané prostředky se (může být přesunutý). Vrácená hodnota je **NULL** Pokud velikost je nula a argument vyrovnávací paměti není **NULL**, nebo pokud není k dispozici dostatek paměti a rozbalte bloku na danou velikost. V prvním případě původní blok je uvolněn. V druhém se nezmění původní blok. Návratová hodnota odkazuje na prostor úložiště, která je zaručeně jako vhodně zarovnaný pro úložiště libovolného typu objektu. K získání ukazatele na typ jiný než void, použijte přetypování typu na návratovou hodnotu.

Jedná se o chybu znovu přidělit paměti a změnit zarovnání do bloku.

## <a name="remarks"></a>Poznámky

**_aligned_realloc_dbg –** je ladicí verzi [_aligned_realloc –](aligned-realloc.md) funkce. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, každé volání **_aligned_realloc_dbg –** je omezená na volání **_aligned_realloc –**. Obě **_aligned_realloc –** a **_aligned_realloc_dbg –** přidělení bloku paměti v haldě základní, ale **_aligned_realloc_dbg –** obsáhne některé funkce pro ladění : vyrovnávací paměť po obou stranách část uživatele bloku pro testování nevracení, parametr typu blok pro sledování konkrétní přidělení typů a *filename*/*linenumber* informace k určení původu požadavků na přidělení.

**_aligned_realloc_dbg –** znovu alokuje blok zadaná paměťová s mírně více místa požadovaného *newSize*. *newSize* může být větší nebo menší než velikost bloku původně přidělené paměti. Další místo používá správce hald ladění k propojení paměť bloků ladicího a k poskytování aplikací s informace hlavičky ladění a přepsat vyrovnávací paměti. Přerozdělení může způsobit přechod původního paměťového bloku na jiné místo v haldě, jakož i změníte velikost bloku paměti. Pokud se přesune blok paměti obsah původního bloku jsou přepsány.

**_aligned_realloc_dbg –** nastaví **errno** k **ENOMEM** Pokud selhání přidělení paměti nebo pokud přesahuje velikost potřebné paměti (včetně režie již bylo zmíněno dříve) **_ Heap_maxreq –**. Informace o tomto a dalších chybových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Navíc **_aligned_realloc_dbg –** ověří jeho parametry. Pokud *zarovnání* není mocninou čísla 2, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce vrací **NULL** a nastaví **errno** k **EINVAL**.

Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsob jejich použití naleznete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce haldy standardní a jeho ladicí verze v sestavení pro ladění aplikace najdete v tématu [ladění verze z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_realloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
