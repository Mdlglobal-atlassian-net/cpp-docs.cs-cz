---
title: _msize
ms.date: 4/2/2020
api_name:
- _msize
- _o__msize
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
- msize
- _msize
helpviewer_keywords:
- memory blocks
- msize function
- _msize function
ms.assetid: 02b1f89e-d0d7-4f12-938a-9eeba48a0f88
ms.openlocfilehash: 7d5f62bd6111a305c18b0ee19bb6d3e90f2ddb49
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338669"
---
# <a name="_msize"></a>_msize

Vrátí velikost bloku paměti přidělené v haldě.

## <a name="syntax"></a>Syntaxe

```C
size_t _msize(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblok*<br/>
Ukazatel na blok paměti.

## <a name="return-value"></a>Návratová hodnota

**_msize** vrátí velikost (v bajtů) jako nepodepsané celé číslo.

## <a name="remarks"></a>Poznámky

Funkce **_msize** vrátí velikost bloku paměti přiděleného voláním **calloc**, **malloc**nebo **realloc**.

Pokud je aplikace propojena s ladicí verzí knihoven run-time C, **_msize** překládá na [_msize_dbg](msize-dbg.md). Další informace o tom, jak haldy je spravována během procesu ladění, naleznete [v tématu HALDA ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Tato funkce ověřuje jeho parametr. Pokud *memblock* je nula ukazatel, **_msize** vyvolá neplatný obslužnou rutinu parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je chyba zpracována, funkce nastaví **errno** na **EINVAL** a vrátí -1.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

Viz příklad pro [realloc](realloc.md).

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[_expand](expand.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
