---
title: _heapadd
ms.date: 11/04/2016
api_name:
- _heapadd
api_location:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- heapadd
- _heapadd
helpviewer_keywords:
- _heapadd function
- memory, adding to heaps
- heaps, adding memory
- heapadd function
ms.assetid: 4d691fe2-2763-49f4-afb1-62738b7cd3ff
ms.openlocfilehash: c5eeb66ff0e6fb05063ec395e12cd97106ad724d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351322"
---
# <a name="_heapadd"></a>_heapadd

Přidá paměť do haldy.

> [!IMPORTANT]
> Tato funkce je zastaralá. Počínaje Visual Studio 2015, není k dispozici v CRT.

## <a name="syntax"></a>Syntaxe

```
int _heapadd(
   void *memblock,
   size_t size
);
```

#### <a name="parameters"></a>Parametry

*memblok*<br/>
Ukazatel na paměť haldy.

*Velikost*<br/>
Velikost paměti přidat, v bajtů.

## <a name="return-value"></a>Návratová hodnota

Pokud je `_heapadd` úspěšná, vrátí 0; v opačném případě funkce vrátí `errno` `ENOSYS`hodnotu -1 a nastaví na hodnotu .

Další informace o tomto a dalších návratových kódech naleznete [v tématu _doserrno, errno, _sys_errlist a _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Počínaje Visual C++ verze 4.0, základní struktura haldy byla přesunuta do knihoven C run-time pro podporu nové funkce ladění. V důsledku `_heapadd` toho již není podporována na žádné platformě, která je založena na rozhraní API Win32.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|`_heapadd`|\<malloc.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../c-runtime-library/compatibility.md) v úvodu.

## <a name="see-also"></a>Viz také

[Přidělení paměti](../c-runtime-library/memory-allocation.md)<br/>
[Zdarma](../c-runtime-library/reference/free.md)<br/>
[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapmin](../c-runtime-library/reference/heapmin.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[malloc](../c-runtime-library/reference/malloc.md)<br/>
[realloc](../c-runtime-library/reference/realloc.md)
