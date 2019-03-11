---
title: Přidělení paměti
ms.date: 11/04/2016
f1_keywords:
- c.memory
helpviewer_keywords:
- memory allocation, routines
- memory, managing
- memory, allocation
ms.assetid: b4470556-a128-4782-9943-2ccf7a7d9979
ms.openlocfilehash: bcc9865b149c2289f99f6ee13f31179ae58a15e1
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742789"
---
# <a name="memory-allocation"></a>Přidělení paměti

Pomocí těchto rutin můžete přidělit zdarma a znovu přidělit paměti.

## <a name="memory-allocation-routines"></a>Rutiny přidělení paměti

|Rutina|Použití|
|-------------|---------|
|[_alloca](../c-runtime-library/reference/alloca.md), [_malloca](../c-runtime-library/reference/malloca.md)|Přidělit paměť ze zásobníku|
|[calloc](../c-runtime-library/reference/calloc.md)|Přidělení úložiště pro pole a inicializace každého bajtů v přiděleného bloku na hodnotu 0|
|[_calloc_dbg](../c-runtime-library/reference/calloc-dbg.md)|Ladit verzi **calloc**; k dispozici pouze v ladicích verzí knihoven runtime|
|[delete – operátor](../c-runtime-library/operator-delete-crt.md)|Bezplatné přiděleného bloku|
|[delete – operátor&#91;&#93;](../c-runtime-library/delete-operator-crt.md)|Bezplatné přiděleného bloku|
|[_expand](../c-runtime-library/reference/expand.md)|Zvětšení nebo zmenšení blok paměti bez jeho přesunutí|
|[_expand_dbg](../c-runtime-library/reference/expand-dbg.md)|Ladit verzi **_expand**; k dispozici pouze v ladicích verzí knihoven runtime|
|[free](../c-runtime-library/reference/free.md)|Bezplatné přiděleného bloku|
|[_free_dbg](../c-runtime-library/reference/free-dbg.md)|Ladit verzi **bezplatné**; k dispozici pouze v ladicích verzí knihoven runtime|
|[_freea](../c-runtime-library/reference/freea.md)|Volný blok přidělené v zásobníku|
|[_get_heap_handle](../c-runtime-library/reference/get-heap-handle.md)|Získejte Win32 zpracování haldy CRT.|
|[_heapadd](../c-runtime-library/heapadd.md)|Přidejte paměť haldy|
|[_heapchk](../c-runtime-library/reference/heapchk.md)|Kontrola haldy pro zajištění konzistence|
|[_heapmin](../c-runtime-library/reference/heapmin.md)|Uvolnění nevyužité paměti v haldě|
|[_heapset](../c-runtime-library/heapset.md)|Vyplnit zadanou hodnotou volné haldy položky|
|[_heapwalk](../c-runtime-library/reference/heapwalk.md)|Vrátí informace o každé položce v haldě|
|[malloc](../c-runtime-library/reference/malloc.md)|Přidělení bloku paměti z haldy|
|[_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md)|Ladit verzi **malloc**; k dispozici pouze v ladicích verzí knihoven runtime|
|[_msize](../c-runtime-library/reference/msize.md)|Vrátí velikost přiděleného bloku|
|[_msize_dbg](../c-runtime-library/reference/msize-dbg.md)|Ladit verzi **_msize –**; k dispozici pouze v ladicích verzí knihoven runtime|
|[new](../c-runtime-library/operator-new-crt.md)|Přidělení bloku paměti z haldy|
|[Nový&#91;&#93;](../c-runtime-library/new-operator-crt.md)|Přidělení bloku paměti z haldy|
|[_query_new_handler](../c-runtime-library/reference/query-new-handler.md)|Zpáteční adresa aktuálního nové rutiny obsluhy úmluvu **_set_new_handler**|
|[_query_new_mode](../c-runtime-library/reference/query-new-mode.md)|Vrácení celé číslo, které nastavil nový režim obslužné rutiny **_set_new_mode** pro **malloc**|
|[realloc](../c-runtime-library/reference/realloc.md)|Přidělit jinému uživateli pro novou velikost bloku|
|[_realloc_dbg](../c-runtime-library/reference/realloc-dbg.md)|Ladit verzi **realloc**; k dispozici pouze v ladicích verzí knihoven runtime|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Povolte mechanismus zpracování chyb při **nové** operátor selže (přidělování paměti) a povolte kompilace standardní knihovny C++|
|[_set_new_mode](../c-runtime-library/reference/set-new-mode.md)|Nastavit nový režim obslužné rutiny pro **malloc**|

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
