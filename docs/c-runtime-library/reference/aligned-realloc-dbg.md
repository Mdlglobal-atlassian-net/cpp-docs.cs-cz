---
title: _aligned_realloc_dbg – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _aligned_realloc_dbg function
- aligned_realloc_dbg function
ms.assetid: 8aede920-991e-44cd-867f-83dc2165db47
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fd5854bc18cecda1fd3ffee4f28ec2fa5d2a68a
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451664"
---
# <a name="alignedreallocdbg"></a>_aligned_realloc_dbg

Změní velikost bloku paměti, který byl přidělen s [_aligned_malloc –](aligned-malloc.md) nebo [_aligned_offset_malloc –](aligned-offset-malloc.md) (pouze ladicí verze).

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
Velikost velikost paměti požadované přidělení.

*Zarovnání*<br/>
Zarovnání hodnota, která musí být celé číslo mocninou 2.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který vyžadují **realloc –** operaci nebo **NULL**.

*lineNumber*<br/>
Číslo řádku na zdrojový soubor kde **realloc –** byla vyžádána operace nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

**_aligned_realloc_dbg –** vrací neplatný ukazatel k opětovnému přidělení (a případně přesouvat) paměti bloku. Vrácená hodnota je **NULL** Pokud velikost je nula a argument vyrovnávací paměti není **NULL**, nebo pokud není k dispozici dostatek paměti k rozšíření bloku na danou velikost. V prvním případě původní blok uvolněno. Za sekundu původní blok je beze změny. Návratová hodnota odkazuje na prostor úložiště, který zaručeně vhodně zarovnána pro ukládání jakéhokoli typu objektu. Získání ukazatele na typ než void, použijte typ přetypovat na návratovou hodnotu.

Jedná se o chybu, znovu přidělte paměť a změňte zarovnání bloku.

## <a name="remarks"></a>Poznámky

**_aligned_realloc_dbg –** je ladicí verze [_aligned_realloc –](aligned-realloc.md) funkce. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, každé volání **_aligned_realloc_dbg –** byla snížena volání **_aligned_realloc –**. Obě **_aligned_realloc –** a **_aligned_realloc_dbg –** znovu přidělte blok paměti základní haldy, ale **_aligned_realloc_dbg –** může vyrovnávat několik funkce ladění : vyrovnávací paměti na obou stranách části uživatele bloku chcete otestovat nevracení, parametr typ bloku ke sledování přidělení konkrétní typy a *filename*/*linenumber* informace k určení původu požadavků na přidělení.

**_aligned_realloc_dbg –** přidělí blok zadaná paměťová se něco víc místa, než požadovaný *newSize*. *newSize* může být větší nebo menší než velikost bloku původně přidělenou paměť. Další prostor se používá správce haldy ladění propojení bloky paměti ladění a k poskytování aplikace s informace o ladění záhlaví a přepsat vyrovnávací paměti. Přerozdělení může způsobit přesunutí původní bloku paměti do jiného umístění v haldě, jakož i změníte velikost bloku paměti. Pokud se přesune bloku paměti, obsah původního bloku se přepíší.

**_aligned_realloc_dbg –** nastaví **errno** k **enomem –** Pokud selže přidělení paměti nebo pokud přesahuje množství paměti nutné (včetně režie, již bylo zmíněno dříve) **_ Heap_maxreq –**. Informace o tomto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Navíc **_aligned_realloc_dbg –** ověří jeho parametry. Pokud *zarovnání* není napájení 2, tato funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu **NULL** a nastaví **errno** k **einval –**.

Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce standardní haldy a jeho ladicí verze v sestavení ladicí verze aplikace, najdete v tématu [ladění verzí z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_realloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
