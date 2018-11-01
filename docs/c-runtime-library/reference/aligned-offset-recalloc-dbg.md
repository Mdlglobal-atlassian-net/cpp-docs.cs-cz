---
title: _aligned_offset_recalloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_offset_recalloc_dbg
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
- aligned_offset_recalloc_dbg
- _aligned_offset_recalloc_dbg
helpviewer_keywords:
- aligned_offset_recalloc_dbg function
- _aligned_offset_recalloc_dbg function
ms.assetid: 7ab719c3-77e0-4d2e-934f-01529d062fbf
ms.openlocfilehash: 0b314b4aca080877b4e41723a8d2010fd8e835ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627965"
---
# <a name="alignedoffsetrecallocdbg"></a>_aligned_offset_recalloc_dbg

Změní velikost bloku paměti, která byla přidělena pomocí [_aligned_malloc](aligned-malloc.md) nebo [_aligned_offset_malloc –](aligned-offset-malloc.md) a inicializuje přidělenou paměť na hodnotu 0 (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_offset_recalloc_dbg(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment,
   size_t offset,
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
Délka v bajtech každého prvku.

*Zarovnání*<br/>
Hodnota zarovnání, které musí být celočíselnou mocninou 2.

*Posun*<br/>
Posun na přidělení paměti pro vynucení zarovnání.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci realloc nebo **NULL**.

*Číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, ve kterém se požadovaná operace realloc nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

**_aligned_offset_recalloc_dbg –** vrací neplatný ukazatel na blok paměti a nevyčerpané prostředky se (může být přesunutý). Vrácená hodnota je **NULL** Pokud velikost je nula a argument vyrovnávací paměti není **NULL**, nebo pokud není k dispozici dostatek paměti a rozbalte bloku na danou velikost. V prvním případě původní blok je uvolněn. V druhém případě je beze změny původního bloku. Návratová hodnota odkazuje na prostor úložiště, která je zaručeně jako vhodně zarovnaný pro úložiště libovolného typu objektu. K získání ukazatele na typ jiný než void, použijte přetypování typu na návratovou hodnotu.

## <a name="remarks"></a>Poznámky

**_aligned_offset_realloc_dbg –** je ladicí verzi [_aligned_offset_recalloc –](aligned-offset-recalloc.md) funkce. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, každé volání **_aligned_offset_recalloc_dbg –** je omezená na volání **_aligned_offset_recalloc –**. Obě **_aligned_offset_recalloc –** a **_aligned_offset_recalloc_dbg –** přidělení bloku paměti v haldě základní, ale **_aligned_offset_recalloc_dbg –** obsáhne Některé funkce pro ladění: vyrovnávací paměť po obou stranách část uživatele bloku pro testování nevracení, parametr typu blok pro sledování konkrétní přidělení typů a *filename*/*číslo řádku*  informací pro určení původu požadavků na přidělení.

**_aligned_offset_realloc_dbg –** znovu alokuje blok zadaná paměťová s mírně více místa požadovaného *newSize*. *newSize* může být větší nebo menší než velikost bloku původně přidělené paměti. Další místo používá správce hald ladění k propojení paměť bloků ladicího a k poskytování aplikací s informace hlavičky ladění a přepsat vyrovnávací paměti. Přerozdělení může způsobit přechod původního paměťového bloku na jiné místo v haldě, jakož i změníte velikost bloku paměti. Pokud se přesune blok paměti obsah původního bloku jsou přepsány.

Tato funkce nastaví **errno** k **ENOMEM** Pokud přidělení paměti se nezdařilo nebo pokud požadovaná velikost (*číslo* * *velikost* ) byla větší než **_heap_maxreq –**. Další informace o **errno**, naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Navíc **_aligned_offset_recalloc_dbg –** ověří jeho parametry. Pokud *zarovnání* není mocninou čísla 2 nebo, pokud *posun* je větší než nebo rovna požadované velikosti a nenulovou hodnotu, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [parametr Ověření](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce vrací **NULL** a nastaví **errno** k **EINVAL**.

Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsob jejich použití naleznete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce haldy standardní a jeho ladicí verze v sestavení pro ladění aplikace najdete v tématu [ladění verze z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_offset_recalloc_dbg**|\<malloc.h >|

## <a name="see-also"></a>Viz také:

[Zarovnání dat](../../c-runtime-library/data-alignment.md)<br/>
