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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 0e0a53dd9d24634442c8dd456e4f9d38f742e292
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920427"
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

*memblock*<br/>
Dříve přidělený blok paměti, který se má uvolnit

## <a name="remarks"></a>Poznámky

Funkce **Free uvolní** blok paměti (*memblock*), který byl dříve přidělen voláním metody **calloc** **,** nebo **realokace**. Počet uvolněných bajtů se rovná počtu bajtů požadovaných v době, kdy byl blok přidělen (nebo znovu přidělen v případě **přepřidělení**). Pokud *memblock* má Memblock **hodnotu null**, ukazatel se ignoruje **a okamžitě se vrátí** . Při pokusu o uvolnění neplatného ukazatele (ukazatel na blok **paměti, který**nebyl přidělen pomocí **calloc**, nezdařila nebo **realokace**) může ovlivnit následné žádosti o přidělení a způsobit chyby.

Pokud dojde k chybě při uvolnění paměti, **errno** se nastaví s informacemi z operačního systému podle povahy selhání. Další informace najdete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Po uvolnění bloku paměti [_heapmin](heapmin.md) minimalizuje množství volné paměti v haldě sloučením nepoužívaných oblastí a jejich uvolněním zpět do operačního systému. Uvolněná paměť, která není vydána v operačním systému, se obnoví do volného fondu a je možné ji znovu přidělit.

V případě, že je aplikace propojena s ladicí verzí běhových knihoven jazyka C, je **bezplatná** překládána na [_free_dbg](free-dbg.md). Další informace o tom, jak je halda spravována během procesu ladění, naleznete v [haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

**Free** je označena `__declspec(noalias)`, což znamená, že funkce zaručuje, že nemění globální proměnné. Další informace najdete v tématu [jiné](../../cpp/noalias.md).

K uvolnění paměti přidělené [_malloca](malloca.md)použijte [_freea](freea.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**dost**|\<Stdlib. h> a \<. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte [se na příklad pro.](malloc.md)

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[_alloca](alloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
[_freea](freea.md)<br/>
