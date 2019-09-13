---
title: _msize
ms.date: 11/04/2016
api_name:
- _msize
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
ms.openlocfilehash: c1760cfa6a416e2eb4cd7b549cb5ae9bed00a609
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951435"
---
# <a name="_msize"></a>_msize

Vrací velikost bloku paměti přiděleného v haldě.

## <a name="syntax"></a>Syntaxe

```C
size_t _msize(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Ukazatel na blok paměti.

## <a name="return-value"></a>Návratová hodnota

**_msize** vrací velikost (v bajtech) jako unsigned integer.

## <a name="remarks"></a>Poznámky

Funkce **_msize** vrací velikost bloku paměti, který je přidělen voláním metody **calloc**, pole nebo **realokace** **, v**bajtech.

Pokud je aplikace propojena s ladicí verzí knihoven C Runtime, **_msize** se přeloží na [_msize_dbg](msize-dbg.md). Další informace o tom, jak je halda spravována během procesu ladění, naleznete v [haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Tato funkce ověří svůj parametr. Pokud je *memblock* ukazatel s hodnotou null, **_msize** vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud je chyba zpracována, funkce nastaví **errno** na **EINVAL** a vrátí-1.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_msize**|\<. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [přepřidělení](realloc.md).

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[_expand](expand.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
