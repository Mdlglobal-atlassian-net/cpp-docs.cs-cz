---
title: _aligned_recalloc_dbg – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- aligned_recalloc_dbg function
- _aligned_recalloc_dbg function
ms.assetid: 55c3c27e-561c-4d6b-9bf9-1e34cc556e4b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a73142a832f98caa673c014bad0a909749af3cd9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="alignedrecallocdbg"></a>_aligned_recalloc_dbg

Změní velikost bloku paměti, který byl přidělen s [_aligned_malloc –](aligned-malloc.md) nebo [_aligned_offset_malloc –](aligned-offset-malloc.md) a inicializuje paměť na hodnotu 0 (pouze ladicí verze).

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
Počet elementů.

*Velikost*<br/>
Velikost v bajtech jednotlivých prvků.

*Zarovnání*<br/>
Zarovnání hodnota, která musí být celé číslo mocninou 2.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo **NULL**.

*lineNumber*<br/>
Číslo řádku na zdrojový soubor, kde byla vyžádána operace přidělení nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

**_aligned_recalloc_dbg –** vrací neplatný ukazatel k opětovnému přidělení (a případně přesouvat) paměti bloku. Vrácená hodnota je **NULL** Pokud velikost je nula a argument vyrovnávací paměti není **NULL**, nebo pokud není k dispozici dostatek paměti k rozšíření bloku na danou velikost. V prvním případě původní blok uvolněno. V druhém případě je původní blok beze změny. Návratová hodnota odkazuje na prostor úložiště, který zaručeně vhodně zarovnána pro ukládání jakéhokoli typu objektu. Získání ukazatele na typ než void, použijte typ přetypovat na návratovou hodnotu.

Jedná se o chybu, znovu přidělte paměť a změňte zarovnání bloku.

## <a name="remarks"></a>Poznámky

**_aligned_recalloc_dbg –** je ladicí verze [_aligned_recalloc –](aligned-recalloc.md) funkce. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, každé volání **_aligned_recalloc_dbg –** byla snížena volání **_aligned_recalloc –**. Obě **_aligned_recalloc –** a **_aligned_recalloc_dbg –** znovu přidělte blok paměti základní haldy, ale **_aligned_recalloc_dbg –** může vyrovnávat několik ladění funkce: vyrovnávací paměti na obou stranách části uživatele bloku chcete otestovat nevracení, parametr typ bloku ke sledování přidělení konkrétní typy a *filename*/*linenumber* informace k určení původu požadavků na přidělení.

**_aligned_recalloc_dbg –** přidělí blok zadaná paměťová se něco víc místa, než požadovaná velikost (*číslo* * *velikost*) který může být větší nebo menší než velikost bloku původně přidělenou paměť. Další prostor se používá správce haldy ladění propojení bloky paměti ladění a k poskytování aplikace s informace o ladění záhlaví a přepsat vyrovnávací paměti. Přerozdělení může způsobit přesunutí původní bloku paměti do jiného umístění v haldě, jakož i změníte velikost bloku paměti. Část uživatele bloku je vyplněnou hodnotou 0xCD a přepsat vyrovnávací paměti jsou vyplněny 0xFD.

**_aligned_recalloc_dbg –** nastaví **errno** k **enomem –** Pokud selže přidělení paměti; **Einval –** je vrácena, pokud objem paměti vyžadované (včetně režie, již bylo zmíněno dříve) přesahuje **_heap_maxreq –**. Informace o tomto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Navíc **_aligned_recalloc_dbg –** ověří jeho parametry. Pokud *zarovnání* není napájení 2, tato funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu **NULL** a nastaví **errno** k **einval –**.

Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce standardní haldy a jeho ladicí verze v sestavení ladicí verze aplikace, najdete v tématu [ladění verzí z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_recalloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
