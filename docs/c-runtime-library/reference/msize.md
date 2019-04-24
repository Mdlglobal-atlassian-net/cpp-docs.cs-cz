---
title: _msize
ms.date: 11/04/2016
apiname:
- _msize
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
- msize
- _msize
helpviewer_keywords:
- memory blocks
- msize function
- _msize function
ms.assetid: 02b1f89e-d0d7-4f12-938a-9eeba48a0f88
ms.openlocfilehash: 0321e42face817a0a9f12d780f72c86c67ba308d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156288"
---
# <a name="msize"></a>_msize

Vrátí velikost bloku paměti přidělení na haldě.

## <a name="syntax"></a>Syntaxe

```C
size_t _msize(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Ukazatele na blok paměti.

## <a name="return-value"></a>Návratová hodnota

**_msize –** vrátí velikost (v bajtech) jako celé číslo bez znaménka.

## <a name="remarks"></a>Poznámky

**_Msize –** funkce vrátí velikost v bajtech, blok paměti přidělený volání **calloc**, **malloc**, nebo **realloc**.

Když je aplikace spojena s ladicí verzí knihovny run-time C **_msize –** přeloží na [_msize_dbg –](msize-dbg.md). Další informace o tom, jak je spravována halda během procesu ladění, naleznete v tématu [haldy pro ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Tato funkce ověřuje svůj parametr. Pokud *memblock* je ukazatel s hodnotou null, **_msize –** vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud je chyba zpracována, funkce nastaví **errno** k **EINVAL** a vrátí hodnotu -1.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [realloc](realloc.md).

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[_expand](expand.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
