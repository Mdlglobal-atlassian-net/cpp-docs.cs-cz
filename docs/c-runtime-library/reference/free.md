---
title: volné | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- free
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
- free
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc6dfd832d18dbabc1ebc10aec252cc8afe15346
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="free"></a>free

Zruší přidělení nebo uvolní blok paměti.

## <a name="syntax"></a>Syntaxe

```C
void free(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock* dříve přidělené paměti bloku na uvolnění.

## <a name="remarks"></a>Poznámky

**Volné** funkce zruší přidělení paměti blok (*memblock*), již bylo přiděleno voláním **calloc –**, **malloc –**, nebo **realloc –**. Počet bajtů, uvolněné se rovná počet bajtů, které jsou požadovány při bloku byl přidělen (nebo opětovnému přidělení u **realloc –**). Pokud *memblock* je **NULL**, ukazatele je ignorován a **volné** hned vrátí. Probíhá pokus o volné neplatný ukazatel (ukazatel na blok paměti, která nebyla přidělena **calloc –**, **malloc –**, nebo **realloc –**) může mít vliv na následné přidělení požadavků a způsobit chyby.

Pokud dojde k chybě v uvolnění paměti, **errno** je nastaven s informacemi z operačního systému, o povaze chyby. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Po blok paměti bylo uvolněno, [_heapmin –](heapmin.md) minimalizuje množství volné paměti v haldě slučování nepoužívané oblasti a uvolnění je zpět do operačního systému. Uvolněné paměti, které není vydané v operačním systému je obnovit do volného fondu a je k dispozici pro přidělení znovu.

Když aplikace je spojená s verzí ladicí běhové knihovny jazyka C, **volné** přeloží na [_free_dbg –](free-dbg.md). Další informace o spravováni haldě ladění během najdete v tématu [haldy ladění The CRT](/visualstudio/debugger/crt-debug-heap-details).

**volné** je označena `__declspec(noalias)`, což znamená, že funkce záruku, že nechcete upravit globální proměnné. Další informace najdete v tématu [noalias](../../cpp/noalias.md).

Uvolnit paměť, kterým je přiřazen [_malloca –](malloca.md), použijte [_freea –](freea.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**free**|\<stdlib.h > a \<malloc.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [malloc –](malloc.md).

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[_alloca](alloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
[_freea](freea.md)<br/>
