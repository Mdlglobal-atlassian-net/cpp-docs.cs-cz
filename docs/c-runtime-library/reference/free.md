---
title: free
ms.date: 4/2/2020
api_name:
- free
- _o_free
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
- free
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
ms.openlocfilehash: eefbe957ce5057b5038f98bc8da8fb2f0bdd3d1c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345983"
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

*memblok*<br/>
Dříve přidělený blok paměti, který má být uvolněn.

## <a name="remarks"></a>Poznámky

**Volná** funkce navrací blok paměti (*memblock*), který byl dříve přidělen voláním **calloc**, **malloc**nebo **realloc**. Počet uvolněných bajtů je ekvivalentní počtu bajtů požadovaných při přidělení bloku (nebo přerozděleny v případě **přerozdělení).** Pokud *memblock* je **NULL**, ukazatel je ignorována a **zdarma** okamžitě vrátí. Pokus o uvolnění neplatný ukazatel (ukazatel na blok paměti, který nebyl přidělen **calloc**, **malloc**, nebo **reloc**) může ovlivnit následné požadavky na přidělení a způsobit chyby.

Pokud dojde k chybě při uvolnění paměti, **errno** je nastaven s informacemi z operačního systému o povaze selhání. Další informace naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Po uvolnění bloku paměti [_heapmin](heapmin.md) minimalizuje množství volné paměti na haldě tím, že slučuje nepoužívané oblasti a uvolňuje je zpět do operačního systému. Uvolněná paměť, která není uvolněna do operačního systému, je obnovena do fondu volného stavu a je k dispozici pro přidělení znovu.

Pokud je aplikace propojena s ladicí verzí knihoven c run-time, **free** resolves to [_free_dbg](free-dbg.md). Další informace o tom, jak haldy je spravována během procesu ladění, naleznete [v tématu HALDA ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

**je** označena `__declspec(noalias)`, což znamená, že je zaručeno, že funkce nebude měnit globální proměnné. Další informace naleznete v tématu [noalias](../../cpp/noalias.md).

Chcete-li uvolnit paměť přidělenou [_malloca](malloca.md), použijte [_freea](freea.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**Zdarma**|\<stdlib.h> \<a malloc.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad pro [malloc](malloc.md).

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[_alloca](alloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
[_freea](freea.md)<br/>
