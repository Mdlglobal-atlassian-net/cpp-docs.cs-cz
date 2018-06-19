---
title: Přidělení paměti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.memory
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, routines
- memory, managing
- memory, allocation
ms.assetid: b4470556-a128-4782-9943-2ccf7a7d9979
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5d13f120fbbb655c644ef1520d011a45f92494ab
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391923"
---
# <a name="memory-allocation"></a>Přidělení paměti

Použijte tyto rutiny přidělit free a znovu přidělte paměť.

## <a name="memory-allocation-routines"></a>Rutiny přidělení paměti

|Rutina|Použití|
|-------------|---------|
|[_alloca –](../c-runtime-library/reference/alloca.md), [_malloca –](../c-runtime-library/reference/malloca.md)|Přidělení paměti ze zásobníku|
|[calloc](../c-runtime-library/reference/calloc.md)|Přidělení úložiště pro pole a inicializace každého bajtů v přidělené bloku na hodnotu 0|
|[_calloc_dbg](../c-runtime-library/reference/calloc-dbg.md)|Ladění verzi **calloc –**; k dispozici pouze ve verzích ladicí běhové knihovny|
|[delete – operátor](../c-runtime-library/operator-delete-crt.md)|Volné přidělené bloku|
|[delete – operátor&#91;&#93;](../c-runtime-library/delete-operator-crt.md)|Volné přidělené bloku|
|[_expand](../c-runtime-library/reference/expand.md)|Zvětšení nebo zmenšení blokem paměti bez jeho přesunutí|
|[_expand_dbg](../c-runtime-library/reference/expand-dbg.md)|Ladění verzi **_rozšířit lokalitu**; k dispozici pouze ve verzích ladicí běhové knihovny|
|[free](../c-runtime-library/reference/free.md)|Volné přidělené bloku|
|[_free_dbg](../c-runtime-library/reference/free-dbg.md)|Ladění verzi **volné**; k dispozici pouze ve verzích ladicí běhové knihovny|
|[_freea](../c-runtime-library/reference/freea.md)|Volné přidělené blokování ze zásobníku|
|[_get_heap_handle](../c-runtime-library/reference/get-heap-handle.md)|Získáte Win32 zpracování haldy CRT.|
|[_heapadd](../c-runtime-library/heapadd.md)|Přidejte do halda paměti|
|[_heapchk](../c-runtime-library/reference/heapchk.md)|Kontrola konzistence hald|
|[_heapmin](../c-runtime-library/reference/heapmin.md)|Verze nevyužitou paměť haldy|
|[_heapset](../c-runtime-library/heapset.md)|Zadaná hodnota vyplníte položky volné haldy|
|[_heapwalk](../c-runtime-library/reference/heapwalk.md)|Vrátí informace o jednotlivých položek v haldy|
|[malloc](../c-runtime-library/reference/malloc.md)|Přidělit blok paměti z haldy|
|[_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md)|Ladění verzi **malloc**; k dispozici pouze ve verzích ladicí běhové knihovny|
|[_msize](../c-runtime-library/reference/msize.md)|Vrátí velikost přidělené bloku|
|[_msize_dbg](../c-runtime-library/reference/msize-dbg.md)|Ladění verzi **_msize –**; k dispozici pouze ve verzích ladicí běhové knihovny|
|[new](../c-runtime-library/operator-new-crt.md)|Přidělit blok paměti z haldy|
|[Nový&#91;&#93;](../c-runtime-library/new-operator-crt.md)|Přidělit blok paměti z haldy|
|[_query_new_handler](../c-runtime-library/reference/query-new-handler.md)|Zpáteční adresa aktuální nové rutiny obslužných rutin jako sady podle **_set_new_handler –**|
|[_query_new_mode](../c-runtime-library/reference/query-new-mode.md)|Návratový celé číslo označující nový režim obslužná rutina, která nastavuje **_set_new_mode –** pro **malloc –**|
|[realloc](../c-runtime-library/reference/realloc.md)|Znovu přidělte blok k novou velikost|
|[_realloc_dbg](../c-runtime-library/reference/realloc-dbg.md)|Ladění verzi **realloc –**; k dispozici pouze ve verzích ladicí běhové knihovny|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Povolit mechanismus zpracování chyb při **nové** operátor nepodaří (přidělení paměti) a povolte kompilace standardní knihovny jazyka C++|
|[_set_new_mode](../c-runtime-library/reference/set-new-mode.md)|Nastavit nový režim obslužné rutiny pro **malloc –**|

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
