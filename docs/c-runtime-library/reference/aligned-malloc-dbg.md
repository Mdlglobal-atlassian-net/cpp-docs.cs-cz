---
title: _aligned_malloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_malloc_dbg
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
- _aligned_malloc_dbg
- aligned_malloc_dbg
helpviewer_keywords:
- aligned_malloc_dbg function
- _aligned_malloc_dbg function
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
ms.openlocfilehash: eb58313c892ffe13e9f8e34e98b7940022899d14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341636"
---
# <a name="alignedmallocdbg"></a>_aligned_malloc_dbg

Přidělí paměť v zadaných hranicích zarovnání s další místo pro ladění záhlaví a přepsat vyrovnávací paměti (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_malloc_dbg(
    size_t size,
    size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Velikost požadované alokace paměti.

*Zarovnání*<br/>
Hodnota zarovnání, které musí být celočíselnou mocninou 2.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který se požadovaná operace rozdělení nebo hodnota NULL.

*linenumber*<br/>
Číslo řádku ve zdrojovém souboru, ve kterém se požadovaná operace rozdělení nebo hodnota NULL.

## <a name="return-value"></a>Návratová hodnota

Ukazatele na blok paměti, která byla přidělena nebo hodnota NULL, pokud operace se nezdařila.

## <a name="remarks"></a>Poznámky

**_aligned_malloc_dbg –** je ladicí verzi [_aligned_malloc](aligned-malloc.md) funkce. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, každé volání **_aligned_malloc_dbg –** je omezená na volání `_aligned_malloc`. Obě `_aligned_malloc` a **_aligned_malloc_dbg –** přidělení bloku paměti v haldě základní, ale **_aligned_malloc_dbg –** nabízí některé funkce pro ladění: vyrovnávací paměť po obou stranách část s uživatelským blok pro testování nevracení, a *filename*/*linenumber* informací pro určení původu požadavků na přidělení. Sledování přidělování konkrétní typy s parametrem typu blok není podporovaný ladicí funkce pro zarovnané přidělení. Zobrazí se zarovnané přidělení jako _normal_block – blok typu.

**_aligned_malloc_dbg –** přiděluje blok paměti se trochu více místa požadovaného *velikost*. Další místo používá správce hald ladění k propojení paměť bloků ladicího a k poskytování aplikací s informace hlavičky ladění a přepsat vyrovnávací paměti. Při přidělení bloku část uživatele bloku je vyplněny hodnotou 0xCD a každý z vyrovnávací paměti přepsání jsou vyplněny 0xFD.

**_aligned_malloc_dbg –** nastaví `errno` k `ENOMEM` Pokud selhání přidělení paměti nebo pokud přesahuje velikost potřebné paměti (včetně režie již bylo zmíněno dříve) `_HEAP_MAXREQ`. Informace o tomto a dalších chybových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Navíc **_aligned_malloc_dbg –** ověří jeho parametry. Pokud *zarovnání* není mocninou čísla 2 nebo *velikost* je nula, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce vrátí hodnotu NULL a nastaví `errno` k `EINVAL`.

Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsob jejich použití naleznete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce haldy standardní a jeho ladicí verze v sestavení pro ladění aplikace najdete v tématu [ladění verze z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_malloc_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)