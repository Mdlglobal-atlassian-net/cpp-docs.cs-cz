---
title: _freea
ms.date: 11/04/2016
api_name:
- _freea
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- freea
- _freea
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
ms.openlocfilehash: dcad8bea4f8cec28d8cb15a9937b1032593ef0cc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956713"
---
# <a name="_freea"></a>_freea

Zruší přidělení nebo uvolní blok paměti.

## <a name="syntax"></a>Syntaxe

```C
void _freea(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Dříve přidělený blok paměti, který se má uvolnit

## <a name="return-value"></a>Návratová hodnota

Žádné

## <a name="remarks"></a>Poznámky

Funkce **_freea** zruší přidělení paměti bloku (*memblock*), který byl dříve přidělen voláním [_malloca](malloca.md). **_freea** zkontroluje, jestli byla paměť přidělená haldě nebo zásobníku. Pokud byla přidělena v zásobníku, **_freea** neprovede žádnou akci. Pokud byla tato halda přidělena, počet uvolněných bajtů se rovná počtu bajtů požadovaných při přidělení bloku. Pokud má Memblock **hodnotu null**, ukazatel se ignoruje a **_freea** se okamžitě vrátí. Pokus o uvolnění neplatného ukazatele (ukazatel na blok paměti, který nebyl přidělen nástrojem **_malloca**) může ovlivnit následné žádosti o přidělení a způsobit chyby.

**_freea** volá **bezplatná** interní, pokud zjistí, že paměť je přidělena haldě. Zda je paměť na haldě, nebo zásobník je určena značkou umístěnou v paměti na adrese bezprostředně předcházející přidělené paměti.

Pokud dojde k chybě při uvolnění paměti, **errno** se nastaví s informacemi z operačního systému podle povahy selhání. Další informace najdete v tématech [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Po uvolnění bloku paměti [_heapmin](heapmin.md) minimalizuje množství volné paměti v haldě sloučením nepoužívaných oblastí a jejich uvolněním zpět do operačního systému. Uvolněná paměť, která není vydána v operačním systému, se obnoví do volného fondu a je možné ji znovu přidělit.

Volání **_freea** musí doprovázet všechna volání **_malloca**. Je také chyba volat **_freea** dvakrát ve stejné paměti. Pokud je aplikace propojena s ladicí verzí běhových knihoven jazyka C, zejména s funkcemi [_malloc_dbg](malloc-dbg.md) povolenými definováním **_CRTDBG_MAP_ALLOC**, je snazší najít chybějící nebo duplicitní volání **_freea**. Další informace o tom, jak je halda spravována během procesu ladění, naleznete v [haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

**_freea** je označena `__declspec(noalias)`, což znamená, že funkce je zaručena, že nemění globální proměnné. Další informace najdete v tématu [jiné](../../cpp/noalias.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_freea**|\<Stdlib. h > a \<. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
