---
title: "_freea – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _freea
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
dev_langs: C++
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 50d1c551f0ae51daafb3d83075091fa299db0fed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="freea"></a>_freea
Zruší přidělení nebo uvolní blok paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _freea(   
   void *memblock   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `memblock`  
 Dříve při přidělování paměti bloku na uvolnění.  
  
## <a name="return-value"></a>Návratová hodnota  
 Žádné  
  
## <a name="remarks"></a>Poznámky  
 `_freea` Funkce zruší přidělení paměti blok (`memblock`), již bylo přiděleno voláním [_malloca –](../../c-runtime-library/reference/malloca.md). `_freea`zkontroluje, pokud byl přidělen paměť na haldě nebo zásobníku. Pokud byl přidělen do zásobníku, `_freea` se nic nestane. Pokud byl přidělen v haldě, počet uvolněné bajtů je ekvivalentní počet bajtů, které jsou požadovány při bloku byl přidělen. Pokud `memblock` je `NULL`, ukazatele je ignorován a `_freea` hned vrátí. Probíhá pokus o volné neplatný ukazatel (ukazatel na blok paměti, která nebyla přidělena `_malloca`) může mít vliv na následné přidělení požadavky a způsobit chyby.  
  
 `_freea`volání `free` interně, pokud zjistí, že je paměť přidělená v haldě. Zda je paměť v haldě nebo zásobníku je dáno značku umístěny v paměti na adrese bezprostředně předcházející přidělenou paměť.  
  
 Pokud dojde k chybě v uvolnění paměti, `errno` je nastaven s informacemi z operačního systému, o povaze chyby. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Po blok paměti bylo uvolněno, [_heapmin –](../../c-runtime-library/reference/heapmin.md) minimalizuje množství volné paměti v haldě slučování nepoužívané oblasti a uvolnění je zpět do operačního systému. Uvolněné paměti, které není vydané v operačním systému je obnovit do volného fondu a je k dispozici pro přidělení znovu.  
  
 Volání `_freea` musí doprovázet všechna volání `_malloca`. Je také chyba volání `_freea` dvakrát na stejnou paměť. Když je aplikace propojený s verzí ladicí běhové knihovny jazyka C, zejména s [_malloc_dbg –](../../c-runtime-library/reference/malloc-dbg.md) Funkce povolené definováním `_CRTDBG_MAP_ALLOC`, je snazší najít chybí nebo je duplicitní volání `_freea`. Další informace o spravováni haldě ladění během najdete v tématu [haldy ladění The CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 `_freea`je označena `__declspec(noalias)`, což znamená, že funkce záruku, že nechcete upravit globální proměnné. Další informace najdete v tématu [noalias](../../cpp/noalias.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_freea`|\<stdlib.h > a \<malloc.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [_malloca –](../../c-runtime-library/reference/malloca.md).  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)   
 [_malloca –](../../c-runtime-library/reference/malloca.md)   
 [calloc –](../../c-runtime-library/reference/calloc.md)   
 [malloc –](../../c-runtime-library/reference/malloc.md)   
 [_malloc_dbg –](../../c-runtime-library/reference/malloc-dbg.md)   
 [realloc –](../../c-runtime-library/reference/realloc.md)   
 [_free_dbg –](../../c-runtime-library/reference/free-dbg.md)   
 [_heapmin –](../../c-runtime-library/reference/heapmin.md)