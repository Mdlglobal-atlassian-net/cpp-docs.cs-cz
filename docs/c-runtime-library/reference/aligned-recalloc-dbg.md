---
title: _aligned_recalloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_recalloc_dbg
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
- _aligned_recalloc_dbg
- aligned_recalloc_dbg
helpviewer_keywords:
- aligned_recalloc_dbg function
- _aligned_recalloc_dbg function
ms.assetid: 55c3c27e-561c-4d6b-9bf9-1e34cc556e4b
ms.openlocfilehash: c0f0cacc5efa5e63cbe05b481f922b35742e3924
ms.sourcegitcommit: beeb77b2976e997debc55b1af35024cc62e62799
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2018
ms.locfileid: "52977781"
---
# <a name="alignedrecallocdbg"></a>_aligned_recalloc_dbg

Změní velikost bloku paměti, která byla přidělena pomocí [_aligned_malloc](aligned-malloc.md) nebo [_aligned_offset_malloc –](aligned-offset-malloc.md) a inicializuje přidělenou paměť na hodnotu 0 (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_recalloc_dbg(
   void * memblock,
   size_t num,
   size_t size,
   size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Aktuální ukazatel bloku paměti.

*Číslo*<br/>
Počet prvků.

*Velikost*<br/>
Velikost v bajtech každého prvku.

*Zarovnání*<br/>
Hodnota zarovnání, které musí být celočíselnou mocninou 2.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo **NULL**.

*Číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, kde byla požadovaná operace rozdělení nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

**_aligned_recalloc_dbg –** vrací neplatný ukazatel na blok paměti a nevyčerpané prostředky se (může být přesunutý). Vrácená hodnota je **NULL** Pokud velikost je nula a argument vyrovnávací paměti není **NULL**, nebo pokud není k dispozici dostatek paměti a rozbalte bloku na danou velikost. V prvním případě původní blok je uvolněn. V druhém případě je beze změny původního bloku. Návratová hodnota odkazuje na prostor úložiště, která je zaručeně jako vhodně zarovnaný pro úložiště libovolného typu objektu. K získání ukazatele na typ jiný než void, použijte přetypování typu na návratovou hodnotu.

Jedná se o chybu znovu přidělit paměti a změnit zarovnání do bloku.

## <a name="remarks"></a>Poznámky

**_aligned_recalloc_dbg –** je ladicí verzi [_aligned_recalloc –](aligned-recalloc.md) funkce. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, každé volání **_aligned_recalloc_dbg –** je omezená na volání **_aligned_recalloc –**. Obě **_aligned_recalloc –** a **_aligned_recalloc_dbg –** přidělení bloku paměti v haldě základní, ale **_aligned_recalloc_dbg –** obsáhne několik ladění funkce: vyrovnávací paměť po obou stranách část blok, který má test pro přetečení s uživatelským a *filename*/*linenumber* informací pro určení původu přidělení požadavky. Sledování přidělování konkrétní typy s parametrem typu blok není podporovaný ladicí funkce pro zarovnané přidělení. Zobrazí se zarovnané přidělení jako _normal_block – blok typu.

**_aligned_recalloc_dbg –** znovu alokuje blok paměti zadaná s trochu více místa, než požadovaná velikost (*číslo* * *velikost*) který může být větší nebo menší než velikost bloku původně přidělené paměti. Další místo používá správce hald ladění k propojení paměť bloků ladicího a k poskytování aplikací s informace hlavičky ladění a přepsat vyrovnávací paměti. Přerozdělení může způsobit přechod původního paměťového bloku na jiné místo v haldě, jakož i změníte velikost bloku paměti. Část uživatele bloku je vyplněny hodnotou 0xCD a přepsat vyrovnávací paměti jsou vyplněny 0xFD.

**_aligned_recalloc_dbg –** nastaví **errno** k **ENOMEM** Pokud selže přidělování paměti. **EINVAL** je vrácena, pokud přesahuje velikost potřebné paměti (včetně režie již bylo zmíněno dříve) **_heap_maxreq –**. Informace o tomto a dalších chybových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Navíc **_aligned_recalloc_dbg –** ověří jeho parametry. Pokud *zarovnání* není mocninou čísla 2, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce vrací **NULL** a nastaví **errno** k **EINVAL**.

Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsob jejich použití naleznete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce haldy standardní a jeho ladicí verze v sestavení pro ladění aplikace najdete v tématu [ladění verze z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_recalloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
