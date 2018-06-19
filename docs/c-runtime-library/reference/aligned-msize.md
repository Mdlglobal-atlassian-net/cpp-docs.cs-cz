---
title: _aligned_msize – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- aligned_msize function
- _aligned_msize function
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2375ec8f61a95ec018ea55cc1f891ad8049748c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393102"
---
# <a name="alignedmsize"></a>_aligned_msize

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

*memblock*<br/>
Ukazatel na oblast paměti.

*Zarovnání*<br/>
Zarovnání hodnota, která musí být celé číslo mocninou 2.

*Posun*<br/>
Posun do přidělení paměti vynutit zarovnání.

## <a name="return-value"></a>Návratová hodnota

Vrátí velikost (v bajtech) jako celé číslo bez znaménka.

## <a name="remarks"></a>Poznámky

**_Aligned_msize –** funkce vrátí velikost v bajtech bloku paměti přidělené voláním [_aligned_malloc –](aligned-malloc.md) nebo [_aligned_realloc –](aligned-realloc.md). *Zarovnání* a *posun* hodnoty musí být stejný jako hodnoty předané funkce, která přidělené bloku.

Když aplikace je spojená s verzí ladicí běhové knihovny jazyka C, **_aligned_msize –** přeloží na [_aligned_msize_dbg](aligned-msize-dbg.md). Další informace o spravováni haldě ladění během najdete v tématu [haldy ladění The CRT](/visualstudio/debugger/crt-debug-heap-details).

Tato funkce ověří jeho parametru. Pokud *memblock* je nulový ukazatel nebo *zarovnání* není mocninou 2, **_msize –** vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru ](../../c-runtime-library/parameter-validation.md). Pokud se zpracovává chyby, nastaví funkci **errno** k **einval –** a vrátí hodnotu -1.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_msize**|\<malloc.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
