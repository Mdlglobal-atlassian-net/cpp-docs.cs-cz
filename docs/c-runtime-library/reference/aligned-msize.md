---
title: _aligned_msize
ms.date: 11/04/2016
apiname:
- _aligned_msize
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _aligned_msize
- aligned_msize
helpviewer_keywords:
- aligned_msize function
- _aligned_msize function
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
ms.openlocfilehash: 97c739eed1f54f0c6705d37542eb13c6ec6879d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524843"
---
# <a name="alignedmsize"></a>_aligned_msize

Vrátí velikost bloku paměti přidělení na haldě.

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
Ukazatele na blok paměti.

*Zarovnání*<br/>
Hodnota zarovnání, které musí být celočíselnou mocninou 2.

*Posun*<br/>
Posun na přidělení paměti pro vynucení zarovnání.

## <a name="return-value"></a>Návratová hodnota

Vrátí velikost (v bajtech) jako celé číslo bez znaménka.

## <a name="remarks"></a>Poznámky

**_Aligned_msize –** funkce vrátí velikost v bajtech, blok paměti přidělený volání [_aligned_malloc](aligned-malloc.md) nebo [_aligned_realloc –](aligned-realloc.md). *Zarovnání* a *posun* hodnoty musí být stejný jako hodnoty předané na funkci, která přidělené bloku.

Když je aplikace spojena s ladicí verzí knihovny run-time C **_aligned_msize –** přeloží na [_aligned_msize_dbg](aligned-msize-dbg.md). Další informace o tom, jak je spravována halda během procesu ladění, naleznete v tématu [haldy pro ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Tato funkce ověřuje svůj parametr. Pokud *memblock* je ukazatel s hodnotou null nebo *zarovnání* není mocninou čísla 2, **_msize –** vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation ](../../c-runtime-library/parameter-validation.md). Pokud je chyba zpracována, funkce nastaví **errno** k **EINVAL** a vrátí hodnotu -1.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_msize**|\<malloc.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
