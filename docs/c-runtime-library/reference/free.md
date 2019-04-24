---
title: free
ms.date: 11/04/2016
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
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
ms.openlocfilehash: f56212874f05ea5d4ab7bd826a7a4c145551dfc0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287756"
---
# <a name="free"></a>free

Zruší přidělení nebo ho uvolní blok paměti.

## <a name="syntax"></a>Syntaxe

```C
void free(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Dříve přidělený blok paměti určený k uvolnění.

## <a name="remarks"></a>Poznámky

**Bezplatné** funkce zruší přidělení bloku paměti (*memblock*), která byla dříve přidělena voláním **calloc**, **malloc**, nebo **realloc**. Počet uvolněných bajtů je ekvivalentní k počtu bajtů při byl přidělen blok (nebo v případě třídy nevyčerpané **realloc**). Pokud *memblock* je **NULL**, ukazatel je ignorována a **bezplatné** okamžitě vrátí. Pokus o uvolnění neplatný ukazatel (ukazatele na blok paměti, který nebyl přidělen pomocí **calloc**, **malloc**, nebo **realloc**) může mít vliv na následné přidělování požadavků a způsobit chyby.

Pokud dojde k chybě v uvolňování paměti, **errno** nastaven s informacemi z operačního systému na povaze selhání. Další informace najdete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Po bloku paměti byl uvolněn, [_heapmin –](heapmin.md) minimalizuje množství volné paměti v haldě slučování nevyužité oblasti a uvolněním je zpět do operačního systému. Uvolněné paměti, který není v operačním systému, budou obnoveny do volného fondu a je k dispozici pro přidělení znovu.

Když je aplikace spojena s ladicí verzí knihovny run-time C **bezplatné** přeloží na [_free_dbg –](free-dbg.md). Další informace o tom, jak je spravována halda během procesu ladění, naleznete v tématu [haldy pro ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

**bezplatné** je označen `__declspec(noalias)`, což znamená, že funkce je zaručeno, že neupraví globální proměnné. Další informace najdete v tématu [noalias](../../cpp/noalias.md).

K uvolnění paměti s [_malloca](malloca.md), použijte [_freea –](freea.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**free**|\<stdlib.h > a \<malloc.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [malloc](malloc.md).

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[_alloca](alloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
[_freea](freea.md)<br/>
