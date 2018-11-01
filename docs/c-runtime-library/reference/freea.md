---
title: _freea
ms.date: 11/04/2016
apiname:
- _freea
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
apitype: DLLExport
f1_keywords:
- freea
- _freea
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
ms.openlocfilehash: ac9c5528755898b0de131bccf94185b501b0e720
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605891"
---
# <a name="freea"></a>_freea

Zruší přidělení nebo ho uvolní blok paměti.

## <a name="syntax"></a>Syntaxe

```C
void _freea(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Dříve přidělený blok paměti určený k uvolnění.

## <a name="return-value"></a>Návratová hodnota

Žádné

## <a name="remarks"></a>Poznámky

**_Freea –** funkce zruší přidělení bloku paměti (*memblock*), která byla dříve přidělena voláním [_malloca](malloca.md). **_freea –** kontroluje, pokud byla přidělena paměť na haldu nebo do zásobníku. Pokud byl přidělen do zásobníku **_freea –** nemá žádný účinek. Pokud byl přidělen na haldě, je počet bajtů při byl přidělen blok ekvivalentní počet uvolněných bajtů. Pokud *memblock* je **NULL**, ukazatel je ignorována a **_freea –** okamžitě vrátí. Pokus o uvolnění neplatný ukazatel (ukazatele na blok paměti, který nebyl přidělen pomocí **_malloca**) může mít vliv na následné přidělování požadavků a způsobit chyby.

**_freea –** volání **bezplatné** interně v případě, že zjistí, že paměť přidělena v haldě. Zda je paměť na haldě nebo zásobníku je určeno značku umístěné v paměti na adrese bezprostředně před přidělené paměti.

Pokud dojde k chybě v uvolňování paměti, **errno** nastaven s informacemi z operačního systému na povaze selhání. Další informace najdete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Po bloku paměti byl uvolněn, [_heapmin –](heapmin.md) minimalizuje množství volné paměti v haldě slučování nevyužité oblasti a uvolněním je zpět do operačního systému. Uvolněné paměti, který není v operačním systému, budou obnoveny do volného fondu a je k dispozici pro přidělení znovu.

Volání **_freea –** musí doprovázejí veškerá volání **_malloca**. Je také chybou volání **_freea –** dvakrát na stejnou paměť. Když je aplikace spojena s ladicí verzí knihovny run-time jazyka C, zejména s [_malloc_dbg](malloc-dbg.md) funkce přidané do aplikace tak, že definujete **_CRTDBG_MAP_ALLOC**, je snazší najít chybějící nebo duplicitní volání **_freea –**. Další informace o tom, jak je spravována halda během procesu ladění, naleznete v tématu [haldy pro ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

**_freea –** je označen `__declspec(noalias)`, což znamená, že funkce je zaručeno, že neupraví globální proměnné. Další informace najdete v tématu [noalias](../../cpp/noalias.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_freea**|\<stdlib.h > a \<malloc.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_malloca](malloca.md).

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[_malloca](malloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
