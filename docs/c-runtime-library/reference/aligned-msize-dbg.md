---
title: _aligned_msize_dbg
ms.date: 11/04/2016
apiname:
- _aligned_msize_dbg
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
- _aligned_msize_dbg
helpviewer_keywords:
- _aligned_msize_dbg
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
ms.openlocfilehash: 054f7b88f93eef37a9a88fbb7895452f7c158716
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451295"
---
# <a name="alignedmsizedbg"></a>_aligned_msize_dbg

Vrátí velikost bloku paměti přiděleny do haldy (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
size_t _aligned_msize_dbg(
   void *memblock,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Ukazatele na blok paměti.

*Zarovnání*<br/>
Hodnota zarovnání, které musí být celočíselnou mocninou 2.

*Posun*<br/>
Posun na přidělení paměti pro vynucení zarovnání.

## <a name="return-value"></a>Návratová hodnota

Vrátí velikost (v bajtech) jako celé číslo bez znaménka.

## <a name="remarks"></a>Poznámky

*Zarovnání* a *posun* hodnoty musí být stejný jako hodnoty předané na funkci, která přidělené bloku.

**_aligned_msize_dbg** je ladicí verzi [_aligned_msize –](aligned-msize.md) funkce. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, každé volání **_aligned_msize_dbg** je omezená na volání **_aligned_msize –**. Obě **_aligned_msize –** a **_aligned_msize_dbg** vypočítat velikost bloku paměti v haldě základní, ale **_aligned_msize_dbg** přidá funkce ladění: zahrnuje blok, ve vrácené velikost vyrovnávací paměti na obou stranách uživatele část paměti.

Tato funkce ověřuje svůj parametr. Pokud *memblock* je ukazatel s hodnotou null nebo *zarovnání* není mocninou čísla 2, **_msize –** vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation ](../../c-runtime-library/parameter-validation.md). Pokud je chyba zpracována, funkce nastaví **errno** k **EINVAL** a vrátí hodnotu -1.

Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsob jejich použití naleznete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce haldy standardní a jeho ladicí verze v sestavení pro ladění aplikace najdete v tématu [ladění verze z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_msize_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
