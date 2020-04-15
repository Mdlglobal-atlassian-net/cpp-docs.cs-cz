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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 21ae07c90bbf9a729a212a97b7de3e0916f8e2c6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350594"
---
# <a name="_aligned_msize"></a>_aligned_msize

Vrátí velikost bloku paměti přidělené v haldě.

## <a name="syntax"></a>Syntaxe

```C
size_t _msize(
   void *memblock,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parametry

*memblok*<br/>
Ukazatel na blok paměti.

*Zarovnání*<br/>
Hodnota zarovnání, která musí být celá mocnina 2.

*Posun*<br/>
Posun do přidělení paměti vynutit zarovnání.

## <a name="return-value"></a>Návratová hodnota

Vrátí velikost (v bajtů) jako nepodepsané celé číslo.

## <a name="remarks"></a>Poznámky

Funkce **_aligned_msize** vrátí velikost bloku paměti přiděleného voláním [_aligned_malloc](aligned-malloc.md) nebo [_aligned_realloc](aligned-realloc.md)v bajtech . Hodnoty *trasy* a *odsazení* musí být stejné jako hodnoty předané funkci, která blok přidělila.

Pokud je aplikace propojena s ladicí verzí knihoven run-time C, **_aligned_msize** překládá na [_aligned_msize_dbg](aligned-msize-dbg.md). Další informace o tom, jak haldy je spravována během procesu ladění, naleznete [v tématu HALDA ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Tato funkce ověřuje jeho parametr. Pokud *memblock* je nula ukazatel nebo *trasa* není mocninu 2, **_msize** vyvolá neplatný obslužnou rutinu parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je chyba zpracována, funkce nastaví **errno** na **EINVAL** a vrátí -1.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
