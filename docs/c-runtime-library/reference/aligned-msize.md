---
title: _aligned_msize
ms.date: 4/2/2020
api_name:
- _aligned_msize
- _o__aligned_msize
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _aligned_msize
- aligned_msize
helpviewer_keywords:
- aligned_msize function
- _aligned_msize function
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
ms.openlocfilehash: e3ff243ba9a135cf660d09fc5b3690f531702aab
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912905"
---
# <a name="_aligned_msize"></a>_aligned_msize

Vrací velikost bloku paměti přiděleného v haldě.

## <a name="syntax"></a>Syntaxe

```C
size_t _msize(
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

Funkce **_aligned_msize** vrací velikost bloku paměti, který je přidělen voláním [_aligned_malloc](aligned-malloc.md) nebo [_aligned_realloc](aligned-realloc.md), v bajtech. Hodnoty *Zarovnání* a *posunutí* musí být stejné jako hodnoty předané funkci, která tento blok přidělila.

Pokud je aplikace propojena s ladicí verzí běhových knihoven jazyka C, **_aligned_msize** překládá na [_aligned_msize_dbg](aligned-msize-dbg.md). Další informace o tom, jak je halda spravována během procesu ladění, naleznete v [haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Tato funkce ověří svůj parametr. Pokud *memblock* je ukazatel s hodnotou null nebo *Zarovnání* není mocninou 2, **_msize** vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud je chyba zpracována, funkce nastaví **errno** na **EINVAL** a vrátí-1.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_msize**|\<. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
