---
title: _aligned_msize_dbg
ms.date: 11/04/2016
api_name:
- _aligned_msize_dbg
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _aligned_msize_dbg
helpviewer_keywords:
- _aligned_msize_dbg
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
ms.openlocfilehash: f2a0ceab906dccacb2e1c78a8789d524b608a4ff
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939868"
---
# <a name="_aligned_msize_dbg"></a>_aligned_msize_dbg

Vrátí velikost bloku paměti přiděleného v haldě (pouze ladicí verze).

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
Ukazatel na blok paměti.

*bod*<br/>
Hodnota zarovnání, která musí být celočíselnou mocninou 2.

*polohy*<br/>
Posun k přidělení paměti pro vynucení zarovnání.

## <a name="return-value"></a>Návratová hodnota

Vrátí velikost (v bajtech) jako unsigned integer.

## <a name="remarks"></a>Poznámky

Hodnoty *Zarovnání* a *posunutí* musí být stejné jako hodnoty předané funkci, která tento blok přidělila.

**_aligned_msize_dbg** je ladicí verze funkce [_aligned_msize](aligned-msize.md) . Pokud není definován [_DEBUG](../../c-runtime-library/debug.md) , každé volání **_aligned_msize_dbg** je sníženo na volání **_aligned_msize**. **_Aligned_msize** i **_aligned_msize_dbg** vypočítávají velikost bloku paměti v základní haldě, ale **_aligned_msize_dbg** přidá funkci ladění: Zahrnuje vyrovnávací paměti na obou stranách uživatelské části bloku paměti ve vrácené velikosti.

Tato funkce ověří svůj parametr. Pokud je *memblock* ukazatel s hodnotou null nebo *Zarovnání* není mocninou 2, **_msize** vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud je chyba zpracována, funkce nastaví **errno** na **EINVAL** a vrátí-1.

Informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloků přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi voláním standardní funkce haldy a její ladicí verzí v sestavení ladění aplikace najdete v tématu [ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_msize_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
