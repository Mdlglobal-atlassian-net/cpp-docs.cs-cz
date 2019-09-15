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
ms.openlocfilehash: 4be87710519c9a389adbaf41fefddb9ea8dfb1e6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940275"
---
# <a name="_heapadd"></a>_heapadd

Přidá paměť do haldy.

> [!IMPORTANT]
>  Tato funkce je zastaralá. Počínaje verzí Visual Studio 2015 není k dispozici v CRT.

## <a name="syntax"></a>Syntaxe

```
int _heapadd(
   void *memblock,
   size_t size
);
```

#### <a name="parameters"></a>Parametry

*memblock*<br/>
Ukazatel na paměť haldy.

*hodnota*<br/>
Velikost paměti, která se má přidat (v bajtech)

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu `_heapadd` vrátí hodnotu 0. v opačném případě vrátí funkce hodnotu- `errno` 1 `ENOSYS`a nastaví na.

Další informace o tomto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Počínaje verzí Visual C++ 4,0 se podkladová struktura haldy přesunula do knihoven run-time jazyka C, aby podporovala nové funkce ladění. V důsledku `_heapadd` toho již není podporován na žádné platformě, která je založena na Win32 API.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|`_heapadd`|\<. h >|\<errno.h>|

Další informace o kompatibilitě naleznete v úvodu v tématu [Kompatibilita](../c-runtime-library/compatibility.md) .

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../c-runtime-library/memory-allocation.md)<br/>
[free](../c-runtime-library/reference/free.md)<br/>
[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapmin](../c-runtime-library/reference/heapmin.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[malloc](../c-runtime-library/reference/malloc.md)<br/>
[realloc](../c-runtime-library/reference/realloc.md)
